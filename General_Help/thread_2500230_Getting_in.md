---
title: "Getting in"
date: 2024-08-26
forum: General Help
---

### Post by keltkitty on 2024-08-26
I start my Win11 Surface laptop, draw up the Ubuntu icon in the start menu and the classic black screen appears with some DOS looking words and my laptop name written in green and :~$  I've typed in a few things and gotten a mess of codes I know nothing about. What do I type in to bring up Ubuntu as I get on the OLD slow laptop  I own?

---

### Post by deadflowr on 2024-08-26
I guessing you installed Ubuntu from Windows App Store?
Then it would be what is known as WSL (Windows Subsystem for Linux)
By default it is only a command line interface.

So long story short, what you see is Ubuntu.


I guess there are ways to run it with a graphical interface...

---

### Post by keltkitty on 2024-08-26
Yes, I could not get Ubuntu in there beyond the download, so had to go through the Windows thing, and then Linux. I did get into the BIOS and update the virtual machine platform, and it does tell me it's Ubuntu in the DOSy script, but nothing manageable by me. I really want a useable Ubuntu to come up and then find a way to kick MS completely out of the laptop. How to I set up the graphical interface which will let me actually use Ubuntu? I just found a reference to "Gnome Desktop" GUI. Is that a good one to install? And is it best done via Win or Linux?

---

### Post by yancek on 2024-08-26
>  I really want a useable Ubuntu to come up and then find a way to kick MS completely out of the laptop 

If you are using WSL (windows subsystem for LInux) that won't work because it is basically virtualization software run from windows and is similar to something like VirtualBox or VMWare.  If you want to replace whatever version of windows you have with Ubuntu you need to download the Ubuntu desktop iso file from the Ubuntu site, write it to a USB stick and boot the USB to install.  If you have not installed UBuntu directly on hardware, it would be a very good idea to go to the Ubuntu site and read up on installing it and maybe go through a few tutorials on the same until you understand the process.

Did you download the Ubuntu Desktop iso?  As far as I know, only windows 11 allows a graphical interface with WSL.

---

### Post by keltkitty on 2024-08-26
I did download the iso, but couldn't get to BIOS to order the boot to come from the USB. Now that I have found a way into BIOS I shall try what you are suggesting. Thanks.

---

