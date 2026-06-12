---
title: "VirtualBox..."
date: 2007-08-19
forum: General Help
---

### Post by CM Xtasy on 2007-08-19
Ok so I'm thinking about switching to VMWare Server.

In VirtualBox, I installed my Windows XP Professional in it, and I have a few problems.  I can't install any display drivers because it has a different chipset than my computer, and the website doesn't even have any drivers for it, it doesnt read USB drives, and some CD's do not work.  Is there a solution to any of these, or should I just switch to VMWare Server and see how that goes?

---

### Post by scxtt on 2007-08-19
you won't ever be able to install drivers for your ACTUAL card in the VM - doesn't work that way ... maybe one day, but that day is not today ...

i've never had any USB/CDROM issues w/ my VMs - i use VMware Server.

---

### Post by HermanAB on 2007-08-19
It is virtual, meaning that the driver isn't real - it is whatever the VirtualBox people programmed it to be.  Think about it for a moment... :)

---

### Post by fjgaude on 2007-08-20
Running VMware by installing it with Synaptic is painless, and it's free. Very mature. Works with my PCI-E GeForce 7600 GS board and 64 X2 CPU, very fast. Everything works that i've tried... nothing to lose, give it a try.

Takes time getting a free serial number over the net; they ask lots of questions and all have to answered, else no SN.

Whole process, from downloading, installing, getting SN, took about 20 minutes. Took over an hour to install WinXP SP2. <sigh>

frank

---

### Post by chejose on 2007-08-20
Well, I just went the other way, leaving VM server for VirtualBox. I am much happier with VB.

But one important factor is that VB has an "add on"  package just like VM. Without it there are all kinds of problems, especially with video. My video problems were solved with that.

If you didn't install it, make a try.... it could be the solution.

José

---

### Post by fjgaude on 2007-08-20
> **chejose said:**
> Well, I just went the other way, leaving VM server for VirtualBox. I am much happier with VB.

Can you tell us what you didn't like about VMware? Thanks.

frank

---

### Post by chejose on 2007-08-20
Well, there were two things that complicated the use of VM server. I had Win 2k guest installed for a work program, and the matter of sharing files between host and guest was one I was never able to solve easily. With VB the two can have a shared folder.

And I could not run full screen with VM. It would always mess up my Ubuntu screen when I left the guest. But with VB the full screen mode works perfectly.

It is very possible that my situation is very personal, but since it was not possible to download VM - (at least when I attempted to do it) I happily ran into VB. For my application, at least, it is much better.

José

---

### Post by fjgaude on 2007-08-20
Okay, thanks for the reply... I've had none of the issues that you talk about. With my guest as WinXP I set the network to be "host only" between host and guest and use the Windows apps to simply point to all my data files on a raid5 array, files are saved there, no need for anything else. My raid is mounted on /home/raid on the host drive. Works quickly, very pleasingly.

Goes full screen and back without issues.

frank

---

### Post by eric_n_va on 2007-08-20
> **CM Xtasy said:**
> Ok so I'm thinking about switching to VMWare Server.

In VirtualBox, I installed my Windows XP Professional in it, and I have a few problems.  I can't install any display drivers because it has a different chipset than my computer, and the website doesn't even have any drivers for it, it doesnt read USB drives, and some CD's do not work.  Is there a solution to any of these, or should I just switch to VMWare Server and see how that goes?

Start your XP virtual machine, then on the title bar go to Devices-->Install Guest Additions.  This will load the windows drivers for the "virtual" hardware including display adapters and USB support.  Also for USB, (after you have the Guest Additions installed), shutdown your XP VM.  On the main innotek VirtualBox screen highlight your XP VM and click USB Controller on the Details tab.  Make sure Enable USB Controller is checked.  Now when you start XP and plug in usb drives you can click Devices-->USB Devices--> then click the drive you want to share with XP...

---

