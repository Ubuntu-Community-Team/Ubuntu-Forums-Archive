---
title: "Ubuntu 10.04 - Unable to boot from live CD"
date: 2013-02-15
forum: General Help
---

### Post by Mr Kipling on 2013-02-15
I have screwed up my Ubuntu 10.04 install be deleting essential packages.

When I boot from 12.04 live CD I get the error: 
No boot device available, Press ENTER key to retry

Grub also won't load, I get the error: 
Error 15: File not found.

The Ubuntu live CD does work, I have tried it on another PC.

Using a CentOS CD I don't get the "No boot device available..." error message and can get to a command line and use apt-get to install packages. However it is so broken it really needs a fresh install.

Why won't the Ubuntu live CD  work and the CentOS one will?

Is there a way to get the Ubuntu CD to boot? I don't want to install CentOS and then install Ubuntu after.

---

### Post by blazemore on 2013-02-15
Your computer probably isn't set to boot from the CD.

You need to go into your BIOS settings and make sure it's trying to boot from a CD BEFORE it tries the hard-drive.

---

### Post by Mr Kipling on 2013-02-15
It is definitely  booting from the CD. It boots OK from the CentOS CD. But comes up with this error with the Ubuntu CD.

---

### Post by oldfred on 2013-02-15
Error 15 is a grub legacy error. Did you have grub legacy on hard drive?

Did you correctly download and install to CD/DVD/Flash drive? If you can boot from flash drive that is reusable and runs quicker than CD.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Mr Kipling on 2013-02-15
The CD doesn't seem to be the issue.

My feeling is that the boot sector is corrupted and for some reason the Ubuntu CD tries to read from this where as the Centos CD doesn't.

For my latest attempt I have a Ubuntu 10.04 CD which allows me to get to the install stage bit then does nothing, except show a blank screen.

---

### Post by oldfred on 2013-02-15
I think Ubuntu CD was issue.

 If CD is not correctly bootable system will default back to MBR of hard drive which then had grub legacy. 

Your other two CD are configured correctly to boot so they work.

---

### Post by Bufeu on 2013-02-15
Tried boot from an USB flash drive. Worked for my friend's computer.

---

### Post by Mr Kipling on 2013-02-16
There was an issue with the CD, although it could be read from the CD drive and booted there were errors reading from it. I found this when doing ctrl+alt F6 to reveal the text output. 

I created the CD again from an iso using a slow burn speed and a good quality disk, it now works.

I can reformat the disk and install or install side by side or manually partition, how do I repair the install, there doesn't seem to be the option?

---

### Post by mörgæs on 2013-02-16
Don't waste time repairing a 10.04 installation, as it is reaching end of life in two months:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

A fresh install of 12.04.2 or 12.10 is a better option.

---

### Post by Mr Kipling on 2013-02-16
I wanted to keep my home dirs if possible.

My idea was to repair then upgrade from 10.04 to 12.04 LTS.

---

### Post by oldfred on 2013-02-16
Still a good idea to backup /home.

Do you have 10 to 25GB available on drive? You might just want to put a new install into a new / (root) partition so you can do more than just test drive with the live version.

You should be able to chroot into your install and run repairs.

But if just a booting issue this may help.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Mr Kipling on 2013-02-19
I opted to install 12.04 in the end.

The issue with the cds turned out to be a faulty CD drive.

Thanks for all the comments and help.

---

### Post by mörgæs on 2013-02-19
Good, please mark the thread 'solved'.

---

