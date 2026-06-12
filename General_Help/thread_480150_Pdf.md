---
title: "Pdf"
date: 2007-06-21
forum: General Help
---

### Post by Howard Kaikow on 2007-06-21
In Windows, I have the full Acrobat 5 product, and Scansoft PDF Converter Professional.

What programs are available in Feisty to accomplish most, if not all, of the functions of those programs?
For example, te Scansoft program is pretty good at converting PDF to other formats, including Word, Excel and RTF.

---

### Post by yota on 2007-06-21
Hi, first of all check these sites:

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)
[http://www.linuxalt.com/](http://www.linuxalt.com/)

Speaking about acrobat specifically, OpenOffice can export to pdf natively (file/export to pdf).
Several (command line) tools are available to convert pdf to other formats: pdftohtml for instance does what it says, while gs-common contains the 'pdf2ps' command which converts pdf to postscript which can be edited with any desktop publishing program as scribus.

Hope this helps!

---

### Post by Brucevdk on 2007-06-21
> **Howard Kaikow said:**
> For example, te Scansoft program is pretty good at converting PDF to other formats, including Word, Excel and RTF.

Like Yota mentioned there are a couple of command line tools such as pdftohtml but they aren't all that great. I'd like to add KWord (from KOffice) which can open PDF files and save in any of the supported output formats, it's not perfect but it sort-of works ([see this article]("http://ubuntu.wordpress.com/2007/04/10/convertimport-from-pdf-and-keep-the-formatting/") [ubuntu.wordpress.com]). I don't know the featureset of the programs you mentioned but it's highly unlikely that there's something for GNU/Linux that does the same.

---

### Post by Howard Kaikow on 2007-06-21
> **yota said:**
> Hi, first of all check these sites:

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)
[http://www.linuxalt.com/](http://www.linuxalt.com/)

Speaking about acrobat specifically, OpenOffice can export to pdf natively (file/export to pdf).
Several (command line) tools are available to convert pdf to other formats: pdftohtml for instance does what it says, while gs-common contains the 'pdf2ps' command which converts pdf to postscript which can be edited with any desktop publishing program as scribus.

Hope this helps!

Thanx, I'll take a look.

Open Office does not help.

1. I need to edit the PDF document without converting to another app, as with full Adobe Acrobat.

2. I need a PDF printer, so I can create PDF from ANY app. 

I installed CUPS-PDF, but it did not add a printer.
I guess I have to somehow make that printer active.
I just download the instructions for setting up the virtual PDF printer.

---

### Post by Howard Kaikow on 2007-06-21
> **Brucevdk said:**
> Like Yota mentioned there are a couple of command line tools such as pdftohtml but they aren't all that great. I'd like to add KWord (from KOffice) which can open PDF files and save in any of the supported output formats, it's not perfect but it sort-of works ([see this article]("http://ubuntu.wordpress.com/2007/04/10/convertimport-from-pdf-and-keep-the-formatting/") [ubuntu.wordpress.com]). I don't know the featureset of the programs you mentioned but it's highly unlikely that there's something for GNU/Linux that does the same.

THanx.

The idea is to avoid the intermediate conversion to, say, a Word processor.

---

### Post by Howard Kaikow on 2007-06-21
is there a way to do n-up printing?
2-up is usually sufficient.

Or does one have to use tools such as pstools?

---

### Post by yota on 2007-06-21
Evince supports n-up printing, you'll find the setting on print/settings.

I'm not aware of applications that can directly edit .pdf files on linux, but usually pdf<->ps conversions can be performed flawlessly since pdf is a ps superset.

---

### Post by Howard Kaikow on 2007-06-21
> **yota said:**
> Evince supports n-up printing, you'll find the setting on print/settings.

I'm not aware of applications that can directly edit .pdf files on linux, but usually pdf<->ps conversions can be performed flawlessly since pdf is a ps superset.

I am looking for at least the following:

1. Abilty to create PDF anytime, e.g., when printing a web page.
Perhaps, CUPS-PDF will allow this.

2. Ability to do n-up when printing, be it PDF or Postscript.

3. Ability to edit PDF files, such as tax forms, without doing tumblesaults. Since I am running linux/winows multiboot, I can always boot to windows to do the deed, but that's a pain in the back rank, to use polite chess teminology.

---

### Post by yota on 2007-06-22
Hi again:

1. Cups-pdf is probably what you're looking for. But installing cups-pdf does not create any printer, you'll have to add one by yourself: select cups-pdf virtual printer and use "generic/postscript color" or "generic postscript" as drivers.
Details about cups pdf can be found in /usr/share/doc/cups-pdf/ (most packages have their docs in /usr/share/doc/*packagename*)
When you print to cups-pdf a file will be generated under the folder "PDF" in your home directory.
By the way any application can print to a file and that file is in postscript format which, as already stated, can be modified and converted to pdf.

2. Evince isn't good for you? it can do n-up printing of pdf and ps.

3. Ok, I if the pdf->ps->modify->pdf procedure isn't feasible, you can still use your favorite windows software under linux with vmware or virtual box (even seamlessly with rdesktop [http://ubuntuforums.org/showthread.php?t=224212](http://ubuntuforums.org/showthread.php?t=224212) ), so at least you're not forced to reboot.

Hope this helps.

---

### Post by kerry_s on 2007-06-22
you know can install acroread in linux, right?

---

### Post by Howard Kaikow on 2007-06-22
> **yota said:**
> Hi again:

1. Cups-pdf is probably what you're looking for. But installing cups-pdf does not create any printer, you'll have to add one by yourself: select cups-pdf virtual printer and use "generic/postscript color" or "generic postscript" as drivers.
Details about cups pdf can be found in /usr/share/doc/cups-pdf/ (most packages have their docs in /usr/share/doc/*packagename*)
When you print to cups-pdf a file will be generated under the folder "PDF" in your home directory.
By the way any application can print to a file and that file is in postscript format which, as already stated, can be modified and converted to pdf.

Yes, and that's what I did.

The difficuly was that the "documentation" at te cups-pdf web site was not sufficient, at least for me.
I found a Linux Journal article that described using a generic printer.

Did not know about /usr/share/doc.

Is there a GOOD BOOK that describes such general details about linux?
THe distro based books are way too general and lack details.

> 2. Evince isn't good for you? it can do n-up printing of pdf and ps.

The goal is to not have to first print to a ps or pdf file.
I often print, say, web pages 2-up to save paper.
Should be able to do this directly from within any app tat allows printing, such as Firefox, or gedit, or ...
> 
3. Ok, I if the pdf->ps->modify->pdf procedure isn't feasible, you can still use your favorite windows software under linux with vmware or virtual box (even seamlessly with rdesktop [http://ubuntuforums.org/showthread.php?t=224212](http://ubuntuforums.org/showthread.php?t=224212) ), so at least you're not forced to reboot.

I am trying to figure out what Linux can do, not via emulation.
The goal is to obviate the need for a Windows license.
Otherwise, why even bothe with Linnux

Thanx.

---

### Post by yota on 2007-06-23
> **Howard Kaikow said:**
> 
The goal is to obviate the need for a Windows license.
Otherwise, why even bothe with Linnux


For freedom, security and fun maybe. ;)

I don't know a single book that explains every detail about linux, but there's plenty of documentation online; maybe a look at [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) can clarify what is contained in each folder, while [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) has howtos on specific subjects. Since ubuntu is based on debian most debian documentation [http://www.us.debian.org/doc/](http://www.us.debian.org/doc/) applies to ubuntu too.
A solution for n-up printing from any app AFAIK is not already available, but probably could be achieved with some work.
Every application can print to postscript, and psnup can do n-up, so a virtual printer that automate the process
file.ps->nup-file.ps->real-printer
should do the job.
Maybe there's already something online.

---

### Post by Howard Kaikow on 2007-06-23
> **yota said:**
> For freedom, security and fun maybe. ;)

I don't know a single book that explains every detail about linux, but there's plenty of documentation online; maybe a look at [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) can clarify what is contained in each folder, while [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) has howtos on specific subjects. Since ubuntu is based on debian most debian documentation [http://www.us.debian.org/doc/](http://www.us.debian.org/doc/) applies to ubuntu too.

The quality/completeness of online documentation varies all over te place.
And, finding the appropriate document is like  ...!

I have corresponding Unix books from years ago, but there is a need for linux book.
A number of possibilitesare fond if one searches for "linux kernel" at [Bookpool]("http://www.bookpool.com/") and [Amazon]("http://www.amazon.com/").

This question is probably better asked in a programming forum.

> A solution for n-up printing from any app AFAIK is not already available, but probably could be achieved with some work.
Every application can print to postscript, and psnup can do n-up, so a virtual printer that automate the process
file.ps->nup-file.ps->real-printer
should do the job.
Maybe there's already something online.

I used to use psnup many years ago in windows 95.

---

### Post by jjross on 2007-06-23
This works for me 
Print to PDF 
[http://ubuntuforums.org/showthread.php?t=283198]("http://ubuntuforums.org/showthread.php?t=283198")

---

### Post by Brucevdk on 2007-06-25
> **Howard Kaikow said:**
> 3. Ability to edit PDF files, such as tax forms, without doing tumblesaults. Since I am running linux/winows multiboot, I can always boot to windows to do the deed, but that's a pain in the back rank, to use polite chess teminology.

I just stumbled upon a package called [PDFedit]("http://sourceforge.net/projects/pdfedit") (somebody namedropped it in the forums), this seems to be a basic PDF editor. Regrettably there doesn't seem to be an undo function :)

Adding and editing text is quite easy (though editing seems document specific and doesn't always work). To edit text you just select some text and then in the toolbar an input field pops up, if the text in the input field is readable you should be able to modify it. 

You can compile it from source or grab the RPM, convert it to deb and install it.

```

sudo apt-get install fakeroot alien
fakeroot alien pdfedit-0.3.1-1.i386.rpm
sudo dpkg -i pdfedit_0.3.1-2_i386.deb

```

---

### Post by moore.bryan on 2007-06-25
> **Brucevdk said:**
> I just stumbled upon a package called [PDFedit]("http://sourceforge.net/projects/pdfedit") (somebody namedropped it in the forums), this seems to be a basic PDF editor. Regrettably there doesn't seem to be an undo function
*this is a great suggestion... works incredibly well for me.  i, too, use adobe professional at work and although there is nothing quite as good for linux (yet, i hope), this a fairly decent work-around.  you could also try to edit through the gimp, but that doesn't always work for me.*

---

### Post by Howard Kaikow on 2007-06-25
> **Brucevdk said:**
> I just stumbled upon a package called [PDFedit]("http://sourceforge.net/projects/pdfedit") (somebody namedropped it in the forums), this seems to be a basic PDF editor. Regrettably there doesn't seem to be an undo function :)

Adding and editing text is quite easy (though editing seems document specific and doesn't always work). To edit text you just select some text and then in the toolbar an input field pops up, if the text in the input field is readable you should be able to modify it. 

You can compile it from source or grab the RPM, convert it to deb and install it.

```

sudo apt-get install fakeroot alien
fakeroot alien pdfedit-0.3.1-1.i386.rpm
sudo dpkg -i pdfedit_0.3.1-2_i386.deb

```


Thanx, I had heard about PDFedit, bur forgot about it.

What does "fakeroot alien" mean?

---

### Post by Brucevdk on 2007-06-25
> **Howard Kaikow said:**
> Thanx, I had heard about PDFedit, bur forgot about it.

What does "fakeroot alien" mean?

Straight from the man pages:

[LIST]
[*]**fakeroot** runs a command in an environment wherein it appears to have root privileges for file manipulation.
[*]**alien** is a program that converts between Red Hat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats. If you want to use a package from another linux distribution than the one you have installed on your  system, you can use alien to convert it to your preferred package format and install it.
[/LIST]

You use alien to convert the RPM from the website to a debian package (deb) which requires fakeroot so the owner/permissions on the files are set correctly.

---

### Post by Howard Kaikow on 2007-06-25
> **Brucevdk said:**
> Straight from the man pages:

[LIST]
[*]**fakeroot** runs a command in an environment wherein it appears to have root privileges for file manipulation.
[*]**alien** is a program that converts between Red Hat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats. If you want to use a package from another linux distribution than the one you have installed on your  system, you can use alien to convert it to your preferred package format and install it.
[/LIST]

You use alien to convert the RPM from the website to a debian package (deb) which requires fakeroot so the owner/permissions on the files are set correctly.

Thanx.

I do not have access to the man pages when booted to Windows.

Could not find any references in the Linux books I havem tbut then the books have such awful indices, the info may actually be there, just not indexed.

---

### Post by Franko30 on 2007-06-25
> **Howard Kaikow said:**
> 
The difficuly was that the "documentation" at te cups-pdf web site was not sufficient, at least for me.

Here's **a quick Cups-PDF How-To for Feisty**:
[INDENT]
- Install cups-pdf via Synaptic
- Configure CUPS for the PDF printer.
- Select SYSTEM > ADMINISTRATION > PRINTERS > NEW PRINTER
- Select LOCAL PRINTER
- Use detected printer: PDF PRINTER
- Select Print Driver:
- Manufacturer: Generic
- Model: Postscript Color Printer
- Name: postscript color
- Click APPLY[/INDENT]

> **Howard Kaikow said:**
> The goal is to not have to first print to a ps or pdf file. I often print, say, web pages 2-up to save paper.
Should be able to do this directly from within any app tat allows printing, such as Firefox, or gedit, or ...

Have you tried **gtklp** (or kprinter for KDE)? They bring up **print dialogues** that make this possible. For instance in Firefox: In the 'PostScript' printer properties, change 'lpr' to 'gtklp' and you're done.  You can even run it without an application and then use its 'print documents' functionality from within the GUI. Just enter gtklp in a terminal and it starts up.

If you don't get this to work, install **pdfjam**. It contains **pdfnup** which does exactly what you want: Print to PDF and convert with pdfnup - but it's commandline. **pdftk** does have other pdf-handling capabilities.

> **Howard Kaikow said:**
> I am trying to figure out what Linux can do, not via emulation. The goal is to obviate the need for a Windows license. Otherwise, why even bother with Linux.

As Brucevdk pointed out above: **pdfedit** is the way to go - it's a young program but seems to be actively developed. Get it from [http://sourceforge.net/projects/pdfedit](http://sourceforge.net/projects/pdfedit)

Cheers

Franko30

---

### Post by Howard Kaikow on 2007-06-25
> **Franko30 said:**
> Here's **a quick Cups-PDF How-To for Feisty**:
[INDENT]
- Install cups-pdf via Synaptic
- Configure CUPS for the PDF printer.
- Select SYSTEM > ADMINISTRATION > PRINTERS > NEW PRINTER
- Select LOCAL PRINTER
- Use detected printer: PDF PRINTER
- Select Print Driver:
- Manufacturer: Generic
- Model: Postscript Color Printer
- Name: postscript color
- Click APPLY[/INDENT]



Have you tried **gtklp** (or kprinter for KDE)? They bring up **print dialogues** that make this possible. For instance in Firefox: In the 'PostScript' printer properties, change 'lpr' to 'gtklp' and you're done.  You can even run it without an application and then use its 'print documents' functionality from within the GUI. Just enter gtklp in a terminal and it starts up.

If you don't get this to work, install **pdfjam**. It contains **pdfnup** which does exactly what you want: Print to PDF and convert with pdfnup - but it's commandline. **pdftk** does have other pdf-handling capabilities.



As Brucevdk pointed out above: **pdfedit** is the way to go - it's a young program but seems to be actively developed. Get it from [http://sourceforge.net/projects/pdfedit](http://sourceforge.net/projects/pdfedit)

Cheers

Franko30

THanx.

I expect to boot to linux in a few minutes and install pdfedit.

I'm trying to stay pure Gnome as long as I can.

---

### Post by Franko30 on 2007-06-25
> **Howard Kaikow said:**
> 
I'm trying to stay pure Gnome as long as I can.

I don't understand?

All the stuff I explained (except kprinter) is Gnome stuff -  even the commandline tools ;-)

Cheers and Good Night (it's 0:30 a.m.)

Franko30

---

### Post by Howard Kaikow on 2007-06-25
> **Brucevdk said:**
> ```

sudo apt-get install fakeroot alien
fakeroot alien pdfedit-0.3.1-1.i386.rpm
sudo dpkg -i pdfedit_0.3.1-2_i386.deb

```

Didn't work for me.

The first line caused about 1 dozen packages, including fakeroot and alien, to be installed.
2nd line did cause a .deb to be created.
3rd line caused a PDFedit entry to be added to the Office menu.

However, nothing happens when I click on the PDFedit entry.

Synaptic has PDFedit listed as "installed (local or obsolete)".
Is there a way to fix this?
Or, should I do a complete removal?
Then wehat?

---

### Post by Franko30 on 2007-06-26
Hi,

Sorry, I didn't pay attention to this one (as it was a long day and a lot of other problem I had to solve):

```
fakeroot alien pdfedit-0.3.1-1.i386.rpm
```

You **don't use fakeroot**, but sudo:

```
sudo alien pdfedit-0.3.1-1.i386.rpm
```

After that **use gdebi (or doubleclick the *.deb package)**.

I just installed it this way.

Cheers

Franko30

---

### Post by Howard Kaikow on 2007-06-26
> **Franko30 said:**
> Hi,

Sorry, I didn't pay attention to this one (as it was a long day and a lot of other problem I had to solve):

```
fakeroot alien pdfedit-0.3.1-1.i386.rpm
```

You **don't use fakeroot**, but sudo:

```
sudo alien pdfedit-0.3.1-1.i386.rpm
```

After that **use gdebi (or doubleclick the *.deb package)**.

I just installed it this way.

Cheers

Franko30

Thanx.

Do I first have to 

sudo apt-get --purge remove pdfedit

---

### Post by Howard Kaikow on 2007-06-26
> **Franko30 said:**
> Hi,

Sorry, I didn't pay attention to this one (as it was a long day and a lot of other problem I had to solve):

```
fakeroot alien pdfedit-0.3.1-1.i386.rpm
```

You **don't use fakeroot**, but sudo:

```
sudo alien pdfedit-0.3.1-1.i386.rpm
```

After that **use gdebi (or doubleclick the *.deb package)**.

I just installed it this way.

Cheers

Franko30

I tried using gdebi, I tried using dpkg -i, and I tried double clicking on the.deb package.

The PDFedit menu item in the Office menu still does nothing.

---

### Post by Howard Kaikow on 2007-06-26
If I type pdfedit in a terminal window, I get the message:

> pdfedit: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

Using Synaptic, I installed libqt3-mt, now pdfedit starts up!

---

