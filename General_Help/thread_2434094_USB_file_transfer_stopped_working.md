---
title: "USB file transfer stopped working"
date: 2019-12-30
forum: General Help
---

### Post by goemonburo on 2019-12-30
I am using Lubuntu 18.04LTS and have for ages been able to plug my Samsung GS6 Android into the USB and download my files.  For several months, however, it has not worked.  I can use the "image transfer" option to get photos off, but it doesn't work for videos nor for other files.  The only way I've been able to work around this is to plug in a USB flash drive with a micro port on one side and regular USB on the other, and use it like a shuttle to move files back and forth.  I'd love to figure out what is causing this -- whether it's a physical problem (cable doesn't seem to matter) or something with the OS or some patch/program I need.  All I know is that it used to work fine, but now doesn't.

More specifically, I am able to get the phone to show up in the file manager and can navigate to the DCIM/Camera folder, and I can see the image and videos (they never thumbnail, but that's a different issue).  Yet when I Ctrl-A, Ctrl-C, and then try to paste...the file manager just hangs.  (I've tried it on two different managers, PCManFM and Nautilus, same deal for either.)

The little "working" wheel just spins and spins and spins.

That's if I get that far.

Other times, if I'm lucky, the files do show up but when I try to copy them, I get an error (which I don't have on hand, will edit this the next time it appears).  I believe it's an input output error or something.  

If anyone knows what this issue is I would love assistance in fixing it.  Thank you!

---

### Post by SeijiSensei on 2019-12-31
Did you put the phone into MTP mode for USB file transfers?  It's somewhere in the Settings, but its location varies by manufacturer.

---

### Post by corktowner on 2020-02-14
This is happening to me, I can see the device but am unable to copy any files to the android tablet. Yes MTP mode is enabled. I am wondering if this is at all related to the sudo lockout for kde users?

---

### Post by wildmanne39 on 2020-02-14
Hello and welcome to the forum corktowner, please start your own thread instead of posting in someone else's you are much more likely to get the help you need that way.

Thanks

---

### Post by HermanAB on 2020-02-14
Howdy,

IMHE, the best way to debug issues is from the command line, since then you will get error messages and don't need to poke around in the dark.

So, try the good o'l cp command.

---

