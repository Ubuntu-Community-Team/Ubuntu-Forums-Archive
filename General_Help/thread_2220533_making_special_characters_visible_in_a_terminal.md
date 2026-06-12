---
title: "making special characters visible in a terminal"
date: 2014-04-28
forum: General Help
---

### Post by George Heine on 2014-04-28
Trying to use a text editor (using vim 7.3, but could be convinced to try something else) to extract some text from a file and put it on a website.
I don't want the whole file, just a few sentences of text.

The header of the file contains the following:

```
<html xmlns="http://www.w3.org/1999/xhtml"><!--This file was converted to xhtml by OpenOffice.org - see http://xml.openoffice.org/odf2xhtml for more info.-->

```

(Actually, I believe it was converted from an MsWord file with LibreOffice.  I did try going to  xml.openoffice.org/odf2xtml but got a "not found" error.)

Although most of the text was converted cleanly, there are a few characters that give me trouble.  Most common is that some, but not all
spaces seem to have been converted to the hex sequence 0xA0 (no-break space), 0xC2 (latin capital A with circumflex).  This sequence just appears as a space on my terminal, which makes it hard to edit with a text editor.   

How can I make odd sequences like this visible on my terminal, so they can be edited with a text editor ?

thanks for any suggestions -

---

### Post by Impavidus on 2014-04-28
Now I'm wondering what character encoding this is. Ubuntu (including all text editors, the terminal and the system itself) by default use Unicode in UTF-8 encoding, but in that encoding the sequence 0xa0 0xc2 is no complete character. I had expected that the terminal would show a question mark for the illegal bytes, but maybe it just ignores them.

Maybe you can set your terminal and/or text editor to some legacy 8-bit encoding, where the sequence 0xa0 0xc2 indeed means <nbsp>Â.

---

### Post by George Heine on 2014-04-29
Haven't yet figured out how to set the terminal to a legacy 8-bit  encoding, but as a workaround, put together a python script that replaces all  bytes>0xFF with a "MARKER" character:
```
with open(filename, "r") as f:
  while True:
    oldstr=f.readline();
    if oldstr=='': break;
    newstr="";
    for char in oldstr:
       if (ord(char) & 0x80): newstr=newstr+MARKER;
       else: newstr=newstr+char;
    print newstr;

```

Also, I have found that, if the .docx file is available, exporting it to PDF and then running pdftotext on the result substantially reduces (but does not eliminate) the number of odd characters.

---

### Post by steeldriver on 2014-04-29
Have you tried iconv?

---

### Post by George Heine on 2014-05-01
Steeldriver, thank you for the hint. Had heard of iconv before but never used it. 
First I tried 

```
iconv -f ASCII -c [file]
```

which deleted the non-ascii characters in the file.

Then tried

```
iconv -f WINDOWS-1251 -t ASCII//TRANSLIT [file] 
```

which replaced the non-ascii characters with something that was easy to spot (mostly  "?").
This looks like a useful tool; I do need to work with UTF-8 characters from time to time.

Question:  where do I find documentation on the different character encodings ?

---

### Post by Impavidus on 2014-05-02
You can find a lot of encoding related stuff on Wikipedia. That's where I read most of it.

The nice thing is that almost everything on Linux is in UTF-8, which is backward compatible with ASCII: any ASCII text is valid UTF-8. The exceptions are some font related stuff in pdf, PostScript and TeX, but as long as you don't create your own fonts you rarely have to care about that. Windows unfortunately is less consistent, which can cause issues when reading non-ASCII text from a Windows environment. And there is of course the line end convention.

---

### Post by George Heine on 2014-05-07
> You can find a lot of encoding related stuff on Wikipedia. That's where I read most of it.

Thanks, Impavidus.  It looks like there is extensive documentation at
[https://en.wikipedia.org/wiki/Character_encoding]("http://en.wikipedia.org/wiki/Character_encoding").

The page for Windows-1252 lists the "smart quotes" at 0x82 and 0x84 as being noncompliant with the ANSI standard, and indeed, those
two have given me problems.  Still don't quite understand why multiple spaces get represented as 0xA0,0xC2.  But, in any case, my original 
problem (finding an easy way to flag non-ASCII characters in a text) appears to be solved.  Marked this thread as "solved".

---

### Post by steeldriver on 2014-05-07
I think the 0xA0,0xC2 come about because something in your chain of document conversions fails to recognize the 2-byte sequence 0xC20xA0 as the UTF-8 encoding of U+00A0 (a non-breaking space) - see [http://stackoverflow.com/a/4515394](http://stackoverflow.com/a/4515394) for example

---

