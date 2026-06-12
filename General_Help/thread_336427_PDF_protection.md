---
title: "PDF protection"
date: 2007-01-11
forum: General Help
---

### Post by Elena678 on 2007-01-11
Hi averyboddy, is there somboddy who now how i can protect my pdf, i meen, so that other people can not coppy somthing that's in my pdf file. i have made the file with openoffice. there is a option to make a pdf. but is there a optoin to make it coppyprotected :)

is it also possible to put a licht text or picture behind it (don't know the english name)

thanks for your help

greetings

Elena

---

### Post by david_2001 on 2007-01-11
You could try pdftk (just sudo apt-get install pdftk if you have the Universe repository enabled).  It's a command line tool but, for example, to convert a file called test.pdf to one called controlled.pdf which will only allow printing, seting the password to "zincplate", is as easy as:

$ pdftk test.pdf output controlled.pdf owner_pw zincplate allow printing

pdftk will do watermarking, which is what I think is what you also want to do, but I've never had to use that option.

HTH

---

### Post by Elena678 on 2007-01-11
thanks, nice for the info, i did it all, it create an other document, but i can still just coppy my text out of my pdf, the watermarking tool, i could also not find :S

thanks

---

### Post by david_2001 on 2007-01-14
Aha, it's naughty Linux application programmers not honouring pdf document security ;-).  If you open the protected pdf in Acrobat Reader - the application that most of the world will be using - then you'll find that the restrictions are in place.

To be honest, even if you only have Acrobat Reader then it's still possible to get the text out of a protected pdf without any special tools provided that the document allows printing.  All you need is a postscript printer driver set up to print to file and the patience to extract the document text from the postscript output.  I know because that's how I've done it in the past!

---

### Post by Elena678 on 2007-01-16
yea, okei, but when you have one protection, it's always a bit more difficult :)

yea, maybe it's also stupid to protect files, but some times ...

greetings

---

