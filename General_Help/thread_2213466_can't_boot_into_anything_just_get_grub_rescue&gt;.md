---
title: "can't boot into anything: just get grub rescue&gt;"
date: 2014-03-26
forum: General Help
---

### Post by mike-j-perrone on 2014-03-26
I have a dual boot setup: win8 and ubuntu. 2hds set up in RAID.

I don't know why, but whenever I turn on my computer it goes directly to "error: no such device 85ccc5d7-..." "grub rescue>". It can't access my bios settings, so I don't know how I can boot into a live CD/usb.

I've looked around at other threads like these:
[http://askubuntu.com/questions/337244/grub-rescue-no-such-device-also-cannot-access-bios](http://askubuntu.com/questions/337244/grub-rescue-no-such-device-also-cannot-access-bios)
[http://ubuntuforums.org/showthread.php?t=1509922](http://ubuntuforums.org/showthread.php?t=1509922)
and I've tried a few of the suggestions there. Unfortunately a lot of them require that I boot a live cd.

Specifically, when I run "ls" it gives
```
(hd0) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)
```
when I run "ls hd0" and "ls (hd0,msdos1)", and ls on the rest I each time get
```
error: unknown filesystem.
```

Any suggestions would be helpful, and if I've left out any information that could be useful, let me know

---

### Post by Navneet_Kumar on 2014-03-27
You can just try the following commands :
[http://askubuntu.com/questions/192621/grub-rescue-prompt-repair-grub](http://askubuntu.com/questions/192621/grub-rescue-prompt-repair-grub)

[http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash](http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash)


Hope they will help......

---

### Post by Bucky Ball on 2014-03-27
Welcome. You don't mention which release you are using. 12.04 LTS, 13.10?

You can't access your BIOS settings? Is this a new problem? You must have been able to get there to do the Ubuntu install I'm guessing ... :-k

Have you tried turning on the computer and immediately hitting F12? That might at least get you to a list of boot device options so you can boot from a CD. If this works, you could try running Boot Repair and seeing if that fixes things ...

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by mike-j-perrone on 2014-03-27
[ @]("http://ubuntuforums.org/member.php?u=1913241")[**[COLOR=#000000]Navneet_Kumar[/COLOR]**]("http://ubuntuforums.org/member.php?u=1913241")
I ran
```
set root=X
set prefix=X
insmod normal
```
for each of X="(hd0,msdos5)","(hd0,msdos2)", "(hd0,msdos1)"

each gave me the following error:
```
error: unknown filesystem
```

With regards to your second link: since when I ls all of those partitions I get the filesystem error, I can't find /boot, so I can't run those commands.

---

### Post by mike-j-perrone on 2014-03-27
@Bucky Ball
I'm using 12.04 LTS. However, I haven't boot into ubuntu on this machine in several months. It's a dual boot and I only use win8 on it at this point(I have ubuntu on another machine).

Immediately after turning on my computer I've tried spamming F2, F5, F10, F12, and DEL. None of these have gotten me to the BIOS menu. It's strange to me because grub is on top of the BIOS so clearly the BIOS is working right? Since I can't get into the BIOS, I can't change the boot priority and I can't boot from a live disk to repair grub (which I think is the problem?). Getting to that point would make me pretty happy and make it fairly clear to me what to do.

This is a new problem. It happened two nights ago. Thinking the error meant my harddrives died, I popped them into another machine, booted those machines from a livecd and ran some tests on each of them. They both were not dead. I then put them back into my original laptop and then magically it booted into grub, win8, and everything was fine. The next morning when I turned it on, the same error came up. So hoping the black magic of the day before would work again, I put it into the other machine, ran the tests, and tried again. Didn't work that time.

Another thing I've tried is resetting the motherboard by unplugging the battery as well as the motherboard battery. Didn't change anything.

---

### Post by Bucky Ball on 2014-03-27
Is this a laptop or a desktop? Sounds like a laptop. Take the battery out, unplug the power cable, hold the power button down for thirty seconds (I usually go a minute), plug the power cable back in (NOT the battery) and boot the machine ...

You also give no detail of your machine, but if the battery is a few years old, and all depending on how it's been used, it could be faulty and dying. That will be read as a hardware issue and prevent the machine from booting. 

Welcome to the forums, BTW. ;)

---

### Post by mike-j-perrone on 2014-03-27
Here's the laptop:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834152296](http://www.newegg.com/Product/Product.aspx?Item=N82E16834152296)

I did what you suggested (battery out, power cable out, power button 1min, power cable in, power on) and nothing changed. I assume you just meant the laptop battery, not the internal battery for the motherboard?

Thanks for the welcome =]

---

### Post by oldfred on 2014-03-27
Also is this Windows 8?
Then you need to turn fast boot off which is always on hibernation. Some BIOS also have the quick boot setting that bypasses all UEFI/BIOS boot to make Windows boot faster. Microsoft requires vendors to make Windows boot faster.
And then you can only get into UEFI/BIOS from Windows 8, which if Windows 8 stops working may cause major issues as then there is not easy way to get into UEFI/BIOS.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by mike-j-perrone on 2014-03-27
@oldfred thanks for the response and the links.

It is windows 8. The fast boot thing may be the problem. I would love to boot into  windows in order to turn of fast boot, but I can't boot into anything at  all. Do you know how I can go about doing that?

---

### Post by oldfred on 2014-03-27
I only know Buckyball's suggestion to remove battery and do a full cold reboot.

Some MSI have had some issues.
       
 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

---

