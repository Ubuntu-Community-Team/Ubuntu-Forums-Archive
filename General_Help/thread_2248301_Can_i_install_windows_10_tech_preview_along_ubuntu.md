---
title: "Can i install windows 10 tech preview along ubuntu 14.04?"
date: 2014-10-13
forum: General Help
---

### Post by 0310aditya on 2014-10-13
My computer originally shipped with windows 7. I then switched to ubuntu 14 and made it my primary OS. Since windows 10 tech preview is now out i wanted to download it and play around with it a bit. So is this possible to install windows WITHOUT having to delete ubuntu (it has all my files) and install windows alongside ubuntu? I just want to make sure before i go ahead and download the iso image.

Cheers!

Jeremy

---

### Post by grahammechanical on 2014-10-13
You might be among the first to gain experience in doing that.

Based upon my experience in installing Windows 8 preview. It is possible to install Windows into its own partition but you will first have to use the installer to format the partition. Then the installer will let you proceed. An important point to remember is that the Windows installer will install the Windows boot loader on every hard disk. Which means that you will lose access to Ubuntu even if it is on another hard disk. I never expected that to happen but it did. So, be ready to use Boot Repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by andrew.46 on 2014-10-13
Such an early copy of the next windows release might be better in a Virtual Machine...

---

### Post by sudodus on 2014-10-14
Windows Technical Preview (WTP) 64-bit seems to need UEFI. I installed WTP into a separate small SSD (with no other drive connected except the install DVD disk). I used Windows to shrink its partition, and then I booted from an Ubuntu 14.04.1 pendrive and used gparted to make an ext4 partition and a swap partition. Finally I installed  Ubuntu.

The whole set of operations worked without problems, and the dual boot system needed no tweaks to work in my Toshiba laptop.

But I agree with andrew.46, that it might be a good idea to test it in a virtual machine. At least, you should avoid risks with your main (or only) computer.

---

### Post by 0310aditya on 2014-10-21
Sorry guys for not replying was REALLY busy...,

The only problem with doing that is that virtual machine tend to be a bit...slow. I have a windows 7 on virtualbox and the thing is that it is pretty slow but can run basic windows applications. The reason i want to install windows 10 onto my hard drive is because 1. My work requires windows applications to be run and i dont want to delete ubuntu as it is my main OS. 2. I generally want to try out windows 10. So my question is can a create a partition, install windows, and then use boot-repair to install GRUB bootloader to replace the windows bootloader. Will i be able to do that? 

Sorry for not replying,

Jeremy

---

### Post by westie457 on 2014-10-21
If I managed to post the correct screenshot of my current partitions /sda9 is Windows Technical Preview. Note that sda9 is a logical partition, the boot files are in sda2 along with the boot files for Windows 7.

Yes it is possible to install the Preview alongside another OS.
Windows 10 might prefer a GPT partitioned drive it is quite happy being installed to a MBR partitioned drive.

Boot Repair will be needed to restore Grub.

In my use case there is a weird issue when booting Windows 7 however I am not interested in sorting that out. I can live with it.

Hope you find this information useful.

---

### Post by 0310aditya on 2014-10-21
> **westie457 said:**
> If I managed to post the correct screenshot of my current partitions /sda9 is Windows Technical Preview. Note that sda9 is a logical partition, the boot files are in sda2 along with the boot files for Windows 7.

Yes it is possible to install the Preview alongside another OS.
Windows 10 might prefer a GPT partitioned drive it is quite happy being installed to a MBR partitioned drive.

Boot Repair will be needed to restore Grub.

In my use case there is a weird issue when booting Windows 7 however I am not interested in sorting that out. I can live with it.

Hope you find this information useful.

Thanks a lot for your help! So just for conformation all i need to do is 1. Create a partition 2. Install windows to a GPT or MBR drive 3. Use boot-repair to reinstall GRUB. Am i right?

Thanks again for your help,
Jeremy

---

### Post by yancek on 2014-10-22
I installed it today in Virtual Box because I don't want it interfering with booting other systems and just did it out of curiosity.  It needs a 25GB partition so if you plan to actually use it you should make it considerably larger.  Since it is still a beta release you can't really expect stability from it.  I installed the 32bit version so I'm not sure if the 64bit requires GPT/UEFI.  You should check that out before doing anything because if it does and you do not have Ubuntu installed with UEFI you are going to muck things up.  Things worked pretty much the way they are explained at the link below and the install went without any problems.  If you don't use VBox, it might still be a good idea to review the link below so you have some familiarity with what you will see in the installer.  

[URL="http://www.techrepublic.com/article/pro-tip-how-to-install-windows-10-technical-preview-in-virtualbox/"]http://www.techrepublic.com/article/pro-tip-how-to-install-windows-10-technical-preview-in-virtualbox/


[/URL]

---

### Post by 0310aditya on 2014-10-23
How to i see whether ubuntu is installed in uefi mode? Im pretty sure i installed it in uefi though...

---

