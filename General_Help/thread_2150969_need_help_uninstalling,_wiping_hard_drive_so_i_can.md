---
title: "need help uninstalling, wiping hard drive so i can get different linux distro"
date: 2013-06-02
forum: General Help
---

### Post by awesomesauce1414 on 2013-06-02
hello, so a while back i got linux ubuntu 12.04 to use on my laptop as windows was loaded with ransomware and i thought ubuntu would be cool to try. so i have been using ubuntu for a few months now and i have been slowly getting problems so i think it's time to go for something else. ever since i have started using ubuntu it has bot wanted me to try and install a new partition on the drive. so i want to wipe it and start over with preferably fedora. so i have tried putting in the live USB and DVD and have been getting this message - "SYSLINUX 4.03 2010-10-22 EDD Copyright 9C0 1994-2010 H. Peter Anvin et all" and am not being to acces my live USB files to go into the partition editor to delete everything (i have no important information on my hard drive that needs to be kept)

So i guess the big question here since i may have been rambling on is "how do i wipe ubuntu and GRUB to start with a fresh hard drive to run a new linux"

---

### Post by prodigy_ on 2013-06-02
You should be able to delete existing partitions from Fedora installer. No need to that from Ubuntu. But if you can't boot from Live media, it might indicate a hardware issue.

Try to burn a CD with Fedora and boot from it.

---

### Post by speartip on 2013-06-03
Ubuntu is still probably the most user friendly & hardware compatible distro there is.
If you are having issues with Ubuntu, chances are you will have more issues, or at least different issues with something else.
It may be better to list what your problems are and see if anyone on here can help you resolve them.

---

### Post by Mark Phelps on 2013-06-03
My suggestion, since Ubuntu is not working well for you, is to try Linux Mint.  I believe v15 just came out.  You can find it, along with a lot of other distros, on the distrowatch.com website.

---

### Post by awesomesauce1414 on 2013-06-03
nope, same message "[COLOR=#000000]SYSLINUX 4.03 2010-10-22 EDD Copyright 9C0 1994-2010 H. Peter Anvin et all" when i try to boot from dvd and USB with Unetbootin. tried with fedora, debian, ubuntu, and mint. i need to know how to get my hard drive wiped inside of ubuntu[/COLOR]

---

### Post by speartip on 2013-06-03
I hope i'm not insulting your intelligence here, but you are actually booting from your cd/usb (ie rebooting the computer with your cd/usb as the first drive to boot from) and not trying to wipe your hard drive while on your desktop?
 Because you can't wipe your hard drive "while in ubuntu" as all your partitions need to be unmounted.
To wipe your entire hard drive, just download a copy of gparted iso image from here:
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.16.1-1/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.16.1-1/)
Burn to disk, boot from it, and wipe your entire disk.
Alternatively any live linux cd should have a partitioner editor on it too mess with your partitions/hard drive, just make sure all partitions are unmounted 1st.

---

### Post by awesomesauce1414 on 2013-06-04
yah i see what your saying but i can't boot from a disk or USB. that's my problem. it's working on my dad's desktop but not my laptop i'm currently on

---

### Post by awesomesauce1414 on 2013-06-04
[COLOR=#000000]yah i see what your saying but i can't boot from a disk or USB. that's my problem. it's working on my dad's desktop but not my laptop i'm currently on[/COLOR]

---

### Post by Warprunner on 2013-06-04
> **awesomesauce1414 said:**
> [COLOR=#000000]yah i see what your saying but i can't boot from a disk or USB. that's my problem. it's working on my dad's desktop but not my laptop i'm currently on[/COLOR]

Just a thought, did you adjust your BIOS to boot from CD/DVD or USB first? I know I am really opening up a can of worms here.

When your computer first boots up... you need to press the F2 or F10 button depending on your BIOS. Once in there you go to bootable options or it will say something similar. Change the Hard Disk from being 1st. Put the USB or the CD/DVD drive first. Save changes, then exit. It will reboot and try to load from your USB or CD/DVD.

_***[COLOR=#ff0000]BE CAREFUL IN THE BIOS!!!!!! [/COLOR]***_

---

