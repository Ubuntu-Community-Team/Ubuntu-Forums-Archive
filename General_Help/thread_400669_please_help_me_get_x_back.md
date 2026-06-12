---
title: "please help me get x back"
date: 2007-04-03
forum: General Help
---

### Post by DougieFresh4U on 2007-04-03
Trying to edit xorg.conf I messed it up and now get blank screen after booting up. I can get recovery mode. I am using live cd to communicate now. If some one can help me mount and get back up, Thanks

---

### Post by zvacet on 2007-04-03
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DougieFresh4U on 2007-04-03
> **zvacet said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```

I tried to reconfigure using recovery mode as I can not boot to get to terminal. I am using live cd now so I can mount but I do not know how to do any thing more

---

### Post by Jeff24K on 2007-04-03
You say you can boot the LiveCD and mount your hard drive, right? You should be able to copy the xorg.conf from the "live" environment over top of your broken copy on the hard drive and get back to a sane default, which should allow you to boot from the hard drive noramlly.

Make a backup of the broken copy before you overwrite it so you have something to work from to rebuild your final version if you need it, and make another backup of the "fresh" LIveCD version along side that so you have everything you may need right at your fingertips if it goes bad again. ;)

---

### Post by rsambuca on 2007-04-03
It might help us to know what you were trying to do.  It might be a simple fix.

---

### Post by DougieFresh4U on 2007-04-03
> **rsambuca said:**
> It might help us to know what you were trying to do.  It might be a simple fix.

I had crashed my Xubuntu-Feisty over the weekend. I re-installed and my direct rendering was not working, so I was trying to re-configure xorg. Of course I have the crappy i810 chipset but as I said, direct rendering was working before I had to re-install Feisty. I now have gotten x up and running again. But I still would like to get the direct rendering again. i have looked at several threads regarding this issue and that  is what led me to break my x earlier. Any one have any ideas as to how I can get DRI on again? Thanks for all replies :)

---

### Post by tribble222 on 2007-04-03
> **DougieFresh4U said:**
> I tried to reconfigure using recovery mode as I can not boot to get to terminal. I am using live cd now so I can mount but I do not know how to do any thing more

Can you boot normally and then hit ctrl-alt-F1 to get to terminal and enter the code?  Otherwise, yes, the xorg.conf is stored in /etc/X11/xorg.conf so you could copy it to a different name and then replace it with a good one from your live cd session.

---

