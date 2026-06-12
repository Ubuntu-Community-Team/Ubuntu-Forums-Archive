---
title: "[SOLVED] Text too small on the login when connected to my 46 inch HDTV"
date: 2007-10-22
forum: General Help
---

### Post by willz06jw on 2007-10-22
Thanks for your help,

My monitor is a 46 inch HDTV connected with a VGA cable directly to my Ubuntu computer.  Everything works very well so far.  The only problem I have had is on the login screen the text is so small that it is completely unreadable.  Once I login everything looks and acts great, but it is strange that I can't even read my login name when I type it in.

Does anyone know why this is happening?

Thanks again,
Will

---

### Post by ToastyX on 2007-10-22
It sounds like a DPI issue. See my reply in this thread: [http://ubuntuforums.org/showthread.php?p=3600024#post3600024](http://ubuntuforums.org/showthread.php?p=3600024#post3600024)

---

### Post by willz06jw on 2007-10-24
Thanks!  That completely fixed my problem ... although I wish I didn't have to fix anything.  I put a bug on launchpad in hope that they will fix it soon.

For everyone else I fixed it by following what ToastyX said in his earlier post:
> This sounds like a DPI issue. If you're using the binary NVIDIA driver, it will try to figure out the DPI of your display based on the DDC information and the current resolution, and text will be sized accordingly. 800x600 on a 42" display results in a low DPI, which results in small text. To fix this, you can manually set the DPI to a more sane value.

If you're using the binary NVIDIA driver, edit /etc/X11/xorg.conf, go down to the section that has Driver "nvidia", and add this line:

Option "DPI" "96x96"

Then restart the X server.

Thanks for your help!,
Will

---

### Post by jusmurph on 2007-10-24
> **willz06jw said:**
> I put a bug on launchpad in hope that they will fix it soon.

Not everything works automatically for everyoneometimes we have do the hard yards.

---

