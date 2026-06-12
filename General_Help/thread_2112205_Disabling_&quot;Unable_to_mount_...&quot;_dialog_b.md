---
title: "Disabling &quot;Unable to mount ...&quot; dialog boxes"
date: 2013-02-04
forum: General Help
---

### Post by daviesl5000 on 2013-02-04
Hi,

I'm a long time user of Ubuntu, however this is my first post so please forgive me if this question is posted in the wrong place ;)

I have an application using the standard 12.04 desktop (gnome), which relies on the automounting of usbpens. The automount works fine, however when operators pulls out the usbpen it produces an annoying "Unable to mount blah blah" dialog box. Is there any setting where I can disable this message box rather than unmounting the pen(s)?

Cheers,

Lee

---

### Post by mcduck on 2013-02-04
You really should be ejecting the drives properly, especially if you write any data to them. Otherwise you'll risk loosing the data and/or corrupting the filesystem on the device. And it really isn't that big job to do, two mouseclicks...

---

### Post by daviesl5000 on 2013-02-04
My fault for not explaining my application (I wanted to avoid the details...but as they say the devil is in the details). 

I've written an application which tests some "hardware". Part of the test is to ensure all the USB sockets on the "hardware" are working. To do this I have 4 USB pens connected with a particular file on each pen. During the the test the supply is switched on **briefly**  (for some initial checks) and off before being restored again for the remainder of the test. 

This breif initial power on is sufficient in duration for Ubuntu to commence the automount but not sufficient to complete the automount. This creates a error dialog box which appears in front of my test app. :(

If I could remove the dialog error message or easily and quickly switch the automount feature on or off, this would solve my problem. 

Cheers,

Lee

---

### Post by mcduck on 2013-02-04
Ah. In that case disabling automounting would probably be the best way. You can do that quite easily through Gsettings, either by the command-line tool or by usinbg dconf-editor.

IF you want to do it from a script, or using a launcher icon etc, thjese commands should do the job:

disable automount:
```
gsettings set org.gnome.desktop.media-handling automount false
```
...and enable it again:
```
gsettings set org.gnome.desktop.media-handling automount true
```

---

