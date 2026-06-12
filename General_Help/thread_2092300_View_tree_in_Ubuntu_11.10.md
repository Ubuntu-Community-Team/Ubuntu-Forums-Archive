---
title: "View tree in Ubuntu 11.10"
date: 2012-12-07
forum: General Help
---

### Post by MocroNL on 2012-12-07
Hello folks,

I'am using ubuntu 11.10(CLI) and I need to get an overview of the directories in my system.

Example /usr: rights = 775 
              owner = root

But I need it for every directory/file and doing this one by one will take me ages.

Is there anything I can download from apt-get to simplify this process??

Many thanks.

---

### Post by oldos2er on 2012-12-07
I ran ```
sudo -i

cd /

ll -R > text
```
This took a couple minutes or so to run, and the final 'text' file was 81MB.

---

### Post by Habitual on 2012-12-07
> **MocroNL said:**
> Hello folks,

I'am using ubuntu 11.10(CLI) and I need to get an overview of the directories in my system.

```
tree /usr
```Perms and user:
```
# find `pwd` /usr -perm 755 -type d
# find `pwd` /usr -user root
```I believe you mis-typed the 775 and that should be 755 for directories (hence the "-type d")

Combining the two is outside my pay grade. :)

---

### Post by MocroNL on 2012-12-10
Thank you for the reply!

@oldos2er
I get too many unnecessary information with that command. The information I need are:

Example 
/etc (rights)(owner)(group)

But I need this information from EVERY directory in my linux system.

@Habitual
When I use the tree command I get a strange output. It looks like this:
 âââ www
        âââ html
        âÂ*Â* âââ dist
        âÂ*Â* âââ etc
        âÂ*Â* âââ images
        âÂ*Â* âÂ*Â* âââ dropline
        âÂ*Â* âÂ*Â* âââ nuovo
        âÂ*Â* âÂ*Â* âââ nuvola_1
        âÂ*Â* âÂ*Â* âââ nuvola_2
        âÂ*Â* âÂ*Â* âââ webset
        âÂ*Â* âââ include
        âÂ*Â* âÂ*Â* âââ classes
        âÂ*Â* âÂ*Â* âââ css
        âÂ*Â* âÂ*Â* âââ defines
        âÂ*Â* âÂ*Â* âââ functions
        âÂ*Â* âÂ*Â* âÂ*Â* âââ redbean
        âÂ*Â* âÂ*Â* âââ js
        âÂ*Â* âÂ*Â* âââ xml
        âÂ*Â* âÂ*Â*     âââ language
        âÂ*Â* âÂ*Â*         âââ DE
        âÂ*Â* âÂ*Â*         âââ EN
???

Is it even possible to get an output from ubuntu that gives you a list of ALL directories inside the machine + rights,user and group???? 


Many thanks.

---

### Post by steeldriver on 2012-12-10
You could do something like

```
 sudo find / -type d -exec stat -c '%N %U %a %G' '{}' \;
```Have a look at the stat man page and decide exactly which fields you want (%U, %a etc.)

```
man stat
```You will need to do it with sudo to list some dirs

---

### Post by MocroNL on 2012-12-10
Heey.

Now I'am getting close! Thank you steeldriver.

Just need to figure it out how to see output from directories only.

Greets

---

### Post by steeldriver on 2012-12-10
The '-type d' should limit the find to directories only

Or do you mean you want to limit it to certain directory levels? if so you can use 'maxdepth'

 ```
sudo find / -type d **-maxdepth 3** -exec stat -c '%N %U %a %G' '{}' \;

```

---

### Post by MocroNL on 2012-12-10
Yes true. Did not pay attention.....:P

Thanks again! And is it possible to put this output into a file? 

Greets.

---

### Post by steeldriver on 2012-12-10
yes of course - just use the shell redirect >

```
 sudo find / -type d -exec stat -c '%N %U %a %G' '{}' \; > whatever.txt
```

---

### Post by MocroNL on 2012-12-10
Thank you steeldriver 

You have made my day :)

---

### Post by Wim Sturkenboom on 2012-12-10
```

tree -pug /

```
gives you want you want. You seem to have a characterset problem. Tree output looks like this (from my home directory)

```

.
&#9500;&#9472;&#9472; [drwxr-xr-x wim      wim     ]  backup
&#9500;&#9472;&#9472; [drwxr-xr-x wim      wim     ]  bin
&#9500;&#9472;&#9472; [drwxr-xr-x wim      wim     ]  Desktop
&#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  df.afterinstall.txt
&#9500;&#9472;&#9472; [drwxr-xr-x wim      wim     ]  documents
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  somenote.note
&#9474;** &#9492;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  somenote.txt
&#9500;&#9472;&#9472; [drwxr-xr-x wim      wim     ]  downloads
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  e2175_p5ld2.pdf
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  foxconn_H61MXL Series-Manual-En-V1.0.pdf.zip
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  H61MXL Series-Manual-En-V1.0.pdf
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  lens_roadmap.pdf
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  mysql.server.txt
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  S19mysql.txt
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  skype-debian_2.2.0.25-1_i386.deb
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  skype_install.txt
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  ts-7260-datasheet.pdf
&#9474;** &#9492;&#9472;&#9472; [-rwxr-xr-x wim      wim     ]  unetbootin-linux-555
...
...
&#9500;&#9472;&#9472; [drwxr-xr-x wim      wim     ]  images
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  2011-09-28--1317224351_1024x600_scrot.png
&#9474;** &#9500;&#9472;&#9472; [-rwxr-xr-x wim      wim     ]  IMGP8946.JPG
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  IMGP8946.resize.JPG
&#9474;** &#9500;&#9472;&#9472; [-rwxr-xr-x wim      wim     ]  IMGP8955.JPG
&#9474;** &#9500;&#9472;&#9472; [-rw-r--r-- wim      wim     ]  IMGP8955.resized.JPG
&#9474;** &#9500;&#9472;&#9472; [-rwxr-xr-x wim      wim     ]  IMGP8955.txt
&#9474;** &#9500;&#9472;&#9472; [drwxr-xr-x wim      wim     ]  wallpapers
&#9474;** &#9474;** &#9492;&#9472;&#9472; [lrwxrwxrwx wim      wim     ]  shared -> /usr/share/backgrounds
&#9474;** &#9492;&#9472;&#9472; [drwxr-xr-x wim      wim     ]  Webcam

```

To circumvent your 'problem',you can try _tree -pugi_ or _tree -pugif_

---

