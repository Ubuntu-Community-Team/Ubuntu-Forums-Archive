---
title: "What is ImageMagick used for?"
date: 2016-10-28
forum: General Help
---

### Post by aajax on 2016-10-28
I'm looking for something that would allow me to turn a screen-shot (i.e., graphic data on the clipboard) into a file in graphic format (e.g., giff, png, jpg, etc.).  My newly installed Ubuntu 16.04.1 has something called ImageMagick already installed.  In fact, it shows up twice on both the list of installed software and the ICONs on the launcher.  However when you launch it nothing happens.  Actually an ICON shows up momentarily in the task bar and then quickly disappears.  I don't see any sign of any kind of window being opened.

The [ImageMagick website]("http://www.imagemagick.org") describes it as having lots of capability but suggests that it might normally be used via CLI which I find to be a bit odd.

The remarks in the Ubuntu Software application make it sound pretty dubious and problematic.  Is it possible that I've simply failed to recognize some little secret that turns on the supposedly powerful software?

I'm not wed to ImageMagick, I'm new to Ubuntu 16.04.1 and was hoping that I could find something pre-installed that would easily accomplish turning a screen-shot into a graphic file.  In that, something like Paint on MS Windows.  Is this possible?  If so what software is the right choice?

---

### Post by ian-weisser on 2016-10-28
Imagemagic is indeed a powerful and handy graphic manipulator and translator.
It is indeed primarily a command-line application, which is very handy for scripts or programs to manipulate images.

Output the screenshot as a file instead of to the clipboard (gnome-screenshot, for example, outputs png files)
Then use imagemagick's convert command: 'convert image.png image.gif'

---

### Post by pqwoerituytrueiwoq on 2016-10-29
imagemagick does includes a GUI (at least on 14.04) /usr/bin/display.im6 
never used the GUI on it myself, just command line stuff/scripts
if you are mainly interested in taking screenshots with it:
[https://wiki.archlinux.org/index.php/taking_a_screenshot#ImageMagick.2FGraphicsMagick](https://wiki.archlinux.org/index.php/taking_a_screenshot#ImageMagick.2FGraphicsMagick)

---

### Post by vasa1 on 2016-10-29
As ian-weisser suggested, use gnome-screenshot. It's simpler and comes with various options you can read about in *man gnome-screenshot*.

If you want to annotate or manipulate screenshots, Shutter is also very good. It may be installed by default on your system.

---

### Post by HermanAB on 2016-10-29
Imagemagick is also very easy to use and can convert pretty much anything to anything:

$ convert oldfile.jpg newfile.pdf

It also does file globbing, so you can convert a PDF into a series of jpg pages and then convert the series of pages into another single file again.

However, to come back to your original question, just press the printscreen button and a screen grab utility should pop up, allowing you to save a grabbed window or rectangle to a file.

---

### Post by SeijiSensei on 2016-10-29
If you want a full-bodied graphics program, you can use the [GIMP]("https://www.gimp.org/") which is available from the repositories.  

As a Kubuntu user, the standard KDE graphics viewer Gwenview offers a number of functions for simple things like resizing, rotating, cropping, and even a number of additional enhancements if you install the "kipi-plugins" package.

I mostly use Imagemagick from the command line when I want to operate on a whole folder of images.  For instance, I uploaded a bunch of photos to my web server the other day and wanted to create thumbnails.  With Imagemagick I could run one command
```
$ mogrify -path thumbs -thumbnail 250 -format png *.jpg
```
to create PNG thumbnails of all the JPEGs, each with a width of 250 pixels, and store them in the "thumbs" subdirectory.

---

### Post by oldfred on 2016-10-29
This site has many scripts/examples. 
The examples so some of what you can do.

Another Fred with many scripts for imagemagick with examples
[http://www.fmwconcepts.com/imagemagick/index.php](http://www.fmwconcepts.com/imagemagick/index.php)

---

### Post by aajax on 2016-10-31
Many thanks!  Lots of helpful replies.

It looks like my intuition lead me in a different direction.  I wasn't thinking of using the command line interface for processing graphics.  Likewise, when an ICON, actually 2 of them, showed up in what looks to me like the prescribed launcher for programs I tried launching it with the mouse. I suppose what I experienced is what one might expect from a program without any GUI.

---

### Post by aajax on 2016-10-31
pqwoerituytrueiwoq says > imagemagick does includes a GUI (at least on 14.04) /usr/bin/display.im6 

I tried it and you do get a splash screen to display that says ImageMagick but the only things to do with it were close|minimize|maximize.  So far not much help.

---

### Post by aajax on 2016-10-31
Have worked with GIMP on Windows and it is what you need to use for sophisticated processing but it's not pre-installed on ordinary Ubuntu 16.04.1.

---

### Post by Geoffrey_Arndt on 2016-10-31
Maybe I'm missing something, but what's wrong with the pre-installed screen-shot program (amazingly, called "Screenshot") . . . places a Camera icon in the standard Launcher.   Works great and saves to png and i think it also saves to jpg format.   Simple to use, perhaps I misinterpreted the original question?

---

