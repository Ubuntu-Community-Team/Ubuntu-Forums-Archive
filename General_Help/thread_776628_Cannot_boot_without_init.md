---
title: "Cannot boot without /init?????"
date: 2008-04-30
forum: General Help
---

### Post by irunwithknives on 2008-04-30
I used the command
```
sudo update-initramfs -u
```
after setting the bootsplash resolution to my screen size.

Terminal froze, and I rebooted, and now it says that I cannot boot without /init, and to try to bypass or something to load the kernel. Right now, I am using my live CD, and I hope I dont have to do a fresh install, cause I just did one like last week cause I screwed something else up.

WHAT SHOULD I DO?

---

### Post by ryanhaigh on 2008-04-30
If you have an old kernel in your grub list you could try booting from that.

---

### Post by rajan on 2008-04-30
this thread might help, especially the part where it has instructions about grub. you probably want to do the update to grub. 

[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)


what specifically is your problem? does the problem happen right where the bios hands off control to GRUB?

---

### Post by ebelog on 2008-04-30
You can try to boot into rescue mode by hitting esc during boot when grub tells you to, and then choosing the rescue mode option.

You can then try to fix the problem before rebooting again. Unfortunately, it's not clear what caused the problem, and because you used "update-initramfs -u" to update the initial ram disk rather than "update-initramfs -c" to create a new one, you don't really have a good back-out solution.

You can try updating the intial ram disk again using "update-initramfs -c" in rescue mode, or you can try updating the kernel, which will also recreate that important file. If those don't work, reinstalling is your best option.

Good luck.

---

### Post by irunwithknives on 2008-05-01
thanks all, but i tried some of those on my own, and just decided to do a fresh install.  I really needed to clean out my harddrive anyways.

---

### Post by warp99 on 2008-05-01
> **irunwithknives said:**
> I used the command
```
sudo update-initramfs -u
```
after setting the bootsplash resolution to my screen size.

Terminal froze, and I rebooted, and now it says that I cannot boot without /init, and to try to bypass or something to load the kernel. Right now, I am using my live CD, and I hope I dont have to do a fresh install, cause I just did one like last week cause I screwed something else up.

WHAT SHOULD I DO?

For future reference you can update the initrd.img this way:

[http://ubuntuforums.org/showpost.php?p=4849200&postcount=2](http://ubuntuforums.org/showpost.php?p=4849200&postcount=2)

---

