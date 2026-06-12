---
title: "Stuck on GNU GRUB after deleting Winds ows and Ubuntu"
date: 2016-05-27
forum: General Help
---

### Post by jasonchiu2 on 2016-05-27
Guys I really need help please.

I've always been a big fan of ubuntu. Last week I uninstalled Windows the Ubuntu set up. Then this week I decided to install Windows, because I need it for work. But now I'm stuck on this screen titled "GNU GRUB". What should I do now?

I really can't afford to pay for a new laptop, I don't know that uninstalling stuff like that could destroy everything. Please help.

Edit: I tried typing reboot and pressed f12 in the Lenovo loading screen. Then I tried every options, it will either go back to the same screen or says Windows boot manager failed.

---

### Post by grahammechanical on 2016-05-27
I have very little experience of installing Microsoft Windows but one of the few things I do know from experience is that it is usual practice for the Windows installer to install the Windows boot loader on to the hard disk. So, I do not see why you are having this problem.

I do not understand what you mean by this

> I uninstalled Windows the Ubuntu set up.

Did you install Ubuntu inside Windows by installing wubi.exe? We install wubi.exe just like any other Windows program and we uninstall it just like any other Windows program. Is this not done using Add/Remove programs? Or something like that.

Did you re-install Windows or restore Windows? Did you restore Windows from a restore point that was made before using wubi.exe to install Ubuntu?

As you can tell, I am having to take wild guesses in the hope that one of them is accurate.

Regards.

---

### Post by jasonchiu2 on 2016-05-27
First of all, big thanks for replying me man, have me some relief :)

Sorry I didn't clarify it. I install Ubuntu from downloading the Ubuntu iso into my windows, then burning it into the disk. Next I reboot my pc from the disk. Throughout thr installation it asked me if I want to delete Windows, I deleted it. And now even though I have already burnt a Windows iso into a disk, it's still not working.

If you don't understand what I meant, it's fine man. I think I need to bring it down to the professionals anyway. Thanks though :)

---

### Post by yancek on 2016-05-27
Your initial post seems to indicate you are booting from the hard drive.  That's where the GNU Grub message is.  You need to enter the BIOS setup on the computer and set the DVD drive to first boot priority there so you boot from the DVD not the hard drive.

It isn't clear from your post whether you installed Ubuntu, doesn't seem like it.

> I don't know that uninstalling stuff like that could destroy everything

You indicate during the attempt to install Ubuntu, you deleted windows.  That was the entire windows operating system which DOES destroy everything.

If you have a windows iso burned to disk, what exactly happens?  "Not working" doesn't tell us much.  As a general point of information, when you are making posts like this, it is generally a good idea to mention which version of an operating system you are using whcih you don't do.  Microsoft has been writing operating systems for 30+ years!

---

### Post by oldrocker99 on 2016-05-27
If you're planning on dual-booting, install Windows FIRST, then Ubuntu, so the GRUB bootloader can see Windows and allow dual-booting. Windows doesn't see Linux and overwrites GRUB.

---

