---
title: "[SOLVED] read hellenic (greek) files in ISO-8859-7"
date: 2008-04-07
forum: General Help
---

### Post by Claus7 on 2008-04-07
Hello,

I have a text file file_name.txt which is written in encoding greek-ISO-8859-7. I say so because when I attach it and view it via opera, I can see it with the following options under greek:

[LIST]
[*]ISO-8859-7
[*]Windows-1253
[/LIST]

I try to open this file with gedit and geany, yet I cannot view the characters correctly (in their place are characters as these : ËÅÎÉÊÏ ÏÑÙÍ ÐËÇÑÏÖÏÑÉÊÇÓ). With geany I can change the encoding, yet to no avail. The document remains unchanged. Is there a way to view files written in the aforementioned encoding, which even being old, is still used? I installed also sfonts-int-european via synaptic, yet to no avail. As to no suprise the unidesc command doesn't recognise the encoding of this file because it is not utf-8.

Has anyone any idea on how in linux and with which program ISO-8859-7 files will be viewed?

Regards!

---

### Post by kostkon on 2008-04-07
You could try opening the file in *gedit* and then re-saving it as *UTF-8*.

---

### Post by kostkon on 2008-04-07
You can also use this *Nautilus* script if you like. Make the attached file executable (delete the .txt extension) and place it in:
```
~/.gnome2/nautilus-scripts
```
then right click on any file you want to convert, and select *Scripts -> iso8859-7-to-utf8*
A new copy of the file that is converted to *UTF-8* will be created. 

The script is absolutely safe. But, here is its code for you to see:
```
#!/bin/bash
#
# Character Encoding Conversion Script for Nautilus
#
# A simple nautilus script to convert from iso-8859-7
# character encoding to utf-8.

from="iso-8859-7"	# Replace $1 with the input encoding ex. "iso-8859-7"
to="utf-8"			# Replace $2 with the output encoding ex. "utf-8"

thefile="$*"
if [ $# -gt 0 ];then
iconv -f $from -t $to "${thefile}" > "${thefile}.utf8"
fi
exit 0 
```

But check the file's contents before using it to be sure ;)

---

### Post by Claus7 on 2008-04-07
Hello,

first of all thank you for your script and replies. 

As far as the first one is concerned, I have to say that the format of the text file (the characters if you prefer) are in ISO-8859-7. That means that when I save the file as utf-8, I see the unreadable characters as above. Even if I save it as ISO-8859-7 I cannot see the characters as I should. No matter what I do the characters remain unreadable, in contrast to opera, where if I choose the ISO-8859-7, I can see them properly. So I think that I should change the encoding before saving. 

As far as the second one is concerned I have to tell you the following:
very nice the idea to convert "on the fly" the text file. I do not think though that I have to convert it to utf-8, yet the other way around. As a result I changed it  for example like that :

```
#!/bin/bash
#
# Character Encoding Conversion Script for Nautilus
#
# A simple nautilus script to convert from utf-8
# character encoding to iso-8859-7

from="utf-8"
to="iso-8859-7"	
			
thefile="$*"
if [ $# -gt 0 ];then
iconv -f $from -t $to "${thefile}" > "${thefile}.iso-8859-7"
fi
exit 0
```

yet to no avail...

I will try to see what I can do with the script you provided.
Also very nice of you to show the code.
Regards!

---

### Post by Claus7 on 2008-04-08
Hello,

the command I ececuted in order to be able to see the file in question is the following :
```
 iconv -f WINDOWS-1253 -t UTF-8 ./README.TXT > ./newfile.txt
```
or
```
 iconv -f ISO_8859-7:2003 -t UTF-8 ./README.TXT > ./newfile1.txt
```

that means that I converted the file from the ISO encoding to UTF-8 so as to be able to see it. My input file was the README.txt and the output the newfile(1).txt . The *:2003* after 7 is not necessary.
**Indeed** I had to make the conversion **from** ISO **to** UTF and not the other way around.

With 
```
man iconv
```
I found out that if I type
```
iconv -l
```

I will see a list which will contain all the coded character sets that are known. As a result the conversion of a file becomes very trivial.

EDIT: In order for someone to find the unicode of the initial file then someone has to type the following command :
```
file name_of_the_file
```


Regards!

---

