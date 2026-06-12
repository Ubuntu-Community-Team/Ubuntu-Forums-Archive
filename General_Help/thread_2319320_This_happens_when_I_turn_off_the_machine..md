---
title: "This happens when I turn off the machine."
date: 2016-04-03
forum: General Help
---

### Post by amol7 on 2016-04-03
I've searched this forum and many other websites on the internet.
So posting a new thread here.

I get the following message while the machine is shutting down. And about 20 lines of it.
```
[drm:gen8_irq_handler [i915_bpo]] *error* the master control interrupt lied (sde)!
```

I do not know if this is a Display related error. Based on some research, I feel this mssg is related to Display.
I do not receive this message upon startup. Only when shutting down. The screen kinda blinks, but, only once. (I wish I could put up the video)
Otherwise my display works well. No flickering No blinking etc.

Any suggestions / advice.

Machine is HP 15-AC170TU.

~a

---

### Post by Bucky Ball on 2016-04-03
Do you have an sde drive? That seems to be where its coming from. Give us the output of 'lsblk' from a terminal. Wrap it in code tags, thanks (green link in my signature for how).

---

### Post by amol7 on 2016-04-03
```
NAME                         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                            8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1                         8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2                         8:2    0   244M  0 part /boot
&#9492;&#9472;sda3                         8:3    0   465G  0 part 
  &#9500;&#9472;ubuntu--vg-root (dm-0)   252:0    0 461.1G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 (dm-1) 252:1    0   3.9G  0 lvm  [SWAP]
sr0                           11:0    1  1024M  0 rom  

```

Thanks

~a

---

### Post by Bucky Ball on 2016-04-03
Looks like a [known bug ]("http://askubuntu.com/questions/687402/log-error-drmgen8-irq-handler-i915-error-the-master-control-interrupt-l")and perhaps nothing to worry about unless it is causing long delays. You might want to [dig deeper]("https://duckduckgo.com/?q=the+master+control+interrupt+lied+%28sde%29&t=h") and see what you can find.

Also looks like you've encrypted your Ubuntu install for some reason. Did you have a specific one? And also added a /boot partition. You already have an /EFI boot partition. Any reason you added the second one? They can be more trouble than they're worth (when they fill up and you need to empty).

* Just before we go any further, which release are you using? This appears to be fixed in the newer kernels ...

---

### Post by amol7 on 2016-04-04
Well I had an issue with the installation and so I seeked help here [http://ubuntuforums.org/showthread.php?t=2316116](http://ubuntuforums.org/showthread.php?t=2316116) before.
That didn't go down well so I had to install Ubuntu on the Whole Disk option (Erase entire Disk)
I don't really remember the options I selected during that installation.

The machine is running 14.04. I had downloaded the latest iso file from the official website. And that's what I used to install.

> Also looks like you've encrypted your Ubuntu install for some reason.  Did you have a specific one? And also added a /boot partition. You  already have an /EFI boot partition. Any reason you added the second  one? They can be more trouble than they're worth (when they fill up and  you need to empty).


Do you think this will cause problems in the future? If yes, should I install it again.? (Of course then after I have to do a lot of work like here [http://ubuntuforums.org/showthread.php?t=2317052 )]("http://ubuntuforums.org/showthread.php?t=2317052")

Thanks

~a

---

### Post by amol7 on 2016-04-14
Can anyone help me out?

Or I let it just be. Since it is considered that this prob doesn't cause any further problems?

~a

---

