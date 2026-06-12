---
title: "slow compiz, slow xgl"
date: 2008-04-27
forum: General Help
---

### Post by akimatsu123 on 2008-04-27
hi,

im on hardy and an ATI video driver (IBM T60p). 

How do i get compiz working? compiz will not start without the xgl package installed (even though i heard you don't need it anymore).

When xgl IS installed, it slows my computer down so much (even though compiz does indeed work) that it's pretty much unusable. 

How do i speed up my xgl? i remember i did something to it in Gutsy but i can't quite remember. 

Thanks

---

### Post by Lithia on 2008-04-27
It ended up working well for me once I had both fglrx working correctly (fglrxinfo returns ATI card information) and I had composite enabled in /etc/X11/xorg.conf.

So, uninstall xserver-xgl and make sure fglrxinfo returns the correct information (if that doesn't work, go here:
 [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=769214]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=769214")

Once that is all working, you can then add/edit this section to/in your /etc/X11/xorg.conf

```
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```

Hope this helps!

---

### Post by Zorael on 2008-04-27
To explain, xserver-xgl makes Compiz use software rendering, making things slow.

You may want to mark thread as solved, though.

---

### Post by gerben1 on 2008-04-28
have you seen this:
[http://www.realistanew.com/2008/04/23/fglrx-breaking-upgrades-to-804/](http://www.realistanew.com/2008/04/23/fglrx-breaking-upgrades-to-804/)

---

