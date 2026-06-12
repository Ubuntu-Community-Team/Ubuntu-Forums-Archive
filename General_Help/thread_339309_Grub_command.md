---
title: "Grub command?"
date: 2007-01-15
forum: General Help
---

### Post by m0u53m4t on 2007-01-15
Im new to this, what exactly do I have to do (Line by line if possible) to do this?
> 
Now grub:

```
gksudo /media/ubuntu/boot/grub/menu.lst
```

Look at your ubuntu stanzas.

Change to:

root (hd0,1)

kernel /boot/vmlinuz..... root=/dev/hda2 ....

Save and exit.

---

### Post by meng on 2007-01-15
There's a typo in those instructions.
1. Open a terminal
2. Type:
gksudo gedit /media/ubuntu/boot/grub/menu.lst
(and enter your user password when prompted)
3. Then use the graphical text editor that opens to make the changes described. When finished, save changes and exit.

You didn't give the complete instructions, so I assume you followed all the steps up to that point. Good luck.

---

### Post by m0u53m4t on 2007-01-15
Typical, it was already that after all that fuss XD

---

### Post by meng on 2007-01-15
> **m0u53m4t said:**
> Typical, it was already that after all that fuss XD
I'm not sure I understand you.

---

### Post by m0u53m4t on 2007-01-15
Sorry, it was already  (hd0,1)

Im still getting the error though. I've removed Windows now and thats still got an option in the menu.lst

Do I need to remove that as well to get it to work?

---

### Post by Ramses de Norre on 2007-01-15
Maybe you should first tell us about the error ;)

The windows option should not cause any harm, but you'll get an error message if you select it. So it may be better to just remove it, yes.

---

### Post by m0u53m4t on 2007-01-15
When I reboot now I just see this straight away:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22

I've just made a new partition on my hard drive and copied linux there. Thats why I've had to change those things, but I'm still getting the error. Any ideas?


Edit: Im just going to reinstall. Its easier. Can I just delete all my partitions and then install from the disk?

---

### Post by Ramses de Norre on 2007-01-15
Are you sure you're filling in the right partition in menu.lst?
If you tell us you're whole hard drive setup (sudo fdisk -l && cat /etc/fstab) we'll be able to help.
I guess you don't have a separate /boot partition or such?

---

### Post by Tux Aubrey on 2007-01-15
I'm not sure what the problem is here or what setup you are using, but the command:

> gksudo gedit  /media/ubuntu/boot/grub/menu.lst

does _NOT_ open the active version of grub's menu.lst

I think you will find that:

> gksudo gedit  /boot/grub/menu.lst

does the job on a regular Ubuntu install.

If you have removed windows, grub would still work OK but you can just edit out the stanzas in menu.lst that refer to it to tidy things up.

---

### Post by bodhi.zazen on 2007-01-15
If it helps anyone, this is a continuation of this thread:

[http://ubuntuforums.org/showthread.php?&t=339059](http://ubuntuforums.org/showthread.php?&t=339059)

meng: > There's a typo in those instructions.

:redface: Ooops, I was typing too fast, thanks for catching that.

The last advice I had given was to re-install grub and had asked for the output of fdisk -l so that I could give explicit directions:

```
sudo grub
root (hd0,x)
setup (hd0)
```

After moving the ubuntu root partition I am not sure of what x =
And we need to make sure fstab is updated as well :p

HTH

---

### Post by m0u53m4t on 2007-01-16
Thanks guys, but I just reinstalled instead, I'd only had it for a day so no new software was on it :p

---

