---
title: "[SOLVED] keyjnote won't run"
date: 2007-12-31
forum: General Help
---

### Post by mdbarton on 2007-12-31
Hi

I've just installed keyjnote from the repositories and have tried it with various PDF files.  I get the following error messages:
```
Welcome to KeyJnote version 0.10.0
Detected screen size: 1280x800 pixels
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x58
  Serial number of failed request:  127
  Current serial number in output stream:  129

```

and if I use the -f parameter (don't run in fullscreen mode) I get:
```
Welcome to KeyJnote version 0.10.0
Using GL_ARB_texture_rectangle.
Traceback (most recent call last):
  File "/usr/bin/keyjnote", line 3233, in <module>
    run_main()
  File "/usr/bin/keyjnote", line 3208, in run_main
    main()
  File "/usr/bin/keyjnote", line 2810, in main
    glBindTexture(TextureTarget, T)
ctypes.ArgumentError: argument 2: <type 'exceptions.TypeError'>: wrong type

```

I am running 64bit Ubuntu 7.10, with an intel graphics chip.  Any ideas?  I'd really like to go beyond doing powerpoint/impress presentations!

Cheers

Matt

---

### Post by mdbarton on 2008-01-03
I just tried it on a 32bit installation and it won't show the slides - just lots of 'KeyJnotes' on a black screen:
```

Welcome to KeyJnote version 0.10.0
Detected screen size: 1024x768 pixels
Using GL_ARB_texture_rectangle.
Error: pdftoppm produced an unreadable file (page 1)
Error: pdftoppm produced an unreadable file (page 2)
Error: pdftoppm produced an unreadable file (page 3)
Error: pdftoppm produced an unreadable file (page 4)
Error: pdftoppm produced an unreadable file (page 5)
Error: pdftoppm produced an unreadable file (page 6)
Background rendering finished, used 13.5 MiB of disk space.
Total presentation time: 0:27.

```

Something wrong with the PDFs exported from Impress?

---

### Post by mdbarton on 2008-01-05
I have installed all the dependencies as per the keyjnote documentation at [http://keyjnote.sourceforge.net/](http://keyjnote.sourceforge.net/) :
```
apt-get install python python-opengl python-pygame python-imaging xpdf-reader gs pdftk
```
and downloaded version 0.10.1a, copying the keyjnote.py file to /usr/share/keyjnote/

I can now run keyjnote using the -f argument and then press 'f' to go to fullscreen, however this is in 1024x768.  keyjnote does not like my widescreen resolution.

Hope the above is helpful to anyone else struggling with this...

---

### Post by oeolartep on 2008-01-07
Both errors was reported as bugs, 

[https://bugs.edge.launchpad.net/ubuntu/+source/keyjnote/+bug/148070](https://bugs.edge.launchpad.net/ubuntu/+source/keyjnote/+bug/148070)
[https://bugs.edge.launchpad.net/ubuntu/+source/keyjnote/+bug/152866](https://bugs.edge.launchpad.net/ubuntu/+source/keyjnote/+bug/152866)

In my case , I have downloaded the 0.10.1a version from internet. The bad detection of screen resolution persists, this problem can be asociated with this line

def GetScreenSize(): return pygame.display.list_modes()[0]

in file keyjnote.py, but I don't know how to fix this.

You can make it work in two ways,

1) Change the lines 

UseAutoScreenSize = True
ScreenWidth = 1024
ScreenHeight = 768

by 

UseAutoScreenSize = False
ScreenWidth = <yourscreenwidth>
ScreenHeight = <yourscreenheight>

in file keyjnote.py.

2) Use -g (geometry) flag

keyjnote -g  <WxH> file.pdf

---

### Post by Birk on 2008-01-17
I had the same problem, that pdf's won't show and only got a black screen with the keyjnote logo.
The first link in the post one above helped me solve this.
Thanks

PS: I am a newby with this stuff so it still took a while for me to figure out what to do.
Here is what I did at the end to get it running:
1. download (save link as) [http://launchpadlibrarian.net/10294904/keyjnote_v10.0.patch](http://launchpadlibrarian.net/10294904/keyjnote_v10.0.patch)
and save as keyjnote_v10.0.patch in your home directory.
2. go to the keyjnote folder:
cd /usr/share/keyjnote/
3. patch:
sudo patch --backup keyjnote.py ~/keyjnote_v10.0.patch


Thanks again for the help.

---

### Post by Leo the Lion on 2008-04-07
Thanks Birk!! I was having the same problem but you solved it.

Now I have another question. I prepared a presentation using OO Impress, converted to pdf. When I use keyjnote, the transitions are random and I would like to specify a single transition. Do you know how to do this?

Thanks.

---

### Post by Leo the Lion on 2008-04-08
bump

---

### Post by jgeezy on 2008-04-21
not sure if you are already using it but download keyjnoteGUI its an amazing front end for the commands of keyjnote....there is a whole section for it!

---

