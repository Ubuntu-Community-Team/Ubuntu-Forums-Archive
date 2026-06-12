---
title: "Dual boot from two different hard drives - ubuntu and centos"
date: 2012-10-17
forum: General Help
---

### Post by redhive on 2012-10-17
Hello everyone,

I am beginning to study for the RHCSA/RHCE  certifications - and trying to setup a studying environtment at home. I  am not an expert, but not a complete newbie either. Hope with practice  and lots of hard work I will be able to get there.

My first issue  is as follows: I have a pc with two different hard drives. In one, I  have ubuntu 12.4 64 bit installed - which I simply LOVE. The other hard drive will be used to  install centos 6.3. At the moment, this second hard drive has a trial  version of RHEL, and what happens is that when I boot the computer,  Ubuntu's grub doesn't "see" the RHEL installation on the other hard  drive and vice versa, RHEL's grub does not see the Ubuntu installation.  So each time I boot, I need to go to the BIOS first and choose with  which drive to boot first, depending on the system I want to use -  doable, but quite annoying.

Since I am going to be re-installing  the second drive with centos, I was wondering if anyone has advice on  how to avoid this problem, meaning, is there any way to make Ubuntu's GRUB recognize the other system and offer it as an option to  boot? If yes, can you point me in the right direction?

Thanks in advance for your help,

redhive

---

### Post by jerrrys on 2012-10-17
Not sure if this will help, but found ..

[http://ubuntuforums.org/showthread.php?t=1786895](http://ubuntuforums.org/showthread.php?t=1786895)

---

### Post by redhive on 2012-10-17
Thank you jerrrys, I will look into it more in depth, but from what I saw till now, not sure it will help me because I need dual boot from two different hard drives, and the thread you showed me is regarding dual boot from one single drive.

redhive

---

### Post by Gokutux on 2012-10-17
From ubuntu terminal type 
**sudo ./sh /etc/grub.d/30_os-probe** and then 
**sudo update-grub** 
this script of grub2 searches for os entries at drives. 
I'm not sure if this work but something like that is the solution...

---

### Post by PowerBarry43 on 2012-10-17
Hi

you should be able to make your ubuntu grub menu include any other distro on your pc by running

```
sudo update-grub
```from the terminal

this will definitely scan all devices for OSes as I've had it work for me with a Windows/Ubuntu dual boot system with my laptop and an external hard drive.

Hope this helps!

Barry

---

### Post by redhive on 2012-10-17
Thanks PowerBarry43 & Gokutux - I will try this once I get home and let you know how it goes. 

@PowerBarry43 - this should work even if the different OS are on separate hard drives ?

Very grateful for the help :-)

---

### Post by oldfred on 2012-10-17
The os-prober is good at finding other installs. But recently it has not been finding other installs that are in a LVM unless you load the lvm2 driver & mount the partition first.

sudo apt-get install lvm2

Grub2 uses a lot of loadable modules and it must not know to load the lvm module without a little help.

I have 4 drives and a sudo update-grub takes forever as I have a lot of old Ubuntu installs and it finds all of them. I turn off os-prober and just copy a few boot entries into my 40_custom to avoid menu overkill. New grub2 version 2 puts a lot of that into sub-menus so that is another change.

---

### Post by redhive on 2012-10-17
gotta love ubuntu and its community - problem solved guys! many thanks!

os-prober + update-grub did the trick for me, so many thanks PowerBarry43 and oldfred for the suggestions!

---

