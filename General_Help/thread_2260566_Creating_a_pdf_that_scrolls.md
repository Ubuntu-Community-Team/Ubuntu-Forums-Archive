---
title: "Creating a pdf that scrolls"
date: 2015-01-12
forum: General Help
---

### Post by hreichgott on 2015-01-12
Hello, I occasionally scan scores (sheet music) into .pdf form to read on a tablet while I play music. The tablet has a USB foot pedal that sends up arrow/down arrow signals to the tablet. 
On most .pdfs, the up arrow/down arrow scrolls the page upward/downward just a little bit, very useful when reading music. 
On the .pdfs I create, the up arrow/down arrow flips immediately to the next page, and appears to be moving left/right though it's so fast it's hard to tell. Not as useful.
Is there a way to create .pdfs that will scroll the way I want?
I know my reader is not the problem, as .pdfs I didn't create work great, and my .pdfs have this problem even when reading on other computers/OSs.

I am currently using gscan2pdf, sometimes gimp + pdftk.
Thanks

---

### Post by Impavidus on 2015-01-13
Some pdfs contain instructions for pdf viewers to change their default settings, like pdfs automatically triggering presentation mode. It should be possible to override. After opening the pdf, go to the settings of the pdf reader and find something like "single page" or "continuous". Maybe the program you used for creating the pdf also has a setting to remove this default page by page behaviour.

---

### Post by dragonfly41 on 2015-01-13
The default PDF viewer on my Ubuntu 14.04 is Evince.

With View > Continuous selected in Evince toolbar the up/down arrows go in small steps through multiple pages and doesn't jump at page breaks. But I imagine in reading and playing music scores you need smoother increments in scrolling.

Possibly you could achieve smoother scrolling SVG in a browser rather than using default PDF viewer.

The issue is to convert the PDF file (multiple pages) to multiple SVG files (one SVG file per PDF page) and embed into HTML container with smoother scrolling.


Some ideas for this ...

Install pdf2svg from Ubuntu Software Centre to convert PDF to SVG format.

Go to the folder containing test multiple page musicscore.pdf.

Launch terminal in that folder and run

pdf2svg musicscore.pdf musicscore%d.svg all

Note the use of %d for numbering all pages.

This will create multiple SVG files

musicscore1.svg
musicscore2.svg
musicscore2.svg
etc.

Then create a simple HTML container to place the svg objects each in its own div. 

I leave you to research how to do that.  "embed SVG objects in HTML"

But one tip .. when embedding each SVG file strip off the first line ..

<?xml version="1.0" encoding="UTF-8"?>

so that you only embed the svg 

<svg> ... </svg>

The resulting HTML page can be scrolled.

As a further refinement if using Firefox as your browser there is an add-on "SmoothWheel".

After installation go to SmoothWheel Preferences and set parameters such as scroll step size.

You can also tick "use with Up/Down" for smooth scrolling to be controlled with your foot control.

---

### Post by hreichgott on 2015-01-14
Fixed it!
Scanned to a group of .png images, one per page, and used convert to build the pdf.

---

### Post by dragonfly41 on 2015-01-14
After I posted the svg suggestion I ran a quick test and with HTML I could add a javascript function
to run smoothly through the HTML file.

I would imagine that you could avoid the conversion to pdf and include your images in HTML file.

Then use a scroll javascript function like this with body tag in HTML page ..

<body onLoad="pageScroll();">

js:

```

function pageScroll() {
        window.scrollBy(0,1); // vertical scroll increment 1px .. very smooth
        scrolldelay = setTimeout('pageScroll()', 50); // scrolls every 50 milliseconds .. scroll speed
}

```

Other refinements would be to use your foot controls to go forward and back in score via javascript.

---

