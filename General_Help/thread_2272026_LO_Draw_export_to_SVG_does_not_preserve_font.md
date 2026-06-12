---
title: "LO Draw export to SVG does not preserve font"
date: 2015-04-03
forum: General Help
---

### Post by Buntu Bunny on 2015-04-03
I'm working on a calendar project in Scribus 1.4. I discovered Sribus is weak in the table department, so after some research, started making my tables in LibreOffice Draw and exporting them as SVGs to import into Scribus. However, the font I've chosen is not preserved, rather the SVGs are in a different font. I've set the desired font and size in table properties, and I can 'save as' or export as PDF with the proper font. Not so with SVG. Is there some way I can get the font I want, or is this a native problem with SVGs?

---

### Post by mcduck on 2015-04-03
This happens while working on one and the same computer, where the font you are using is installed system-wide so that's it's available (and visible in both programs)?

The font itself might not be included in the SVG files, only referenced, so you need the same font to be available on the machine (and program) viewing the file. (or vectorize the text like you'd do before sending any files to print, for example)

edit: I tested this quickly,  and at least with default settings LO seems to add the used glyphs in the SVG file, so it should work even without having the correct font, at least as long as you don't try to change the text and add letters that were not included, and that the  program viewing the file chooses to use the embedded glyphs. So my test file opened just fine and with correct fonts in Inkscape. Maybe you could test with IS, just to see if the problem is related to Scribus, or LO export. (and also keep in mind that the SVG is actually a text file, so you can easily open it with a text editor to check if the font information or used glyphs are included or not...)

---

### Post by Buntu Bunny on 2015-04-03
mcduck, thank you for your reply. The font *is* available in both programs. It's pre-installed, actually. What I'm having to do is import a blank formatted table into Scribus and apply my chosen font there via text boxes. It's a little quicker and easier to do in Draw, but I'm doing what I have to do. 

EDIT: I should add that the thumbnail preview of the exported SVG shows the default font. Thumbnails of the PDF show chosen font. So it appears to have something to do with Draw's export function. Just want to make sure I'm not missing something. 

It occurred to me to try it in Inkscape. Will report back on that.

---

### Post by Buntu Bunny on 2015-04-06
Best solution seems to be to create the tables in Scribus trunk, which I will need anyway to prepare the document for print. Seems that it would still be easier to do in LO Draw, but the fonts clash and that is not acceptable. If I ever figure out how to preserve the font in the SVG conversion, I'll update this thread in case anyone else has the same question.

---

