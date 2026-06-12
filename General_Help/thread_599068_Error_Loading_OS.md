---
title: "Error Loading OS"
date: 2007-10-31
forum: General Help
---

### Post by mcar2185 on 2007-10-31
OK, I had two harddrives in my computer. The master had only XP installed on it, while the newer slave had Ubuntu Studio edition installed on it. The master harddrive crashed this week, and since then, I have set the jumpers on the other HDD to master and hooked it up accordingly. However, I am getting an "error loading OS" message when trying to boot the computer in Ubuntu. How do I fix this?

---

### Post by confused57 on 2007-11-01
> **mcar2185 said:**
> OK, I had two harddrives in my computer. The master had only XP installed on it, while the newer slave had Ubuntu Studio edition installed on it. The master harddrive crashed this week, and since then, I have set the jumpers on the other HDD to master and hooked it up accordingly. However, I am getting an "error loading OS" message when trying to boot the computer in Ubuntu. How do I fix this?
Grub's IPL was probably installed on the Windows drive's mbr...you'll need to use the Ubuntu live cd to install grub to the Ubuntu drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Read the instuctions in the tutorial...you'll do something like:
```
root (hdx,y)
setup (hdx)
```

You'll probably need to change root from (hd1,y) to (hd0,y) when you boot your pc after reinstalling grub...you can do this by highlighting your first Ubuntu entry in the grub boot menu, press "e", select the line with root, press "e" again, change root to (hd0,y), press "enter", then "b" to boot...y means leave this value as it is.

This change is temporary, but you can make it permanent in your /boot/grub/menu.lst, if it works.

---

### Post by mcar2185 on 2007-11-01
The Live CD doesn't work with my computer, unfortunately. So I'm using the text-based alternate. I'm trying to re-install GRUB using the rescue system feature. I try to reinstall it in SDA or SDA2 and get a fatal error. What do I do?

---

### Post by mcar2185 on 2007-11-01
Is there any way to use the alternate CD to retrieve the GRUB menu?

---

### Post by confused57 on 2007-11-01
> **mcar2185 said:**
> Is there any way to use the alternate CD to retrieve the GRUB menu?
Here are instructions using the alternate cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

---

### Post by mcar2185 on 2007-11-02
Are there any ways of making a GRUB bootable CD? I don't have any blank floppys on me right now and want to get Ubuntu working.

---

### Post by shad0w_walker on 2007-11-02
You should probably try out super grub disc. It's got a pretty simple interface to help you reinstall grub as needed.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by mcar2185 on 2007-11-02
OK, thanks, it got the menu back, but when I attempt to boot I get:

Error 21: Selected Disk does not exist

What now?

---

### Post by shad0w_walker on 2007-11-02
When the grub menu comes up, select your entry and press the 'e' key. This puts you into edit mode. Select the line saying root (hdx,x) 

The numbers vary from system to system. If your system already says something like (hd1,0) try changing the 1 to a 0, or if it says 0 try changing it to a 1. When you have changed it press enter to confirm it and then press b to boot with those settings.

 If it works you should boot into Ubuntu, you will however need to tweak your menu.lst file for grub so it knows the right harddrive by default.

---

### Post by mcar2185 on 2007-11-02
It worked, thank you! I just have to do what you said with the menu file and it should be fine.

---

