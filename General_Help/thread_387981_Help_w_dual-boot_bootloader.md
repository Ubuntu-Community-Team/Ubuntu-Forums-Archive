---
title: "Help w/ dual-boot bootloader"
date: 2007-03-18
forum: General Help
---

### Post by MeathooK427 on 2007-03-18
I'm running Ubuntu Edgy on my first partition, sda1. I also have an install of Windows XP Home on sda3. Here's the thing, I installed Ubuntu first to set up the partitions correctly, then installed Windows. Everything went fine, I pop in my Super Grub Disk to restore the Grub as the MBR, then things start getting weird. Ubuntu tries to load the first time, and has to do a checkdisk for some odd reason (first time it's happened on an ext3 install). After that, it loads into Ubuntu fine, but things are weird, my Beryl install is being funky (Window menu bars, whatever you want to call them) aren't showing up, and I have to set the desktop manager back to metacity, then restart Beryl, and back to setting Beryl as the desktop manager before it works correctly. Then I start noticing random lockups, YES, LOCKUPS IN LINUX! Now, whenever I boot into Windows...I no longer have support for my keyboard, which I've tried two different keyboards, both of them lacking support. Whenever in device manager, there's an exclamation point by the keyboard, saying the device couldn't start. So I go into the XP boot CD, and restore the Windows MBR, and to my luck, I have keyboard support back. 

My question: Is there something w/ the Grub boot loader that "Super Grub Disk" installs that messes things up? Is there a repair feature on the Live CD to repair the Ubuntu install? How much of a pain in the A** is it to add Ubuntu to the Windows MBR? 

Thanks in advance!

edit: Sorry for the novel.

---

### Post by Herman on 2007-03-19
Hello MeathooK427,
That's an extremely unusual problem that you are reporting, I can't imagine how grub or supergrub could possibly affect your keyboard in Windows. 
For interest's sake, can you tell me anything about your hardware, like the brand and model of your computer, just in case someone else has the same problem some day? It's an interesting problem. Motherboard, BIOS and keyboard info could be interesting too, if it isn't too much of a chore. I like to collect info like that if I can.

Linux computers do an automatic filesystem check once every 30 mounts (boot-ups) so that could be normal. Another reason it might bring on a filesystem check early is if the filesystem is marked 'dirty'. (maybe from a bad shutdown), I would be surprised if it has anything to do with grub or super grub disk. Probably it's just a co-incidence.

If you really think it has something to do with grub's IPL being installed in your hard disk's MBR, you could try [WinGrub]("http://users.bigpond.net.au/hermanzone/p9.html") instead maybe.

There is no such thing as a 'Windows MBR', Windows has a bootsector, and Windows has a bootloader, and Windows bootloader's IPL can be written to the IPL section of the hard disk's MBR. 
The IPL, (also called 'stage1') for the Grub bootloader, or LiLo, or GAG can also be written to the hard disk's MBR, overwritting Window's bootloader's stage1 code. I expect you know all that but your are saying it that way for brevity.  The problem with that is, it can lead to new users misinterprting things and becoming misinformed and ultimately making mistakes with the way they make up commands to re-install their bootloaders. (Several have actually written grub's IPL to their Windows bootsector).

To fix your Ubuntu install, try opening a terminal in your Ubuntu desktop live cd and running a filesystem check again, this command works well for me, 
```
sudo e2fsck -C0 -p -f -v /dev/sda1
``` It would be best to copy it right from this post and paste it into your terminal rather than try to type it manually, unless you know what you are doing.  See if that fixes your Ubuntu install. 
If that one didn't help after you reboot and try your Ubuntu install out, reboot your live cd and try this one, ```
sudo e2fsck -c -c -v /dev/sda1
``` See if that one helps you.
Regards, Herman :)

---

### Post by MeathooK427 on 2007-03-19
Herman,

Thanks for your interest and help. My hardware is as follows:

Asus Crosshair AM2 board - Bios Rev. 0502 
AMD Opteron 1212 (OC'd to 2.8ghz) Maybe that has something to do w/ it? idk
2 x 1024MB Corsair DDR 800 Running at 933Mhz
BFG 8800 GTS 320MB OC

OS's used: Windows XP Home SP2 (updates finished), and Ubuntu Edgy

Another weird thing, whenever I FIXMBR'd in the XP boot CD, I didn't have support for my main keyboard (Microsoft multifunction..thing), but when I used my dads Dell kind of standard IBM looking keyboard, I was able to get to the recovery console. However, with that IBM/Dell keyboard, I still didn't have keyboard support in Windows before I fixed the MBR. Maybe there's something funky w/ my keyboard, so I may go pick up a standard IBM keyboard today w/out all the bells and whistles.

I'll be doing that checkdisk command you supplied after I get back from class, thanks for that.

---

