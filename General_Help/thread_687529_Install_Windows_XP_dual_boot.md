---
title: "Install Windows XP dual boot"
date: 2008-02-04
forum: General Help
---

### Post by timboellis on 2008-02-04
Unfortunaty I need to use windows for some project work I am doing however I have Ubuntu Installed on my drive just now.

However i need to install Windows XP whats the best way to do this, I can do it the other way round.

Any help

---

### Post by slibuntu on 2008-02-04
As far as I know, since Windows likes to overwrite the MBR when installing, it's a tricky operation, if you have your home directory on a seperate partition to your installation, the quickest way may be to install Windows and then reinstall Ubuntu, although I'd love to be proved wrong if anyone else has a better idea

---

### Post by timboellis on 2008-02-04
I think I may just slip in another hard drive and take my Ubuntu one out

---

### Post by slibuntu on 2008-02-04
If you have a spare one lying around, sure. Have you tried running the applications you need under WINE?

---

### Post by Borbus on 2008-02-04
Or just use VirtualBox or VMWare and run Windows in a virtual machine. If you have a modern CPU with either Intel VT or whatever AMD's one is then it runs just as fast as a native OS.

---

### Post by timboellis on 2008-02-04
Yes I have it is for a website I manage I need to do a 360 view, floorplan, walkthrough with Java and as 90% of the visitors to the site are windows based have to configure it for this.

So need flash, Java , a 360 software manager no software exists for Linux as it is a very closed software distro.

But as soon as it is done back to Ubuntu , not looking forwads to it at all

---

### Post by geo909 on 2008-02-04
Hello timboellis,

well, when you install windows on a separate partition or another hard drive when you already have Ubuntu installed, windows will overwrite GRUB menu, the one you choose between kernels etc after you boot your PC. 

** That doesn't mean that the installation of Ubuntu will be altered**: everything will stay as is, you just need to reinstall GRUB. That's a tricky operation indeed, but not so difficult after all, you will need a live CD (assume you have one since you have ubuntu already installed) and a few commands typed..

 Don't know how convenient you feel with the terminal. Anyway, follow the link below:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

and choose "Using the Desktop/LiveCD and Overwriting the Windows bootloader".

It's pretty clear, I think...

---

### Post by geo909 on 2008-02-04
OOps, sorry I forgot..

How many disks have you on your system?

 If you have one with Ubuntu on it and you are able to add another one that you will install windows on it then this operation will be really easy..
 
 Or maybe you could partition it with a tool such as gParted, but I really don't know if this will alter the Ubuntu installation (quite possible-I haven't tried it).

 On the other hand, if you have a fresh installation of Ubuntu with nothing on it and you don't really mind to lose your settings/configuration stuff, it's not a bad idea to make a full-disk installation of windows and install Ubuntu afterwards (the classic dual-boot installation).

---

### Post by timboellis on 2008-02-06
Thanks for alll the support I got it working without any interuption on my main Ubuntu drive

I removed my Ubuntu Drive installed an old 80 gig HDD installed Windows.

Then I put in my ubuntu drive as master and my XP drive as slave(Irrellevant which way) and then set the computer bios to ask what drive to boot from on each ocassion so I can choose maxtor(Ubuntu) or Hitchi(Windows) and the 3rd drive is just my backup drive which I installed Linux read write to the drive on Windows.

So all peachy.

---

