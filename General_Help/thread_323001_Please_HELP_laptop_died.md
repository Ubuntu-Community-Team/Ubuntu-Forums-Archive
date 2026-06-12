---
title: "Please HELP laptop died"
date: 2006-12-21
forum: General Help
---

### Post by Korrontean on 2006-12-21
Hi, this is my first post in the Ubuntu Forums.

I had succesfully installed Ubuntu 6.06. As I was very optimistic about Ubuntu, I decided to install it without the double boot, deleting everything in the computer and forgetting Windows.

However, it was being impossible for me to access the Internet, so I inserted the standard recovery CDs that came with my laptop (Acer Aspire 3500) and completed the process in order to re-install Windows. No questions were asked, just when it had completed "recovering the hard disk" and was going to start with Windows (already 3 recovery CDs inserted and read), it is blocked.

Now I turn the computer and all I get is

"GRUB loading stage1.5.

GRUB loading, please wait...

Error 17"

I find it weird, as I thought the Acer official CD's had deleted everything in the disk, including the Lynux stuff. And it doesn't react at all, even when I boot with the Lynux CD inside.

I'd appreciate anyone giving me some advice. I have a Windows desktop computer (from which I am writing), with full access to the internet and also a USB portable hard disk. I hope this will help.

THANK YOU VERY MUCH

Desperate Jon

---

### Post by Ambimom on 2006-12-21
Try this: 

 [http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)

You need to recover the master boot record.

Good luck.

---

### Post by Robert.Zapata on 2006-12-21
Jon:

For recovering the MBR, load from a DOS CD or floppy and do a: fdisk /MBR

Be sure your Acer machine is fully compatible with Ubuntu, lots of time is tricky to make Ubuntu work in notebooks.

P.S. Feliz Navidad y prospero ano nuevo..!!

Saludos al Sub Marcos..!!

---

### Post by Korrontean on 2006-12-21
Thank you very much - MUCHAS GRACIAS to both.

First solution didn't work, as I my laptop refuses to boot from a Windows XP/Ubuntu CD.

For the second one, how do I "load from a DOS CD or floppy and do a: fdisk /MBR"?

I haven't got a floppy. What is a DOS CD?

THANK YOU....I think I overestimated my computer skills when I started to switch to Ubuntu - even if everyone says anyone can do it :-(

Jon

(le daré saludos al Sup cuando regrese a Chiapas en enero, de momento estoy de vacaciones en mi tierra, en Europa)

---

### Post by ardvark71 on 2006-12-21
> **Korrontean said:**
> Thank you very much - MUCHAS GRACIAS to both.

First solution didn't work, as I my laptop refuses to boot from a Windows XP/Ubuntu CD.

For the second one, how do I "load from a DOS CD or floppy and do a: fdisk /MBR"?

I haven't got a floppy. What is a DOS CD?

THANK YOU....I think I overestimated my computer skills when I started to switch to Ubuntu - even if everyone says anyone can do it :-(

Jon

(le daré saludos al Sup cuando regrese a Chiapas en enero, de momento estoy de vacaciones en mi tierra, en Europa)

Hi, 

Can you get into your system's BIOS and verify the boot order?

Booting from CD shouldn't be a problem:confused:

---

### Post by Korrontean on 2006-12-21
Yeah, I had just found that solution (changing boot order), and I am back again fighting in Ubuntu.

THANK YOU VERY MUCH!!!

Jon (a happy man discovering the advantages of a great support community)

---

### Post by Robert.Zapata on 2006-12-21
> **Korrontean said:**
> I haven't got a floppy. What is a DOS CD?




Jon: Please not offense intended...How old are you..?? In the old times *(mid 80's)* before Windows OS. Computers used to work with DOS *(Disk Operative System)* that was based on only text on the screen, like when you go to the console using the terminal program. A DOS CD, is a CD that will allow you to boot your machine in DOS and be able to issue comands to do specific tasks.

Hope this link helps:

[http://club.cdfreaks.com/showthread.php?t=102301](http://club.cdfreaks.com/showthread.php?t=102301)

Once you boot the machine in DOS, issue the "fdisk" command as explained above.

---

### Post by vidak on 2006-12-21
Your laptop shoud possibly work with Ubuntu - I got also an Aspire, and (almost) everything works out of box... Check out the forum - there should be a solution for all the mentioned problems

---

### Post by Korrontean on 2006-12-21
Haha, of course I am not offended :) .

I am 25 and I got to know DOS. I even learnt some Basic. What I didn't understand was how to burn a CD to boot in DOS. Even if I remember the old files autoexec.bat and config.sys (is that correct?).

However my "big" problem was solved by changing the boot order. Now I am trying to connect to the internet. That's another story...


THANK YOU!

---

