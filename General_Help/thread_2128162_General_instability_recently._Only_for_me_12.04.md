---
title: "General instability recently. Only for me? 12.04"
date: 2013-03-22
forum: General Help
---

### Post by okok on 2013-03-22
I am using Ubuntu 12.04 with GNOME. I have not installed anything new recently, nor have I changed my pattern of work, but in recent days I have experienced unusual stability problems. There were several complete system freezes, and today all the menus and dialog boxes went completely white, with no content visible.

I could not find any problem with my hardware, and I usually accept the automatic updates, so I am wondering whether this may be a result of something that came in one of those recent updates, in which case other users might also have experienced similar problems.

---

### Post by Yellow Pasque on 2013-03-22
- Try running a LiveUSB of Ubuntu and see if issues occur.
- Run Memtest

---

### Post by okok on 2013-03-22
> **Temüjin said:**
> - Try running a LiveUSB of Ubuntu and see if issues occur.
- Run Memtest
Thanks, but a live USB won't help in this case because these errors have occured twice or so a day on average, and not in any particular circumstances that I could notice, so several hours or a whole day of smooth operation won't give any insight as to the source of the problem (and besides, this way I don't have access to all of my software and settings etc.). I have run hardware tests, including memory tests, and no hardware problem was found. This is almost surely a sofware problem.

---

### Post by rsrocha on 2013-03-22
My quantal install is crashing all over the place since the last updates. I heard precise is also affected with crash reports and freezing graphics.

---

### Post by vanadium on 2013-03-22
Strangely enough, same experience. My 12.10 became somewhat more slugish, and I experienced random freezes now and then. For me, it was definitely related to kernel updates: the problem dissappeared again after I reverted to a previous kernel (3.5.0-24). To the OP, although you are running the (super stable long-term release) 12.04, try also downgrading the kernel. If that is not the cause, you can easily upgrade to the last kernel again.

---

### Post by okok on 2013-03-27
My boot menu allows to me to choose "previous verions", and when I choose the 3.2.0-38-generic kernel those stability problem appear to be gone. I have been working with this kernel for two days now, and the system is perfectly stable again.

Any idea how should I go about making this change permanent, so that the next time I reboot my system it doesn't go back to the latest and very unstable kernel?


> **vanadium said:**
> Strangely enough, same experience. My 12.10 became somewhat more slugish, and I experienced random freezes now and then. For me, it was definitely related to kernel updates: the problem dissappeared again after I reverted to a previous kernel (3.5.0-24). To the OP, although you are running the (super stable long-term release) 12.04, try also downgrading the kernel. If that is not the cause, you can easily upgrade to the last kernel again.

---

### Post by vanadium on 2013-03-27
To my surprise, I did not find a clear standard procedure on how to revert to a previous kernel. In lack of a better solution, I have removed the latest kernels using synaptic package manager (not anymore installed by default0, and then "locked" the packages so they are not anymore updated. To my nowledge (and it actually works ;) there are four packages

linux-headers-[versionnumber]
linux-headers-[versionnumber]-generic
linux-image-[versionnumber]-generic
linux-image-extra-[versionnumber]-generic

Perhaps try first if just "locking" the package already makes you boot with that kernel. If after rebooting, you find that you are still in the higher version, then remove these.

---

### Post by pfeiffep on 2013-03-27
I was able to lock my version to one of my liking by using [grub customize]("http://ubuntuforums.org/showthread.php?t=1664134")r and changing the default setting to boot my kernel choice. Here's what it looks like ...
> linux    /boot/vmlinuz-3.5.0-24-generic root=UUID=0f3541ae-c4fe-4e96-a9e7-98bb51e9c34a ro   quiet splash $vt_handoff
initrd    /boot/initrd.img-3.5.0-24-generic


In this manner you can keep newer kernels to try at your leisure

---

### Post by Slim Odds on 2013-03-27
The primary cause of instability that I've seen with any version of linux that I've every used was always hardware.

Failing memory chip.
Drooping power supply voltage.
Hard drive about to give out.

I would investigate the hardware.

---

### Post by pfeiffep on 2013-03-27
In my case I firmly believe an UNDER powered laptop causes instability!

---

### Post by okok on 2013-03-27
Thanks for the answers. I'll try your advices.

As I explained before, in my case, I did test the hardware (which is fairly new and fast) for problems and found none, and switching to a different kernel version, as suggested by 
vanadium, DID solve the problem. I have been running my OS for two whole days now with the older kernel without a single problem. So at this stage it is quite safe to conclude that the problem was with the most up-to-date kernel, which probably came in one of the recent updates.

---

### Post by Slim Odds on 2013-03-27
> **okok said:**
> Thanks for the answers. I'll try your advices.

As I explained before, in my case, I did test the hardware (which is fairly new and fast) for problems and found none, and switching to a different kernel version, as suggested by 
vanadium, DID solve the problem. I have been running my OS for two whole days now with the older kernel without a single problem. So at this stage it is quite safe to conclude that the problem was with the most up-to-date kernel, which probably came in one of the recent updates.

Did you look at the list of changes in the latest kernel to confirm that there is actually a change that would have affected you?

Kernel updates for Ubuntu releases are very incremental (i.e., there are not a lot of changes in each one). They generally only put in very important fixes for known problems or security issues. Therefore the number of changes is very small and well defined.

Kernel changes between releases; well that's another story.

---

### Post by pfeiffep on 2013-03-27
> [COLOR=#000000]Did you look at the list of changes in the latest kernel to confirm that there is actually a change that would have affected you?[/COLOR]

[COLOR=#000000]Kernel updates for Ubuntu releases are very incremental (i.e., there are not a lot of changes in each one). They generally only put in very important fixes for known problems or security issues. Therefore the number of changes is very small and well defined.[/COLOR]

[COLOR=#000000]Kernel changes between releases; well that's another story.[/COLOR]

For a relatively new Linux user more substantial guidance please! Sometimes the quickest method to success **is a bigger hammer** - ie locking your kernel to a previous version! Maybe not pretty, maybe not elegant, but ultimately functional.

I'm hoping that raring will fix some of the nonsense OP and I have endured. BTW I joined U+1 just to help educate myself:P 

[COLOR=#ff0000]*Stupidity is a disease not able to be cured; while ignorance is easily remedied *[/COLOR]

---

### Post by okok on 2013-03-27
I am not a highly technical user, so those changes often mean very little to me. You are probably right that the changes between the versions are relatively small; or at least they don't seem to be of much significance to the kind of use I make of my computer, since everything seems to be wokring well again now that I switched to the previous kernel verion.

---

