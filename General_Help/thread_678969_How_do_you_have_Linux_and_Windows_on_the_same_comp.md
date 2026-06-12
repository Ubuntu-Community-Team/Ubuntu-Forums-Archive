---
title: "How do you have Linux and Windows on the same computer"
date: 2008-01-26
forum: General Help
---

### Post by gamemusician on 2008-01-26
I have installed Linux and  had Window XP on my computer first with lots of valuable data. I can't get back to my Windows XP stuff. All I have to use is Linux, but it's the stuff that's important. 

When I start up my computer I have 6 choices

Ubuntu 7.10, kernel 2.6.22-14-generic

Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

Ubuntu 7.10, memtest86+

other operating systems:

Windows XP Media Center Edition

Windows NT/2000/XP

When I choose Windows XP Media Center Edition it sits on a black screen that says "starting up..." at the top of the screen.

When I choose Windows NT/2000/XP it Goes to the PC recovery screen.

How do I get back my Windows stuff?

---

### Post by aysiu on 2008-01-26
Did you install Linux *over* Windows or *next to* it?

If it's the former, well, you may have to use a data recovery program to get your files back.

If it's the latter, did you defragment Windows before shrinking the partition to make room for Linux?

You may, once you boot into Linux, be able to mount your Windows drive and fetch the important stuff up. Just go to Places > Home, which should open the file manager. In the left pane, your Windows partition should appear, and you can double-click it to mount it and have your Windows files available to you.

P.S. I know it's too late for you, but for other new users read this thread: **this** is why you should always back up before installing a new operating system.

---

### Post by CCNA_student on 2008-01-26
Aysiu is right, I think your Windows partition is useless now. You may be able to access the partition from the Linux side and put all of your important files on a DVD or a flash drive. It appears that some important file like ntoskernel.dll or boot.ini was lost when you did the partitioning. You have your Windows recovery or installation disc, and backed up all of your important data right? You will have to reinstall Windows now if you want to use Windows still.

    Sin Cere,

    CCNA

---

### Post by aysiu on 2008-01-26
> **CCNA_student said:**
> You will have to reinstall Windows now if you want to use Windows still. Please note that if you reinstall Windows, you won't be able to boot into Ubuntu, as the Windows boot loader will overwrite Ubuntu's (Grub) boot loader.

If you have enough RAM (say 1 GB or more), you might want to install Windows as virtual operating system inside Ubuntu using virtualization software like VirtualBox or VMWare.

---

