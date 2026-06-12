---
title: "openoffice as a desktop publsiher (dtp)?"
date: 2007-09-27
forum: General Help
---

### Post by gobbles414 on 2007-09-27
Hi all,

Thanks in advance for helping me. :)  If you are uninterested in the background of my problem. Please skip to question 1.

BACKGROUND:
I have been trying to import a 140 page .doc file into [Scribus]("http://www.scribus.net") (1.25, 1.3.3.9 and 1.4 snapshot) for conversion into a PDF-formatted ebook. I have tried exporting from OpenOffice to Scribus as .odt .sxw .pdb .ps and a couple variations of .html. Some of these will import without footnotes, the remaining will not import at all. Copy and paste fails as well. If I save a successful import in any version of Scribus using the default or compressed Scribus formats, Scribus is unable to open the saved file. Obviously, this is unacceptable. Scribus looks like a great program for smaller documents such as newsletters and posters. And I'm sure that the Scribus development teams are doing the best possible work to make Scribus load large files. LyX does not have nearly as many import problems with the document. However, LyX is not enough of a desktop publisher for my needs. Passepartout does not appear to support documents of this size. PageStream is a possibility. But it costs lots of money. I am on 32-bit Feisty. EDIT: I need the ability to view formatted text and graphics in "real time". 

QUESTION 1:
Do any of you have experience using OpenOffice 2.x as a desktop publisher? I would love to hear any ideas that you might have about the following:

* applying a template with a company logo or the like to all pages but the cover page
* creating a table of contents that links to the appropriate page in the document (click on the TOC entry and get sent to the correct page). This functionality would need to survive in the final PDF
* In the past, I have made newsletters with OpenOffice using text boxes to separate paragraphs in a professional-looking manner. Is there an easier way to do this, considering that I am dealing with a 140 page document? :confused:

QUESTION 2:
Is there an inexpensive or free DTP program that works well with Wine? I know which ones are reported to work with Wine. I am looking for more "first-hand" information. I will still need to be able to export to PDF when I am finished.

---

### Post by aquavitae on 2007-09-27
You can do what you want in open office, but its a bit of a pain.  I can probably help with any specific questions if you decide to do it that way, but personally, I'd suggest latex.  I used latex (in the form of lyx) for my thesis and its far more powerful than it appears.  I don't believe lyx is the best frontend for it though - try texmaker (gnome) or kile (kde) instead.  There's quite a learning curve involved, but the three points you mention in Q1 can certainly be done and I find it more reliable and easier than openoffice.

---

### Post by gobbles414 on 2007-09-27
Hi aquavitae,

Thanks for your reply. Texmaker and LyX are similar in that they [EDIT] are both frontends for a "typesetting" application. As you have said, that would be great for a thesis. However, my ebook is going to contain many graphics and, the way my brain works, I need to be able to see in real time how my text and graphics relate to one another.

I experimented last night with OpenOffice, and I believe that I have discovered how to do an interactive TOC -- although I would still be interested in learning the easiest way to do it in Writer. I'm sure that I am making the procedure more difficult than it needs to be. :lolflag: Anyway, I'm not committed to OpenOffice if there is another application that you can recommend. Although I've never used the program, something like Apple iWork would be ideal I think. Too bad that there isn't a Windows version that can be run in Wine... :(

---

### Post by gobbles414 on 2007-09-27
bump

---

### Post by aquavitae on 2007-09-28
Yes, if there are a lot of graphics I can see the problem.  I think in that case I would go with writer.  I don't know how you've done you TOC, but the way I would do it is through styles.  Modify and create styles (inparticular the heading styles) as necessary, apply them to your doc, and then use Insert - Indexes and Tables - Indexes and Tables to add a TOC.  Select Create From Additional Styles (disable outline) and choose the heading styles you want.  There are also various options for how to display the TOC, but it should be easy to work out.  I find it much more straight forward than msword!!!  

Just a tip - I've had problems in openoffice before with lots of frames.  Don't use them if you can avoid it.  You'll obviously have to for the graphics but don't use them for the text.  Also, don't try to draw diagrams in openoffice, use inkscape or something similar instead.

---

### Post by gobbles414 on 2007-09-28
aquavitae,

I've been attempting to guide myself through the work of converting my document into an ebook in OpenOffice. Actually, I am having some success. Frames, pictures, and text boxes are a pain for me to work with in OpenOffice though. This is mainly because I cannot group pictures and text boxes together -- as you alluded to in your most recent reply. I have found myself using STYLES AND FORMATTING a lot for altering page styles. Using page styles, I have been able to design a cover page without changing the rest of the document. I'll let you know how I progress with my TOC. Thanks again... :KS

---

### Post by aquavitae on 2007-10-01
The best way to group boxes is to put them in one frame, but its slow and painful.  One way to do it would be to design the contents of the box (text and graphics) in inkscape, save it as an svg image and load it as a picture into openoffice.  I haven't tried it but it should work.  You won't lose resolution on the text because its scalable (but make sure the image is at 100% scale in openoffice)

Good luck with the TOC!

---

