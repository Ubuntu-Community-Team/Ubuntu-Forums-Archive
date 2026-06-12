---
title: "Firefox can't display Chinese"
date: 2007-08-04
forum: General Help
---

### Post by satimis on 2007-08-04
Hi folks,

Ubuntu 7.04 server amd64

Firefox can't display Chinese characters but only codes.

/etc/X11/xorg.conf```

.....
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
...

```

Please advise how to fix the problem.  What additional fonts are needed.

TIA


B.R.
satimis

---

### Post by apetresc on 2007-08-04
Does Chinese text appear correctly in any other apps on your system? If so, the problem is probably with Firefox, not the fonts. Have you set the firefox encoding right? Go to a Chinese website, like [here]("http://www.fwolf.com/blog/post/170"), from Firefox go to "View->Character Encoding" and make sure it is set to "Unicode (UTF-8)". Then refresh the page. Does it show up properly now? If not, post back here and we'll get you some fonts :)

---

### Post by satimis on 2007-08-04
Hi Adrian

> **AdrianP said:**
> Does Chinese text appear correctly in any other apps on your system? 

I have no other Chinese text doc here for testing.

> 
Have you set the firefox encoding right? Go to a Chinese website, like [here]("http://www.fwolf.com/blog/post/170"), from Firefox go to "View->Character Encoding" and make sure it is set to "Unicode (UTF-8)". Then refresh the page. Does it show up properly now? If not, post back here and we'll get you some fonts :)
It is already set to UTF-8.  No, Only codes are displayed.


satimis

---

### Post by benx009 on 2007-08-04
install chinese fonts from synaptic and see if that fixes your problem (*xfonts-intl-chinese* is one set of fonts, but there are many others available in synaptic)

---

### Post by satimis on 2007-08-05
> **benx009 said:**
> install chinese fonts from synaptic and see if that fixes your problem (*xfonts-intl-chinese* is one set of fonts, but there are many others available in synaptic)
Hi benx009,


I'm running Fluxbox, a light-weight desktop manager, here.  So I did the installation on command line.

$ apt-cache policy xfonts-intl-chinese```

xfonts-intl-chinese:
  Installed: (none)
  Candidate: 1.2.1-6ubuntu1
  Version table:
     1.2.1-6ubuntu1 0
        500 http://hk.archive.ubuntu.com feisty/universe Packages

```

I found the packages on repo

$ sudo apt-get install xfonts-intl-chinese
Password:```

Reading package lists... Done
....
....
Setting up xfonts-intl-chinese (1.2.1-6ubuntu1) ...
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory

```

$ ls -l /usr/lib/X11/```

total 12
drwxr-xr-x 2 root root 4096 2007-07-26 11:58 config
lrwxrwxrwx 1 root root   16 2007-07-26 11:58 rgb.txt -> /etc/X11/rgb.txt
drwxr-xr-x 2 root root 4096 2007-07-26 11:58 x11perfcomp
drwxr-xr-x 2 root root 4096 2007-07-26 11:58 xsm

```


I think the installation failed.  Directories don't exist.


Rebooted the server and started Firefox.  Visiting a Chinese site failed, only codes displayed.


What shall I do?  Create the directories and try again with following steps?

$ sudo mkdir -R /usr/lib/X11/fonts/misc
$ sudo chmod 750 -R /usr/lib/X11/fonts/misc

Re-run
$ sudo apt-get install xfonts-intl-chinese

On /etc/X11/xorg.conf
add following line under "Section "Files"```

FontPath        "/usr/lib/X11/fonts/misc"

```


Or direct installing xfonts-intl-chinese on```

/usr/share/fonts/X11/misc

```
???

TIA


$ ls /usr/share/fonts/X11/misc/```

10x20-ISO8859-10.pcf.gz  6x9-ISO8859-1.pcf.gz         9x15B-ISO8859-9.pcf.gz
10x20-ISO8859-11.pcf.gz  6x9-ISO8859-2.pcf.gz         9x15B.pcf.gz
10x20-ISO8859-13.pcf.gz  6x9-ISO8859-3.pcf.gz         9x15-ISO8859-10.pcf.gz
10x20-ISO8859-14.pcf.gz  6x9-ISO8859-4.pcf.gz         9x15-ISO8859-11.pcf.gz
10x20-ISO8859-15.pcf.gz  6x9-ISO8859-5.pcf.gz         9x15-ISO8859-13.pcf.gz
10x20-ISO8859-16.pcf.gz  6x9-ISO8859-7.pcf.gz         9x15-ISO8859-14.pcf.gz
10x20-ISO8859-1.pcf.gz   6x9-ISO8859-8.pcf.gz         9x15-ISO8859-15.pcf.gz
10x20-ISO8859-2.pcf.gz   6x9-ISO8859-9.pcf.gz         9x15-ISO8859-16.pcf.gz
....
....
6x13-ISO8859-3.pcf.gz    8x13O-ISO8859-15.pcf.gz      decsess.pcf.gz
6x13-ISO8859-4.pcf.gz    8x13O-ISO8859-16.pcf.gz      encodings.dir
6x13-ISO8859-5.pcf.gz    8x13O-ISO8859-1.pcf.gz       fonts.alias
6x13-ISO8859-7.pcf.gz    8x13O-ISO8859-2.pcf.gz       fonts.dir
6x13-ISO8859-8.pcf.gz    8x13O-ISO8859-3.pcf.gz       gb16fs.pcf.gz
6x13-ISO8859-9.pcf.gz    8x13O-ISO8859-4.pcf.gz       gb16st.pcf.gz
...

```


B.R.
satimis

---

