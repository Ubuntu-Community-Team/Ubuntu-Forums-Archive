---
title: "Help: Open Office Support for Microsoft Word 2007"
date: 2007-10-28
forum: General Help
---

### Post by xhuga2 on 2007-10-28
Hello I downloaded the Open XML odf-converter-1.0.0-5.i586.rpm and odfconverter-1.0.0-2.oxt. I have managed to install it and I am now able to read all my work previously in .docx. However this my problem is: I can't save my work into Microsoft 2007 format. Can anyone help me? Thanks. I used these 3 sites since I have been using linux for two days now. I am a confused wreck. 

[http://download.novell.com/SummaryFree.jsp?buildid=ESrjfdE4U58%7E](http://download.novell.com/SummaryFree.jsp?buildid=ESrjfdE4U58%7E)
p://geekhacks.blogspot.com/2007/05/working-with-word-2007-documentsdocx-in.html
[http://www.sigmundvoid.com/?p=81](http://www.sigmundvoid.com/?p=81)

I am using Gutsy Gibbon

 Thank you.

---

### Post by Cochise on 2007-10-28
the converter only allows you to read .docx files i think you&#314;l have to save in word 97-2000 format .doc

---

### Post by edoviak on 2007-10-28
If you've installed the converter properly, you should be able to save into DOCX from OpenOffice. If that doesn't work, you can convert it from ODF to DOCX at the command line. A summary of the commands can be found at: [**the Xandros OOXML page**]("http://support.xandros.com/downloads/Openxml/")

The easiest way to do it from the command line is to make a hard link to the converter. Open up a console and become root, then insert the link in your **/usr/bin** directory:
[B]
$ su
Password:
# cd /usr/lib/openoffice/program
# ln OdfConverter /usr/bin/OdfConverter
# exit
$ exit
[/B]
Then you should be able to convert from the command line. For example, to convert from DOCX to ODT, you would type:
[B]
$ OdfConverter /I file_from_Bill-Gates.docx
[/B]
After mindlessly spewing the word "progress" for minutes on end, the conversion will finally stop and provide you with a friendly ODT file: **file_from_Bill-Gates.odt** 

To convert from ODT to DOCX, you would type:
[B]
$ OdfConverter /I file_for_Bill-Gates.odt /O file_for_Bill-Gates.docx /ODT2DOCX
[/B]
The same summary of the command options that's on the Xandros page, can be found by typing:
[B]
$ OdfConverter -h
[/B]
...

But why would you want to convert to DOCX? [**Stand up for Open Source and take REVENGE on the people who send you that crap**]("http://forums.debian.net/viewtopic.php?t=20050")

- Eric

---

