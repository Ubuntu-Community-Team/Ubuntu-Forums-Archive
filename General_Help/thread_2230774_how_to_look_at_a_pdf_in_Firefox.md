---
title: "how to look at a pdf in Firefox?"
date: 2014-06-21
forum: General Help
---

### Post by alfred4 on 2014-06-21
Hello everybody :-)

Please, how could you see the following .pdf which should be downloaded through Firefox?
[http://eu1.qnap.com/Storage/Manual/QTS_user_manual_Home_ger_4.1.pdf](http://eu1.qnap.com/Storage/Manual/QTS_user_manual_Home_ger_4.1.pdf)

I can download this .pdf through Windows but not through Kubuntu 12.04.

---

### Post by sudodus on 2014-06-21
It works for me (in Firefox) when I click on the link. What happens when you click on the link?

---

### Post by lisati on 2014-06-21
The link works for me by opening and displaying the file a new tab in Firefox. The new tab has a "save to disk" button.

---

### Post by alfred4 on 2014-06-21
Thank you Sudodus and Lisati.
I only have a black window with the typical adobe tools on the top.

---

### Post by lisati on 2014-06-21
There are the equivalent of 345 pages to be retrieved: it might take a little while for something to display, particularly if you have a slow connection.

---

### Post by sudodus on 2014-06-21
An alternative is to download the file with wget and read it locally:

```
wget "http://eu1.qnap.com/Storage/Manual/QTS_user_manual_Home_ger_4.1.pdf"
```

---

### Post by alfred4 on 2014-06-21
Thanks lisati, but it cannot last more than one hour.
Thanks sudodus, but where is it saved?

---

### Post by lisati on 2014-06-21
An alternative, which is not necessarily any better, is to right click on the link and use "Save link as...." which will default to your Downloads folder.

---

### Post by Dennis N on 2014-06-21
Your file is only 5.5 MB, and takes only a few seconds to download. Firefox saves it to your Downloads directory by default. You can right-click on a link to a PDF and use the "save link as ..." option to save it to disk first before opening and viewing (in any PDF viewer), or left-click to open and view it in Firefox first before saving.

---

### Post by sudodus on 2014-06-21
> **alfred4 said:**
> Thanks sudodus, but where is it saved?

When you run wget, the file will be saved in the directory where you run the command.

So if you cd to Downloads it will be saved there.

```
cd ~/Downloads
wget "http://eu1.qnap.com/Storage/Manual/QTS_user_manual_Home_ger_4.1.pdf"
ls -l "http://eu1.qnap.com/Storage/Manual/QTS_user_manual_Home_ger_4.1.pdf"
```

---

### Post by alfred4 on 2014-06-21
Thank you very much lisati,
Thank you very much sudodus and
Thank you very much Dennis N

---

### Post by SeijiSensei on 2014-06-21
> **alfred4 said:**
> Thank you Sudodus and Lisati.
I only have a black window with the typical adobe tools on the top.

That tells me you have Adobe Acrobat installed.  I'd dump that right away.  On my Kubuntu 14.04 machine, opening a PDF in Firefox launches Okular, the default KDE PDF reader.  You can switch to that by going to Edit > Preferences > Applications and choosing "Use okular" from the drop-down menu next to "Portable Document Format".

Acrobat is known to have [many security problems]("http://www.cvedetails.com/vulnerability-list/vendor_id-53/product_id-497/cvssscoremin-4/cvssscoremax-4.99/Adobe-Acrobat-Reader.html"). Just this week I saw a phishing email with an infected PDF attachment that was probably targeting Acrobat vulnerabilities.

---

