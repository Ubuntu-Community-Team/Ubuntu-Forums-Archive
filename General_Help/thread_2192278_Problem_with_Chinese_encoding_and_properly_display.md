---
title: "Problem with Chinese encoding and properly displaying Chinese Characters"
date: 2013-12-07
forum: General Help
---

### Post by learnlinux2 on 2013-12-07
I am having many problems reading Chinese characters not saved in the UTF-8 format. After doing the "file" command, I realized that nearly all of the files that I have problems reading in Ubuntu are ISO-8859 English text, with CRLF, NEL line terminators. Though, I can type in Chinese on my computer properly, and generally have no problem reading Chinese characters on websites.

One thing I am trying to do is watch movies with double subtitles. The problem is that often the Chinese characters look like nonsense. The characters display properly in the Chinese version of Windows XP, but do not display properly in Ubuntu.

One example is this: 
On a computer with the Chinese version of Windows XP, the file correctly displays as:
&#65279;{102611}{102677}Just like now.|&#23601;&#20687;&#29616;&#22312;&#19968;&#26679; 
{102683}{102753}Perfect.|&#24456;&#22909;

But in Ubuntu, Linux Mint, and various Debian variants it displays as:
{102611}{102677}Just like now.|ŸÍÏñÏÖÔÚÒ»Ñù 
{102683}{102753}Perfect.|ºÜºÃ

I am using the Ubuntu 12.04 base, 32 bit edition. I have tried to install every possible Chinese font I could find, but to no avail. Also, I tried changing my locale to charset="utf-8", but that didn't change anything. I have also tried converting the encoding for the various files to UTF-8, but could never get a correct solution.

Any and all help is appreciated.
Thanks!!!!
:guitar:

---

### Post by Impavidus on 2013-12-07
To convert various legacy encodings to utf-8 (utf-8 is the future and has arrived years ago) one can use **iconv**. In the terminal:```
iconv -f<your chinese encoding> -t UTF-8 -o <output file name> <input file name>
```I don't know enough about chinese to see which is your chinese encoding, but to list all encodings iconv knows about, use```
iconv -l
```
When typing you use utf-8, most websites use utf-8 too.

---

