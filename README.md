## My pagedown rendered CV

**This is forked from Nick Strayer's cool repo: https://github.com/nstrayer/cv**

I have attempted to keep the whole thing as easy as possible to understand and modify by using a publically available sheet and preserving the old CSV driven way behind a boolean variable that can be set in the setup chunk. 


## Structure

This repo contains the source-code and results of my CV built with the [pagedown package](https://pagedown.rbind.io) and a modified version of the 'resume' template. 

The main files are:

- `index.Rmd`: Source template for the cv, contains a variable `PDF_EXPORT` in the header that changes styles for pdf vs html. 
  - `index.html`: The final output of the template when the header variable `PDF_EXPORT` is set to `FALSE`. View it at [ryanpeek.org/cv](https://ryanpeek.org/cv).
  - `peek_cv.pdf`: The final exported pdf as rendered by Chrome on my mac laptop. Links are put in footer and notes about online version are added. 
- `resume.Rmd`: Source template for single page resume. 
  - `resume.html`/`peek_resume.pdf`: Result for single page resume.
- `parsing_functions.R`: A series of small functions for parsing a position entry into the proper HTML format. Includes logic for removing links if needed etc..
- `gather_data.R`: Loads the data that makes up the body of both the CV and resume. Either pulls from a specified google sheet with info or multiple csvs. (Examples of both are provided in repo.)
- `csvs/*.csv`: A series of CSVs containing the information CV and resume. Included as examples if the non-googlesheets method of storing data is prefered.  
- `css/`: Directory containing the custom CSS files used to tweak the default 'resume' format from pagedown. 

## Want to use this to build your own CV/resume? 

1. Fork, clone, download the zip of this repo to your machine with RStudio.
2. Make a copy of my [info-holding google sheet](https://docs.google.com/spreadsheets/d/1S5al5nRok8JuYBlf2mx43OoHI3p4QvZ4TrSAf-6Cjf8/edit?usp=sharing) and fill in your personal info for all the sheets (`positions`, `language_skills`, `text_blocks`, and `contact_info`). 
    a. If you want to use CSV's instead of google sheets, update the contents of the CSVs stored in the `csvs/` folder. 
3. Go through and personalize the supplementary text in the Rmd you desire (`index.Rmd` for CV, `resume.Rmd` for resume).
4. Print each unique `section` (as encoded in the `section` column of `positions.csv`) in your `.Rmd` with the command `position_data %>% print_section('education')`.
5. Get the PDF out by viewing in your browser and then doing `control/command + P` and selecting "print to pdf". Alternatively use `pagedown::chrome_print()` or `knit: pagedown::chrome_print` in RMD header. See [pagedown docs on printing](https://pagedown.rbind.io/#print-to-pdf) for more details.
6. Let the world know how awesome you are! (Also send me a tweet/email if you desired and I will broadcast your version of the CV on this repo and or twitter.)



