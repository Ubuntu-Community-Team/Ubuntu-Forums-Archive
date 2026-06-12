---
title: "Transfer files from linux to sony ericsson cellphones"
date: 2008-07-06
forum: General Help
---

### Post by a.dehqan on 2008-07-06
In the name of god
Hello

I will be Thankfull if you guide me ;
Is any software to transfer data such files , from linux to sony ericsson cellphones ?
Like pc suite but be a linux based ?

Thanks

---

### Post by rraj.be on 2008-07-06
I am too using sony Ericsson's mobile.

You don't need any such packages for you mobile phone.

just connect it via usb cable or vial blutooth and you can easily transfer your files.

Further you can just post here if you have any problems still;

---

### Post by inca99 on 2008-09-15
Hi, I'm having trouble transferring to my K800i. I can connect via bluetooth without issue and can browse my phone and memory card, however when I try to copy files I receive the following error,

There was an error copying the file into obex://[00:16:B8:99:56:A8]/Memory%20Stick/Music/My%20Music/MOS/The%20Mash%20Up%20Mix%202005/CD1.

Show more details

Operation not supported by backend

Any ideas?

---

### Post by Bops on 2008-12-27
I have the problem that when I put my C905 on mass-storage mode and it's connected I don't see my merory card anywhere on my Ubuntu-box.

But Ubuntu finds the phone.

lsusb gives me:

Bus 003 Device 003: ID 0fce:e0ef Sony Ericsson Mobile Communications AB 
Bus 003 Device 002: ID 14aa:0221 AVerMedia (again) or C&E AVermedia DVBT Tuner Dongle
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


But why can't I see the card anywhere??

---

### Post by chairmeleon on 2009-01-19
I'm copying a solution to this problem that I posted in my blog earlier Applies to Sony Ericsson C905 and probably other recent SE phones:

**1.** Open up a terminal window (i.e Gnome Terminal or Konsole)
[B]
2.[/B] Change directory to the one containing udev rule files, by typing:
*cd /etc/udev/rules.d/ *and pressing return.
[B]
3.[/B] Download the rule file by entering wget [http://arch.uhl.nu/60-persistent-storage.rules](http://arch.uhl.nu/60-persistent-storage.rules) and pressing return. **On Ubuntu 8.10 this file is already present, so you may have to remove the original by entering ***rm 60-persistent-storage.rules* [B]before doing the above.
[/B]
**4. **Reboot and enjoy!

The steps above were tested and confirmed working on Arch Linux with kernels 2.6.27/2.6.28 and Ubuntu 8.10 with kernel 2.6.27

---

### Post by hyper_ch on 2009-01-19
works fine on my K800i when I select data transfer mode when I hook it up through USB.

---

### Post by mangurt on 2009-01-21
Thank you very much!!!  This worked flawlessly with my sony ericsson w760a phone!!!

---

### Post by binbash on 2009-01-22
you can use your card as a storage manager (if your phone supports this) or you can send them via bluetooth

---

### Post by fedoraboy on 2009-04-28
> **chairmeleon said:**
> I'm copying a solution to this problem that I posted in my blog earlier Applies to Sony Ericsson C905 and probably other recent SE phones:

**1.** Open up a terminal window (i.e Gnome Terminal or Konsole)
[B]
2.[/B] Change directory to the one containing udev rule files, by typing:
*cd /etc/udev/rules.d/ *and pressing return.
[B]
3.[/B] Download the rule file by entering wget [http://arch.uhl.nu/60-persistent-storage.rules](http://arch.uhl.nu/60-persistent-storage.rules) and pressing return. **On Ubuntu 8.10 this file is already present, so you may have to remove the original by entering ***rm 60-persistent-storage.rules* [B]before doing the above.
[/B]
**4. **Reboot and enjoy!

The steps above were tested and confirmed working on Arch Linux with kernels 2.6.27/2.6.28 and Ubuntu 8.10 with kernel 2.6.27


No worky for me: w760a, ubuntu 8.10 2.6.27.

I don't get a /dev entry at all.  dmesg says:
[ 1828.844643] usb 3-1: new high speed USB device using ehci_hcd and address 3
[ 1828.981067] usb 3-1: configuration #4 chosen from 1 choice
[ 1853.796224] drivemount_appl[7323]: segfault at 0 ip 0000000000000000 sp 00007fff8dccccd8 error 14 in drivemount_applet2[400000+8000]

---

### Post by demersal on 2010-01-08
i have a c905 and im running ubuntu 8.10 in the past it has only allowed me to drag and drop music files to the phone but dose not recognize my sd card and only allows me to load files less than 84mb. now its not showing the files on my card at all. f-spot gives me various errors. i tried the posted solution but it comes back "no such file or directory" help? any1 have a pre connect command for amarok?

carlos@Carlos:~$  rm 60-persistent-storage.rules
rm: cannot remove `60-persistent-storage.rules': No such file or directory
carlos@Carlos:~$ cd /etc/udev/rules.d/
carlos@Carlos:/etc/udev/rules.d$ [http://arch.uhl.nu/60-persistent-storage.rules](http://arch.uhl.nu/60-persistent-storage.rules)
bash: [http://arch.uhl.nu/60-persistent-storage.rules:](http://arch.uhl.nu/60-persistent-storage.rules:) No such file or directory
carlos@Carlos:/etc/udev/rules.d$

---

### Post by aaronwinborn on 2010-01-24
> **demersal said:**
> 
carlos@Carlos:/etc/udev/rules.d$ [http://arch.uhl.nu/60-persistent-storage.rules](http://arch.uhl.nu/60-persistent-storage.rules)


try 

carlos@Carlos:/etc/udev/rules.d$ wget [http://arch.uhl.nu/60-persistent-storage.rules](http://arch.uhl.nu/60-persistent-storage.rules)

---

