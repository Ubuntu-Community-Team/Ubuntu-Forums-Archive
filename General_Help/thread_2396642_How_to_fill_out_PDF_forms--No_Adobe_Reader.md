---
title: "How to fill out PDF forms--No Adobe Reader"
date: 2018-07-18
forum: General Help
---

### Post by Ralph L on 2018-07-18
I can no longer find Adobe Reader for Linux on the Adobe web site.  I have the old Adobe Reader 9.5.5-1, but when I installed it inXubuntu 18.04 (64 bit), it wouldn't run saying ```
ralph@asp1:~$ acroread
/opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory
ralph@asp1:~$ 


```  How are people filling out PDF forms???????  In the past I have found that Adobe Reader was best for that purpose.  I have also used Okular and Evince Document Viewer, but they don''t always work correctly.  Is there a better PDF program out there???  How about running the Windows version under Wine?  Has anybody had good luck with that approach.

---

### Post by rbmorse on 2018-07-18
I use Master PDF Editor which works fine, but it's a commercial program (not free).  I don't remember for sure...I think the license is about $50 USD.  Updated regularly and support via e-mail is timely and effective. There's a free trial, but I think it leaves a watermark. 

As far as free solutions,  it's a little clunky, but if you're just doing the occasional form, The GIMP and its text tool is serviceable.  One year where I did my entire U.S Income tax return (Form 1040 and supplemental schedules) with it.  It worked pretty well once I got the hang of how to use the text box locator and remembered to flatten all the layers when I was done with a page.

---

### Post by HermanAB on 2018-07-18
I just write anywhere I want using Xournal and then export the form back to a new PDF.

---

### Post by Ralph L on 2018-07-23
Thanks for the input.  It was helpful. I didn't know about Master PDF Editor, nor xournal.  I will try these.  I also found a free version of PDF Studio Viewer  at [https://www.qoppa.com/pdfstudioviewer/](https://www.qoppa.com/pdfstudioviewer/) .

---

### Post by mIk3_08 on 2018-07-23
Install PDFsam
PDFsam requires a java runtime environment 8 (or above) with javafx to run
in terminal run this code below
```
sudo apt install openjdk-8-jre libopenjfx-jni libopenjfx-java openjfx
```
then install PDFsam via software

---

### Post by sudodus on 2018-07-23
> **HermanAB said:**
> I just write anywhere I want using Xournal and then export the form back to a new PDF.

+1 for Xournal :-)

---

### Post by dragonfly41 on 2018-07-23
FoxitReader has some interesting features.

[https://www.foxitsoftware.com](https://www.foxitsoftware.com)

---

### Post by monkeybrain20122 on 2018-07-23
I think evince (document reader) has form filling feature though probably kind of rudimentary. qpdfview also has form filling feature (IMO by far the best pdf reader on Linux too, but install it with the [ppa]("https://launchpad.net/~adamreichold/+archive/ubuntu/qpdfview-dailydeb") instead of the very outdated version in repo, some new improvements really rocks) Unfortunately all Linux pdf readers (at least the free ones) use poppler as it backend so some forms may have features that are not supported (scripts, e.g) In those cases running pdf-xchange viewer in wine would work, it is light and works perfectly in wine.

---

### Post by monkeybrain20122 on 2018-07-23
> **dragonfly41 said:**
> FoxitReader has some interesting features.

[https://www.foxitsoftware.com](https://www.foxitsoftware.com)

The Windows version may be good, but the Linux version is meh. Foxit for Linux is very basic. qpdfview blows it out of the water for a tabbed reader. :)  Foxit linux does not open .djvu files (.ps?) and only allows 20 tabs max. qpdfview supports more formats and allows unlimited tabs and loads very fast too even with ~ 50 tabs on a moderately specs laptop (for the ppa version) Besides foxit linux has not updated for quite a while.

---

### Post by ajgreeny on 2018-07-23
Another vote for **xournal** from me.

Just remember that you have to open the original pdf file, add your notations or whatever, then export it again as a pdf.
It might sound a bit clunky, but it can do a superb job and place the text anywhere at all; wherever you put the cursor, so is incredibly flexible and versatile.

---

### Post by monkeybrain20122 on 2018-07-23
> **ajgreeny said:**
> Another vote for **xournal** from me.

Just remember that you have to open the original pdf file, add your notations or whatever, then export it again as a pdf.
It might sound a bit clunky, but it can do a superb job and place the text anywhere at all; wherever you put the cursor, so is incredibly flexible and versatile.

If i need to sign the form I would use xouranal with a stencil or something, but it is not much good for filling forms in my experience, when typing characters often appear out of the box for some reasons.

---

### Post by Ralph L on 2018-07-23
Thanks to even more people who have replied.....
monkeybrain20122:  I also use qpdfview (version 0.4.17.99~2083~63~ubuntu18.04.1) and like using it for reading (except when set to Continuous, Fit To Page, Trim Margin, and scrolled up and down with PageUp/PageDown keys, it loses full page and ends up with partial pages), but have been unable to get it to fill out forms.  
Please tell me how to fill out pdf forms with qpdfview.

---

### Post by monkeybrain20122 on 2018-07-24
> **Ralph L said:**
> 
Please tell me how to fill out pdf forms with qpdfview.

Just open the form, type into the text box and save.

---

### Post by TechnoJunky on 2018-07-24
I use Okular.  It's in the repo.

---

