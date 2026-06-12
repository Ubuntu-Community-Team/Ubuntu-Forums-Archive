---
title: "Cant Open a Zip"
date: 2014-10-10
forum: General Help
---

### Post by jooge on 2014-10-10
Now, I know how to do it, I aint THAT new but I seem to be having an issue with lots of zips as of late. Opening 7zip, rar and other archieve formats is not an issue just zips. When I try to open one more times than not I get this error:


7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Error: /home/xxxxx/Documents/UYBC #10.zip: Can not open file as archive

Errors: 1

What does this mean exactly and how can I correct it? Also is there any other alternative ways of opening an archive?

---

### Post by sudodus on 2014-10-10
Please upload a fairly small zip file, that you cannot open, give us a link to it, and let us try to open it!

Then we'll have a chance to give relevant advice :-)

---

### Post by nerdtron on 2014-10-10
Is this really a zip file? or just a renamed file with changed extension?
ZIP file, have you tired it in windows? Does it have a password?
Have you tried opening it on the command line using the command "unzip /path/to/filename.zip"?
Are you sure you have the permissions to read the file?

---

### Post by sudodus on 2014-10-10
Is there a **#** character in the file name? It might be interpreted as the beginning of a comment somewhere inside the tool to read the archive, so that the file name is truncated (and not found).

---

### Post by jamesisin on 2014-10-10
I wrote this article some time ago.  It may be useful to you today.

[http://jamesisin.com/a_high-tech_blech/index.php/2008/11/the-quirks-of-7zip-under-ubuntu/](http://jamesisin.com/a_high-tech_blech/index.php/2008/11/the-quirks-of-7zip-under-ubuntu/)

---

### Post by andrew.46 on 2014-10-10
The *space* could be more of a problem than the **[COLOR="#FF0000"]#[/COLOR]** mark. Correct syntax (using infozip) would be something like:

```

andrew@ilium~/test$ **[COLOR="#FF0000"]unzip test\ #.zip [/COLOR]**
Archive:  test #.zip
  inflating: IMAG0232.jpg            
  inflating: IMAG0233.jpg            
  inflating: IMAG0234.jpg            
  inflating: IMAG0235.jpg            
  inflating: IMAG0236.jpg            
  inflating: IMAG0237.jpg            
  inflating: IMAG0238.jpg            
  inflating: IMAG0243.jpg            
  inflating: IMAG0244.jpg            
  inflating: IMAG0245.jpg            
andrew@ilium~/test$ 

```

or an alternative:

```

andrew@ilium~/test$ **[COLOR="#FF0000"]unzip 'test #.zip' [/COLOR]**
Archive:  test #.zip
  inflating: IMAG0232.jpg            
  inflating: IMAG0233.jpg            
  inflating: IMAG0234.jpg            
  inflating: IMAG0235.jpg            
  inflating: IMAG0236.jpg            
  inflating: IMAG0237.jpg            
  inflating: IMAG0238.jpg            
  inflating: IMAG0243.jpg            
  inflating: IMAG0244.jpg            
  inflating: IMAG0245.jpg            
andrew@ilium~/test$ 

```

Another example of spaces in filenames being the natural enemy of a linux system :)

---

