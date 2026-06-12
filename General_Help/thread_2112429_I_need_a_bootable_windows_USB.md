---
title: "I need a bootable windows USB"
date: 2013-02-04
forum: General Help
---

### Post by greatsirkain on 2013-02-04
to fix another computer, had no luck with winusb, unetbootin etc.
found an online guide or two but none worked which was nice.

I have a windows ISO that I tried to mount then install on a partition to use sardu to make the USB but got a 'mounted as read only' message

I ran a live version of winxp from a VM but I still couldn't create it

Is there like a simple drag and drop file I can put on the USB followed by the windows ISO to make it bootable?

I'm sure I've done it before but I've been up 48 hours straight and my heads spinning & not in a pleasant 'ooo so that's what happens when you down whiskey' kinda way

---

### Post by Cheesemill on 2013-02-04
Can you clarify a bit please.

Do you want a USB stick that will boot into the Windows installation process, or a USB stick that will boot into a live, running Windows installation?

What version of Windows is it?

I've used WinUSB plenty of times and never had any issues.

---

### Post by Habitual on 2013-02-04
[http://sourceforge.net/projects/unetbootin/files/UNetbootin/583/unetbootin-windows-583.exe/download?_test=updater&utm_expid=65835818-0&use_mirror=hivelocity&utm_referrer=http%3A%2F%2Funetbootin.sourceforge.net%2F](http://sourceforge.net/projects/unetbootin/files/UNetbootin/583/unetbootin-windows-583.exe/download?_test=updater&utm_expid=65835818-0&use_mirror=hivelocity&utm_referrer=http%3A%2F%2Funetbootin.sourceforge.net%2F)

---

### Post by greatsirkain on 2013-02-04
sorry I meant a bootable USB for installation of windows 7 to fix my cousins computer who wants me to format the drives & put then put the OS back on. Her DVD drive isn't working so I made an ISO of her disk to create a USB to use at her house.

I already have my own winxp live USB but it doesn't have persistence on it so I can't install sardu (which is what I've always used in the past for windows USB') to do it from there & I don't really want to install it onto my computer if I can avoid it. Running sardu with wine hasn't worked either :S

---

### Post by greatsirkain on 2013-02-04
> **Habitual said:**
> [http://sourceforge.net/projects/unetbootin/files/UNetbootin/583/unetbootin-windows-583.exe/download?_test=updater&utm_expid=65835818-0&use_mirror=hivelocity&utm_referrer=http%3A%2F%2Funetbootin.sourceforge.net%2F](http://sourceforge.net/projects/unetbootin/files/UNetbootin/583/unetbootin-windows-583.exe/download?_test=updater&utm_expid=65835818-0&use_mirror=hivelocity&utm_referrer=http%3A%2F%2Funetbootin.sourceforge.net%2F)

yup I got that but it's to make live linux usb'

---

### Post by Bucky Ball on 2013-02-04
*Thread moved back to **General Help** after clarification from OP and at their request.*

---

### Post by greatsirkain on 2013-02-04
The reason I posted it in general help is because I have to make it on lubuntu 12.04

---

### Post by Bucky Ball on 2013-02-04
See PM I sent you. You waited until post #7 to add this information so you will understand the confusion. ;)

---

### Post by Cheesemill on 2013-02-04
What problems are you having with WinUSB? It's always worked for me in the past.

---

### Post by C.S.Cameron on 2013-02-04
To make a Windows Installer using Ubuntu: 

Format the USB as NTFS using Gparted and set the boot flag.

Extract the contents of the Win 7 iso to the USB using Archive Manager.

That's it.

---

### Post by cpatrick08 on 2013-02-05
[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)

---

### Post by greatsirkain on 2013-02-05
> **C.S.Cameron said:**
> To make a Windows Installer using Ubuntu: 

Format the USB as NTFS using Gparted and set the boot flag.

Extract the contents of the Win 7 iso to the USB using Archive Manager.

That's it.


Thanks guys, one headache down, maybe I was having trouble because I'd formatted it to fat32?
and sorry for not being clear straight away but there was only caffeine keeping me upright last night :P

---

### Post by iamkuriouspurpleoranj on 2013-02-06
Here's how I have done it (works a treat):


[LIST]
[*]Format your USB as FAT32 in GParted
[*]Open UNetbootin and get it as far as the stage where it brings up the USB partition to install to e.g. /dev/sdb1 - Don't install the ISO, though
[*]Leaving UNetbootin open as is, reopen GParted
[*]Format the USB in GParted as NTFS
[*]If GParted doesn't automatically add the "boot" flag, add it yourself
[*]Now, go back to UNetbootin, which you've left open in the meantime, and click OK
[/LIST]

Without doing those extra steps, UNetbootin won't find the NTFS partition.

---

### Post by Bucky Ball on 2013-02-06
> **iamkuriouspurpleoranj said:**
> 
[*]Format your USB as FAT32 in GParted
[*]Open UNetbootin and get it as far as the stage where it brings up the USB partition to install to e.g. /dev/sdb1 - Don't install the ISO, though
[*]Leaving UNetbootin open as is, reopen GParted
[*]Format the USB in GParted as NTFS

The problem has been solved. But in response to your afterthought: wonndering why you would format the USB to FAT32 when in step 4 you format it as NTFS. Why wouldn't you just format it as NTFS in the first instance or leave it as free space and let UNetbootin do it?

---

