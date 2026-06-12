---
title: "Boot problems - boot from &quot;savedefault&quot; in grub only working option"
date: 2007-02-26
forum: General Help
---

### Post by KimTjik on 2007-02-26
Hi!

I'm more or less a first time user of Ubuntu, but not totally new to Linux, even though I'm more used to work with Fedora- and Slackware-based systems.

My issue can be seen by the title. "menu.lst" and "fstab" are coherent, so there's no classic problem of them pointing to different locations for the "/"-partition. Two kernels are present: 2.6.17.10 and 2.6.17.11, and initially both gave me the same symptom of booting up to the point when it should load the in-logging screen, but instead froze the system. By hitting "b" from "savedefault" in the grub-menu the system boot fine and this works for both kernels. 

I saw the list of "Known bugs and workarounds" and thought that the "Generic kernel don't boot issue" could apply to me, even though secondary problem with Nvidia drivers doesn't. I followed the instructions of creating an initramfs script manually; the only difference was that I made it for the 2.6.17.11 kernel instead. Unfortunately this only made the 2.6.17.11 totally unable to boot, even from "savedefault". So as it is now I can only boot from 2.6.17.10 "savedefault", which makes it more hazardous for me to change anything in grub, because there's no working back-up at this moment.

I've search the web and this forum, but never really saw anything similar. Mostly booting issues seem to have been caused by grub pointing to the wrong root partition or dual boot issues. Neither is applicable in my case.

Hardware in question: Intel P4 processor with i845 chipset and hence just simple IDE-devices.

Does anyone know what causes this? The computer isn't prepared for myself, I just made it multimedia and mozilla-plugin ready, besides installation of the operating system and a good selection of needed software. Hence I would like it to be able to boot without any hassle; for me it could be annoying to enter the grub menu every time, but for the owner it would scare him and made him very suspicious about the whole system; and we don't want that, do we?

Regards,
KimTjik

---

### Post by KimTjik on 2007-02-26
Update:

One progress is that I now have two working kernels, but still just from "savedefault", this by once more manually create initramfs. For some reason the first attempt didn't set it up correctly, so when booting grub couldn't find anything in /lib/modules/2.6.17.11-generic. Now it does, so at least I have two kernel options to play with, but I'm not a bit closer to understand what's causing this issue.

---

### Post by KimTjik on 2007-02-26
Alright, I'm still alone in this thread. Instead of hunting for more clues does anyone know how to figure out a workaround?

As I can understand "savedefault" actually has nothing to do with the boot process, but simply a command to direct the selection boot-option. Am I right? At least I might get a yes or no on that question.

As it is now I don't know if I'm dealing with a bug in grub or ubuntu. I've searched for an hour today as well, and still I can't find anything helpful. So, please, if anyone has even a hint of where to search for an answer or a suggestion make it heard!

---

### Post by KimTjik on 2007-03-06
It looks like there's no real interest in my problem, which feels a bit strange since this is one of the biggest forums for Linux. I hope I don't offend anyone, but this will become a deciding factor for whether I keep on running Ubuntu or not.

To the problem: could it be that some aggressive hd parameter is used by default? If plausible, can anyone give me a hint about how to solve it?

The system keeps on booting faithfully as long as I enter grub and press <B> from "Savedefault", which still doesn't make any sense to me. The person using the system has accepted the annoyance for now, but has had a good laugh over it.

I wonder what the difference is between how Ubuntu boot in comparison to Fedora, because Fedora based system work stable and never fail to boot the system.

---

### Post by confused57 on 2007-03-06
> **KimTjik said:**
> It looks like there's no real interest in my problem, which feels a bit strange since this is one of the biggest forums for Linux. I hope I don't offend anyone, but this will become a deciding factor for whether I keep on running Ubuntu or not.

To the problem: could it be that some aggressive hd parameter is used by default? If plausible, can anyone give me a hint about how to solve it?

The system keeps on booting faithfully as long as I enter grub and press <B> from "Savedefault", which still doesn't make any sense to me. The person using the system has accepted the annoyance for now, but has had a good laugh over it.

I wonder what the difference is between how Ubuntu boot in comparison to Fedora, because Fedora based system work stable and never fail to boot the system.
Maybe there' something in this link that might help:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

You might want to post your /boot/grub/menu.lst, maybe someone will see a problem

posting your partition layout may help also:
```
sudo fdisk -l
```

---

### Post by KimTjik on 2007-03-10
> Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         969     7783461   83  Linux
/dev/hda2             970        2434    11767612+   5  Extended
/dev/hda5             970        1098     1036161   82  Linux swap / Solaris
/dev/hda6            1099        2049     7638876   83  Linux
/dev/hda7            2050        2434     3092481   83  Linux

> 
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot
Sorry for being late with an answer. I can't see any strangeness in the above.

Another note: it could be Ubuntu has problems setting up the monitor correctly. This is how xorg.conf looks like:
> Section "Monitor"
	Identifier	"Elographic Screen"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection
I'm used to that xorg.conf is giving the parameters, but it looks like Ubuntu doesn't work this way, or I'm misunderstanding something here. VertRefresh is set to 43-60, but Ubuntu refuses to use anything else but 75; if using the GUI it doesn't even giving any other choices. I don't understand this: how come xorg.config states one thing and Ubuntu still working differently. Is the xorg.config obsolete, or what have I misunderstood?

Anyhow the above lead to a problem when using a projector: nothing but a screen-resolution of 800x600 would work because of this. Same system setup and Fedora prefer 60Hz.

---

### Post by KimTjik on 2007-03-19
If anyone had a good suggestion I suppose it would have been posted by now.

Actually this thread could be closed as "Unsolved", because I've no other choice than to install another system. The Ubuntu system has started to overall degrade and become terribly slow; today it started to switch by itself default sound-cards back and forth, which of course made a mess of all configurations already made for audio software and IP-telephony; several system configuration tools start to freeze, just as Gnome as a whole.

So in this specific computer Ubuntu certainly looks like a very bad idea. The only comfort is that I've encountered some other folks with similare experience, which leads me to think that Ubuntu is developed on a too narrow selection of hardware. A standard IBM NetVista with an Intel P4 1.8GHz and i845 chipset should practically work whatever junk was thrown at it.

No hard feelings here, nevertheless it might take some time before my confidence in Ubuntu get reestablished.

Keep up the good work folks!

PS. This thread became more of a blog, didn't it? DS.

---

### Post by KimTjik on 2007-03-24
Another day without Ubuntu but with some thoughts about Gnome:

I don't know if I'm wrong or right, but my experience tells me that Gnome is less reliable than KDE when it comes to configuring sound-cards. If I get some spare time I'll investigate it further, since Kubuntu at least would be an option to evaluate the differences. Of course my need for using two sound-cards simultaneously might not be what the average user looks for, nevertheless I have yet to encounter in the KDE the difficulties I've experienced in the Gnome desktop environment.

You might wonder: "what system did you install to that friend of yours"? The answer is: Pardus. It could well be that Pardus become a real contender for Ubuntu. Pardus has several good ideas and stuff going for them.

...

Back to the initial topic: I'll make another test with Ubuntu - as already said when I get some spare time - to also track down the problems Ubuntu has booting the IBM NetVista system. I'm more and more inclined to think it has something to do with the parameters for the IDE hard-drive. I'll compare the results given by a totally new hard-drive.

---

