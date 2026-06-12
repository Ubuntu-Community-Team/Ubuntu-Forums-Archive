---
title: "How to print/save a bundle of .png files as a single .pdf file"
date: 2007-06-29
forum: General Help
---

### Post by satimis on 2007-06-29
Hi folks,

Ubuntu Desktop 7.04
Gnome desktop


I have a bundle of .png files, about 30 files.  I need to print all of them together as a single .pdf file.  I have cup-pdf printer installed.  Instead of printing each of them as .pdf file and then adding them together as a single .pdf file afterwards, is there a simple way to do the job???  TIA


B.R.
satimis

---

### Post by barrettorama on 2007-06-29
[Gscan2pdf]("http://gscan2pdf.sourceforge.net/") may work for you.


It has an import function, and works great with scanners too.
Hope this helps.
-Ryan

---

### Post by satimis on 2007-06-29
Hi Ryan,


Tks for your advice.

> **barrettorama said:**
> [Gscan2pdf]("http://gscan2pdf.sourceforge.net/") may work for you.


It has an import function, and works great with scanners too.
Hope this helps.
-Ryan
I ran following commands w/o result.

$ sudo apt-cache showpkg gscan2pdf
W: Unable to locate package gscan2pdf

$ sudo apt-cache search gscan2pdf
No printout

$ sudo apt-cache gscan2pdf
E: Invalid operation gscan2pdf

What will be the correct syntax to search this package???  TIA


B.R.
satimis

---

### Post by noynac on 2007-06-29
You could use the pngtopdf command-line utility to convert the png files to pdf files, and then use the pdftk command-line utility to join the individual pdf files into one large pdf file. Both utilities are in the repo's--pngtopdf is part of the netpmb package. If you convert files like this on a regular basis, a shell script would expedite things.

---

### Post by satimis on 2007-06-29
Hi noynac,

Tks for your advice.

> **noynac said:**
> You could use the pngtopdf command-line utility to convert the png files to pdf files, and then use the pdftk command-line utility to join the individual pdf files into one large pdf file. Both utilities are in the repo's--pngtopdf is part of the netpmb package. If you convert files like this on a regular basis, a shell script would expedite things.
That is what I'm currently doing.  With a simple script it'll make the job easier.  I'm searching for an alternative.


B.R.
satimis

---

### Post by JeffreyRatcliffe on 2007-10-09
> **satimis said:**
> I ran following commands w/o result.

$ sudo apt-cache showpkg gscan2pdf
W: Unable to locate package gscan2pdf

$ sudo apt-cache search gscan2pdf
No printout

$ sudo apt-cache gscan2pdf
E: Invalid operation gscan2pdf

gscan2pdf is in Gutsy, but nothing before.

Just add the following line to your /etc/apt/sources.list:```
deb http://gscan2pdf.sourceforge.net/download/debian binary/
```
If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list, and lo and behold, you can install the nice shiny new version automatically.

From the command line:```
sudo apt-get update
sudo apt-get install gscan2pdf
```

If you add my key to your list of trusted keys, then you will no longer get the "not authenticated" warnings:```
gpg --keyserver www.keyserver.net --recv-keys 4DD7CC93
gpg --export --armor 4DD7CC93 | sudo apt-key add -
```

---

### Post by lngndvs on 2008-05-14
I was unable to install using this method on a Hardy Heron AMD64 machine, but was able to do so after downloading the gutsy deb of libgtkimageview0 and the deb of libgtk2-imagevew-perl, I believe, and installing them with dpkg.  I haven't tried to run the program in this version, yet.  It does run.

I want to thank you for this excellent piece of work.  I was not able to identify a --gain option, perhaps my HP allinone won't do this?  I had trouble with faint old 9-pin dot matrix documents.  I wasn't skilled enough to figure out how to sharpen the contrast.  All other documents I have thrown at it have been scanned and OCRed (tesseract) with a very high degree of accuracy---even 15 year old ink jet printing that has coffee spills etc.   Wow.  It would be very helpful to have a widget to just save selected text pages as a file, rather than having to copy and paste.  

Fantastic, and I'm sure in a day or two the installation issues will shake themselves out.

Alan

---

