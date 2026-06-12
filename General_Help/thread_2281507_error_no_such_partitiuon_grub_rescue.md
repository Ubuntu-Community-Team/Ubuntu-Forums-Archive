---
title: "error: no such partitiuon grub rescue"
date: 2015-06-07
forum: General Help
---

### Post by ajay12 on 2015-06-07
i have a dual booting system(windows 8 and ubuntu 14.04).
Recently i deleted my ubuntu partition and now i am getting "error: no such partition grub rescue>"
on restart.
i tried to use a live usb of ubuntu 14.04 but to no use as i finally shows 
"busybox v1.21.1 built-in shell 
 (initramfs) unable to find a medium containing a live file system"

please help....

---

### Post by ajgreeny on 2015-06-07
Having deleted the ubuntu partition you now have no configuration files for grub, thus you get the grub rescue prompt.

If you made the appropriate repair DVDs when you first got your Win 8 machine or if you have a DVD of the Win 8 system you can easily restore the windows bootloader files and all should be well again.  However, not having used Windows since my XP days I can not help with details of how to restore that bootloader.  A google search should help you find out how.

---

### Post by ajay12 on 2015-06-14
yeah, i had to get a bootable usb with windows 8 on it.Worked for me.

---

### Post by ventrical on 2015-06-14
I have had a lot of success in this using grub rescue cd.

[http://ubuntuforums.org/showthread.php?t=2282431&p=13303588#post13303588](http://ubuntuforums.org/showthread.php?t=2282431&p=13303588#post13303588)

---

