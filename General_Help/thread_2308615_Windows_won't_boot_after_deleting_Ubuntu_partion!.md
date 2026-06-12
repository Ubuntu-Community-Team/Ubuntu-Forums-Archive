---
title: "Windows won't boot after deleting Ubuntu partion!"
date: 2016-01-04
forum: General Help
---

### Post by Seanan on 2016-01-04
Okay I know you guys are probably thinking that i am a stupid for not looking if this topic has been already posted, and it has and I have checked, but this is slightly different. So i did the same thing that everyone else did with this issue to get here: after deleting ubuntu partitions from Windows and rebooting an error shows up. And this is what it says (here's the difference) 
error: no such partition 
entering rescue mode
rm rescue>

WTF is rm rescue?:shock:
As far as i know Ubuntu uses a grub bootloader correct?
Also i have no access at the moment to a Window recovery disk and i was running Windows 8.1 OEM <-- Note this OEM version was installed by me on a desktop (also put together by me).
And the BIOS is perfectly accessible.
How can I boot up Windows again and fix this?
Help!

---

### Post by QDR06VV9 on 2016-01-04
**[SIZE=2]Fix the Windows Boot Loader[/SIZE]**

[FONT=-apple-system][SIZE=2]Linux has now been removed from your computer, but its boot loader persists. _**We’ll need to use a Windows installer disc to overwrite the Linux boot loader with the Windows boot loader.**_[/SIZE][/FONT]
[FONT=-apple-system][SIZE=2]If you don’t have a Windows installer disc lying around, you can create a Windows repair disc and use that instead. Follow our instructions to [create a system repair disc in Windows 8]("http://www.howtogeek.com/131907/how-to-create-and-use-a-recovery-drive-or-system-repair-disc-in-windows-8/") or[create one in Windows 7]("http://www.howtogeek.com/howto/5409/create-a-system-repair-disc-in-windows-7/").
I think this has one that works 
[/SIZE][FONT=Verdana][https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)
More info here
 [/FONT][FONT=Verdana][http://lifehacker.com/5403070/easybcd-makes-tweaking-your-windows-bootloader-a-snap](http://lifehacker.com/5403070/easybcd-makes-tweaking-your-windows-bootloader-a-snap)
Making a Windows repair Disk should be the second thing to after the first start-up.
Regards[/FONT][/FONT]

---

### Post by grahammechanical on 2016-01-04
It might be useful if we understood why this situation develops.

The Linux boot loader is installed in the MBR of the hard disk but it looks for its configuration file on the Ubuntu partition. Specifically, it looks to /boot/grub/ for grub.cfg.

Delete the Ubuntu partition & we delete grub.cfg and when Grub loads it dumps us at a Grub rescue prompt where we have an opportunity to point Grub in the right direction. But of course, in this situation there is no right direction any more.

rm = rescue mode?

---

### Post by Seanan on 2016-01-04
Problem is i don't have another machine running windows so i can't create a recovery disk

---

### Post by Seanan on 2016-01-04
Oh i dont have the Windows installer disk ethier

---

### Post by jim_deadlock on 2016-01-04
The quickest way for you to get up and running in this situation is to simply reinstall Ubuntu and then grub will let you boot Windows. Then you can spend time at your leisure finding a Windows recovery disk or whatever you need to reinstall MBR after removing Ubuntu again.

---

### Post by Seanan on 2016-01-05
Thanks i have a ubuntu boot disk and I will try that, but am wondering if it will make a difference because i originally installed ubuntu using ubuntu desktop to dual boot Windows.
Thanks for your help

---

### Post by jim_deadlock on 2016-01-05
You will need to boot the Ubuntu Live DVD and install Ubuntu onto your hard disk. Grub will be installed as well and it should automatically find your Windows partition and allow you to dual boot again like before. So in other words it will put you back to the position you were in before you removed Ubuntu.

---

### Post by Seanan on 2016-01-05
Thank you. Your help was appreciated and very helpful. I will let you know the results when i am done.

---

