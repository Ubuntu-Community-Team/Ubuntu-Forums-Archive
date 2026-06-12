---
title: "fglrx error message"
date: 2004-11-12
forum: General Help
---

### Post by stateq2 on 2004-11-12
Hi,

According to lspci, my video card is:
```

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```
So i installed my kernel headers, and the fglrx-driver and stuff.  But at boot, I get this error:
```

[fglrx:firegl_init] *ERROR* Device not found!

```
and X fails to start.  The only way I can use X, is if I change back to the generic "ati" driver in the X config file.  Any ideas?  thanks.

---

### Post by ubuntu-geek on 2004-11-12
Did you load the driver line into the /etc/modules file? On Section 2, Number 3 of this link make sure you follow that. [http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)

It kind of sounds like the driver isnt getting loaded correctly.

---

### Post by HiddenWolf on 2004-11-13
Try to re-do the howto in the wiki.

That worked flawlessly for me running warty.

However, support for those mobilities sucks, as do the fglrx drivers in general.

On a laptop, you are probably far better off using the dri drivers that XFree provides.

It might change in the future, but atm fglrx isn't worth your time.

---

### Post by stateq2 on 2004-11-13
[QUOTE=ubuntu-geek]Did you load the driver line into the /etc/modules file? On Section 2, Number 3 of this link make sure you follow that. [http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)

It kind of sounds like the driver isnt getting loaded correctly.[/QUOTE]

yes...I followed the howto here.....
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

[quote=HiddenWolf]
On a laptop, you are probably far better off using the dri drivers that XFree provides.
[/quote]

Since I've been a nvidia person until about 3 days ago...please excuse this question.  Is there a howto on this....or should I run the xconfig or something?  thanks.

---

