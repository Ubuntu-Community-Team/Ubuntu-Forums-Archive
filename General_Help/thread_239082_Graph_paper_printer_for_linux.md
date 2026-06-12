---
title: "Graph paper printer for linux?"
date: 2006-08-18
forum: General Help
---

### Post by linmick on 2006-08-18
Hello, does anyone know for linux a graph printing program? That is  not just one graph something like:  [http://www.incompetech.com/beta/plainGraphPaper/](http://www.incompetech.com/beta/plainGraphPaper/)  (only this is not an offline printer) I have a graph paper printer but it needs  wine ".exe" windows. It works  but not native to linux. It basically has any type of  custom graph paper to print.


Thanks

---

### Post by zami on 2007-02-09
This post is very dated, but I wanted to chime in that I'm looking for a graph paper generator too.

So if any one knows of one, please, pipe up!

-zami

---

### Post by WW on 2007-02-10
Here's a quick-and-dirty python program for generating very simple graph paper PDF files.  It creates just plane rectangular grids--nothing as fancy as the generator linked to by the original poster.  But if anyone wants to hack away at it, be my guest.

To use it, you will first have to install the packages python-gtk2 and python-reportlab. They are both available in the Ubuntu main repository.

Edit: See the newer version in my post below.

---

### Post by WW on 2007-02-12
For kicks, and to learn more Python and PyGTK, I've been making more changes to this program.  Here is version 0.2 (along with a screen shot).

EDIT 17 Feb 2007: I have updated the attachments with a new version (version 0.3).

I have expanded my widget repertoire beyond radio buttons. :)

I have dropped the .py extension in this version.  Save the file in a directory, and enter the following commands in a terminal.
>  $ cd /directory/where/you/put/the/file
$ bunzip2 graphpaper.bz2
$ chmod a+x graphpaper
$ ./graphpaper


---

### Post by zami on 2007-02-13
This program is excellent, THANK YOU!

The linked-to program is yes, much fancier, but I was only looking for straight-up, grid-style graph-paper, so your program is just perfect.

And it's offline which I think is what the original poster was looking for, too.

If you take suggestions for future versions, I'll throw in my vote right now for even larger grid spacing.

(I dork, use the teeny/mid grids for RPGs.  I mom, use the fatty grids for chore lists and whatnot.)

Thanks again for sharing your script!

-zami

---

### Post by WW on 2007-02-17
zami,

Check out the new version above.  It allows you to enter the size of the grid.

---

### Post by zami on 2007-03-27
My reply is a little late but, I just want to say I love, love, love this program!!

Especially now that it makes itty bitty spaced grid lines.  

Bravo!

-zami

---

