---
title: "An error occurred while loading archive"
date: 2013-10-24
forum: General Help
---

### Post by Kojak Peg on 2013-10-24
[SIZE=2][FONT=arial]I've got samsung tv and need to download and extract a file from their website to make bbc iplayer work again. The update is too large to go direct to the tv so I have to put it on a usb stick and load it on myself. I've downloaded the file but got this error message  

> An error occurred while loading the archive.

> Archive:  /home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe[/home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe or
          /home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe.zip, and cannot find /home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe.ZIP, period.


Apart from trying it in windows is there anything I can do

Thanks

Update 
on the samsung firmware webpage [/FONT][/SIZE][FONT=arial]it says [/FONT]> [FONT=arial]to view [/FONT][COLOR=#000000][FONT=arial]PDF file, you must have Adobe Acrobat reader installed on your computer[/FONT][/COLOR][SIZE=2][FONT=arial]][/FONT][/SIZE][SIZE=2][FONT=arial], which I have. It also says [/FONT][/SIZE]> [COLOR=#000000][FONT=Arial] [SIZE=2]you must have the DjVu viewer installed on your computer.[/SIZE][/FONT][/COLOR]

below is the link to the DjVu webpage
[http://djvu.org/resources/](http://djvu.org/resources/)    

Update 
I must be blind, I reread the DjVu website and saw it had a linux version So I installed it from the software centre. However I am still getting the error message > An error occurred while loading the archive.

> Archive:  /home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe
[/home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe or
          /home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe.zip, and cannot find /home/kojakpeg/Downloads/T-MST12DEUC_1113.0.exe.ZIP, period.

So I'm still at a loss as to what to do

---

### Post by Kojak Peg on 2013-10-24
bump

---

### Post by Impavidus on 2013-10-24
Judging from the extension it's not simply an archive, but a Windows executable. This could be a self-extracting archive, which can be handled by Ubuntu, but it doesn't recognise it as such. Your best bet would be using a Windows box, if you have one available.

---

