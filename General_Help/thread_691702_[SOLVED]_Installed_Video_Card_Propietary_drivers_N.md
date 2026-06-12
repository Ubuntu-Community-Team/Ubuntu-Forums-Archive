---
title: "[SOLVED] Installed Video Card Propietary drivers Now just a blank screen"
date: 2008-02-08
forum: General Help
---

### Post by Sabar on 2008-02-08
Followed the directions found in my Ubuntu 7.10 Linux unleashed book. Starting to think it was a mistake. 

I used the restricted drivers manager to load my ATI proprietary drivers just to see if I would see any difference. Well I have. Now after the splash all I get is a blank screen I Did restart in recovery mode and all I got was  

> root@alien:~#

Is there something I can do here to disable the proprietary drivers? so I can get my computer back with out reformatting? 

what is Memtest86+ ??

Thanks for any help you guys can give me

Sabar

Goes to show just because some one printed it in a book doesn't make it a good idea

---

### Post by Sabar on 2008-02-08
Just found [This Post]("http://ubuntuforums.org/showthread.php?t=517225&highlight=remove+proprietary+drivers") So If I started computer in safe mode and after root@alien:~# Typed in sudo apt-get remove xorg-driver-fglrx What would that do?

> root@alien:~# sudo apt-get remove xorg-driver-fglrx Typed it in just like that?

I really do not want to reformat.

---

### Post by pointone on 2008-02-09
That would remove the ATI proprietary driver.

What video card are you using?

---

### Post by Sabar on 2008-02-09
I am using an ATI Radeon X550 256mb PCIE Graphics Processor

When I opened the window to add proprietary drivers it showed the ATI I think. I dont know why it messed up so badly, and the Window X? thing never came up. 

So what I said in my previous post should do it maybe?  Just type in exactly what I have?

Thanks for the response
Sabar

---

### Post by pointone on 2008-02-09
There should be numbers after the X, as in ATI Radeon X1400, or ATI Radeon X3850. This is the important part.

Uninstalling fglrx is probably a good place to start. Run the command you typed above and see what happens.

---

### Post by Sabar on 2008-02-14
ok to get things working again I just typed 

> root@alien:~# sudo apt-get remove xorg-driver-fglrx

Take note that it is FGLRX in small letters. The L got me at first I thought I was looking at an I. 

Then I rebooted and was greeted with Ubuntu in safe mode. all I did was go to system>administration>Restricted drivers manager> clicked on disable drivers and now everything works great

Thank you every one who posted. hopefully some day this can help some one else.
Sabar

---

