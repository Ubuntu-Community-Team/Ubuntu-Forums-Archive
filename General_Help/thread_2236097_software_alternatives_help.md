---
title: "software alternatives help"
date: 2014-07-24
forum: General Help
---

### Post by freewarelover on 2014-07-24
In my search to find linux equivalents of certain software I'm left with these remaining issues that I really would like to get resolved. 

1. For the longest time I've been in search for the linux equivalent of something that can make a pdf searchable. I recently found this. [http://linux-beta.slashdot.org/story/10/07/22/1852234/open-source-ocr-that-makes-searchable-pdfs](http://linux-beta.slashdot.org/story/10/07/22/1852234/open-source-ocr-that-makes-searchable-pdfs) Watchocr doesn't seem to exist anymore and the others did install but I can't find them in the start menu sub-menus of Lubuntu. I've google for the equivalent of the program files folder in linux and have read that it's the /bin or /usr/bin or /usr/share and although usr/share has folders with names of apps none of them (that is usr/bin, usr/share, bin) seem to have the exe to run the app. I used to think the .exe didn't exist in the linux world but in my search to find a piece of software that could make pdfs searchable I came across a piece of software that said in the install instructions I was reading to click on a file which ran the program. (was imageviewer aka master pdf editor) 
2. Is there a linux equivalent to the math ability that MS office has. (since 2007) Is the closest thing to that libreoffice math? Libreoffice math is nice but it doesn't seem to give any format control (which is necessary for homework purposes) (libreoffice math seems seems to put math formats randomly all over the place on the page)

---

### Post by grahammechanical on 2014-07-24
You are right about one thing. Windows exe files do not run or install under Linux. So, it is no good looking for them in usr/bin or usr/share/bin or any where else that a native Linux application would put its binary (executable) files.

Perhaps you are thinking of Wine? 

[http://www.winehq.org/download/](http://www.winehq.org/download/)

There is a Linux application that is part of the default Ubuntu installation called Image Viewer. It does just that. It views images. I do not think that it will covert a PDF document into a searchable PDF document. I do not see any claim for Master PDF editor that it can make a non-searchable PDF into a searchable PDF.

> [COLOR=#252525][FONT=sans-serif]PDF files created by [/FONT][/COLOR][scanning]("http://en.wikipedia.org/wiki/Image_scanner")[COLOR=#252525][FONT=sans-serif] hard-copy documents containing primarily text do not have the same structure as a PDF file of the same document created directly. The scanned document internally contains a picture of the document, with no information about the text. As far as a user can see it is just another PDF file, with a name and extension indistinguishable from any other; a good scan may look exactly the same as a native PDF file, although a visually poor-quality file, often with skewed pages, gives away its nature. However, the file size will be different, and it will not be possible to search for text. For a scan of adequate quality it is possible with suitable software to regenerate the text of the document with [/FONT][/COLOR][Optical character recognition]("http://en.wikipedia.org/wiki/Optical_character_recognition")[COLOR=#252525][FONT=sans-serif] (OCR), and embed it in the file so as to make it searchable, subject to the accuracy of the OCR.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/PDF](http://en.wikipedia.org/wiki/PDF)

I have never tried to OCR a page of a PDF document that is made up of scanned images.

Regards.

---

### Post by freewarelover on 2014-07-24
My mistake it turns it was a type of image file that just opened in imageviewer and when imageviewer opened I thought *that* was the program because I'd never seen imageviewer open before. So I guess that leaves another question, when a program is executed on linux (via the start menu in Lubuntu) what file(s) is/are executed? Is the icon in the start menu linked to multiple files instead of the one executable like it is in windows? If it is linked to multiple files what the extensions of those files? Are the regular source code files like .cpp, .java, .c, .h ect?

---

### Post by buzzingrobot on 2014-07-24
Doesn't Adobe Reader have a search function? And, I think, it's available for Linux. A number of Linux PDF readers exist; I wouldn't be surprise if one or more had search.

"recoll' --available in a PPA -- is a desktop index and search tool that knows about PDF's.  You tell it which directories you want indexed, make sure it runs periodically, then use it to search.  You will likely need to install some "helper apps" that Recoll uses to display the files it locates, but it lists the needed ones for you at the conclusion of its initial indexing run.

---

### Post by freewarelover on 2014-07-24
> **buzzingrobot said:**
> Doesn't Adobe Reader have a search function? And, I think, it's available for Linux. A number of Linux PDF readers exist; I wouldn't be surprise if one or more had search.
Yes but only if the pdf is already **searchable** if it hasn't been made searchable the search tool in  adobe reader (and others) is useless.
> 
"recoll' --available in a PPA -- is a desktop index and search tool that knows about PDF's.  You tell it which directories you want indexed, make sure it runs periodically, then use it to search.  You will likely need to install some "helper apps" that Recoll uses to display the files it locates, but it lists the needed ones for you at the conclusion of its initial indexing run.
Umm thanks. Not sure I'll ever need that but I'll check it out.

---

### Post by buzzingrobot on 2014-07-24
> **freewarelover said:**
> Yes but only if the pdf is already **searchable** if it hasn't been made searchable the search tool in  adobe reader (and others) is useless.



In any case, some programs are clever enough to install themselves in a menu, and some are not.  I don't use Lubuntu, so I don't know specifics about its menu.  In my experience, though, if a package creates a ".desktop" file and puts it in /usr/share/applications, it has turned up in the menu. Othewise, executables are searched for along the Path.  Here, the path looks like this:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```

Apps intended for use by humans will typically be in /usr/bin. /usr/local/bin is often used by locally built and install software.

---

### Post by freewarelover on 2014-07-24
> **buzzingrobot said:**
> In any case, some programs are clever enough to install themselves in a menu, and some are not.  I don't use Lubuntu, so I don't know specifics about its menu.  In my experience, though, if a package creates a ".desktop" file and puts it in /usr/share/applications, it has turned up in the menu. Othewise, executables are searched for along the Path.  Here, the path looks like this:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```

Apps intended for use by humans will typically be in /usr/bin. /usr/local/bin is often used by locally built and install software.
Thanks. I think I've been in that folder before but it always looked intimidating. Dunno what the deal is with the two programs I mentioned in the first post. Their executables don't do anything. (removed them)

Edit: I figured out the answer to my second question about libreofficce math. I didn't know libreoffice writer had a way of inserting formulas because I didn't see it before and ended up finding youtube video on it. 

Note for feature readers with the same issue: go inset>object>formula and learn how to write formula syntax via libreoffice math with the element table.

Edit2: the thing that still remains is how to make pdfs searchable. A friend showed me this but it's repository won't update so I can't install it. [http://ubuntuforums.org/showthread.php?t=1456756](http://ubuntuforums.org/showthread.php?t=1456756)

Edit3: problems solved. As far aas converting pdfs to docs I was never able to find something that could do it but have decided to live without since document viewer can copy text. Regardless though I'm surprised it hasn't been done yet for linux. I found an extension for libreoffice that claimed to be able to do it but couldn't figure out how to work it. As far as finding something that could make pdfs searchable I did. The program is called gscan2pdf Must admit my experience with pdfocr helped because gscan2pdf uses the OCR which wasn't defined to me until dealing with pdfocr.

---

### Post by Rob Sayer on 2014-07-25
Maybe there's something I'm missing but I use okular as a pdf reader on my kubuntu machine ... it's the standard KDE app which came with the install ... and I've text searched pdf's a zillion times with it.

---

### Post by freewarelover on 2014-07-25
> **Rob Sayer said:**
> Maybe there's something I'm missing but I use okular as a pdf reader on my kubuntu machine ... it's the standard KDE app which came with the install ... and I've text searched pdf's a zillion times with it.
Yes you were able to do that because the pdfs you searched in were already made searchable, if they weren't made searchable you wouldn't be able to search for words in them because the reader wouldn't recognize the pdf to have individual words because it would only see the pages as images. In any event I self-solved all questions I had in this thread. It can be marked as solved.

---

