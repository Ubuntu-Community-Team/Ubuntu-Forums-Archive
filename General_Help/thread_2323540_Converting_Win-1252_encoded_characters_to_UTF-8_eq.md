---
title: "Converting Win-1252 encoded characters to UTF-8 equivalents"
date: 2016-05-06
forum: General Help
---

### Post by texpat on 2016-05-06
How can I convert Windows-1252 encoded text into UTF-8 while converting characters into their UTF-8 equivalents.

I've tried [FONT=Courier New]**iconv**[/FONT] but many characters just get converted into something useless: Win-1252 encoded [FONT=Courier New]**Ü**[/FONT] becomes [FONT=Courier New]**ï¿½**[/FONT] in UTF-8, for example.

There are some suggestions over at StackExchange ([here]("http://unix.stackexchange.com/questions/23112/how-to-convert-hex-chars-to-normal-chars"), for example), but that seems complicated. At least for my level of proficiency. I'd like something on the command line ([FONT=Courier New]**sed**[/FONT]?) so I can do further processing, such as converting special characters into HTML entities, if the text has to go into the Web.

Thanks for reading. Any pointers greatly appreciated, as always.
Tx

---

### Post by peter228 on 2016-05-06
I do not have an answer but could you please give a little more information.  What is the big picture ... what is the problem that you need to solve?

It sounds a little like you are moving data off a Windows machine and for some reason wish to change from Win1252 to Unicode / utf8.    But I understand that one will not map exactly to the other.  

But what I do not get is why this is necessary since most Windows data will just work on Linux.

 So if you can give a bit more information please it will help me understand ....

---

### Post by texpat on 2016-05-06
Hi peter228,

OK, I'll elaborate a bit if that helps:

I am given plain text files that are written on a windows machine (no idea what software is used for editing, but I think that's irrelevant at this point). When I try to view them on my Linux workstation some characters are rendered as a question mark inside a box. Problem is, that all characters that are not utf-8 compliant are rendered in this way, so I have no means of telling whether its, for example, a dash, opening or closing quotation marks, umlauts or whatever - they all look the same.

That's normally not a big problem, unless its an HTML text file which is much harder to read because of all the markup. Also, for the web server to render the file correctly, it has to be utf-8 since otherwise you'll get the question-mark-in-a-box on the web page.

So I'm trying to do: 

```
iconv -f WINDOWS-1252 -t UTF-8 infile.txt > outfile.txt
```

This produces correct UTF-8. However it does not correctly convert those pesky question-mark-in-a-box characters. Instead it outputs [FONT=Courier New]**ï¿½**[/FONT] (for all of them), which I think has something to do with the Byte Order Mark (BOM) of UTF-8 which seems to be related to the encoding.

It seems like I'm going to have to look at the text files at hexadecimal level and use [FONT=Courier New]**sed**[/FONT] to change, say, \x94 into ". This I was trying to avoid, hoping something ready made exists for that problem.

---

### Post by peter228 on 2016-05-07
There are people on this forum who know a whole lot more than I do so please expect some better comments ...

However, are you sure that the reason you are not able to see the characters is because you do not have appropriate fonts installed rather than a need to convert to utf8 / unicode?

---

### Post by Impavidus on 2016-05-07
I'm puzzled. The command you tried is correct, so it should have worked. Windows-1252 doesn't use a byte order mark and for UTF-8 a byte order mark exists, but is typically only used for round trip conversions to UTF-16 or UTF-32. Both Windows-1252 and UTF-8 use the byte as the basic unit of their encoding, so don't need a byte order mark.

Most text editors, including gedit, are smart enough to handle multiple encodings. You can select the encoding when you open a file using the "open" dialogue and you can set an encoding when you save a file using the "save as" dialogue. Make sure the text editor assumes the encoding the file is really using, both for the supposedly Windows-1252 file and the UTF-8 file.

Are you absolutely positive that the file is now in Windows-1252 encoding?

---

### Post by texpat on 2016-05-09
@Impavidus: The resulting file is UTF-8 all right. Its just that some characters, such as for example the dash that sits at x96 on Win-1252 does not get converted into a dash in UTF-8. Rather it becomes ï¿½. Which is correct UTF-8, only useless for me. It does the same with other Win-1252 encoded characters, such as x82 (quotation marks) or xDC (Ü).

I have found, however, that atom (text editor) displays characters correctly if you change the encoding for that file to Win-1252, which is a start :-)

---

### Post by texpat on 2016-05-09
So, for anyone interested, I solved this by writing a small bash script and a text file with my desired conversions.

For conversion in to html, the latter looks like this:

```
htmlconversions.txt

\x83=\&lsquo;
\x84=\&ldquor;
\x96=\&ndash;
```

The script:
```
#!/bin/bash
while IFS="=" read -r hexcode htmlchar;
do
  sed -i 's/'$hexcode'/'$htmlchar'/g' $1
done <"htmlconversions.txt"
```

I realise that this is probably a terrible hackjob and anyone fluent in bash scripting is cringing at the sight of this, but for me, right now, it gets stuff done. Doesn't mean I won't listen to suggestions, though ;-)

---

