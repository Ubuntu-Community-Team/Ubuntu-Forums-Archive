---
title: "Need advice with Grub..."
date: 2014-08-09
forum: General Help
---

### Post by Mike_Walsh on 2014-08-09
Afternoon, all.

I need a little bit of advice with Grub.

My system specs are as you see at the bottom of this post. I'm running Ubuntu 14.04 LTS, and Zorin's Core OS 9 (the new release, based on 14.04).

I have a 500 GB Seagate external Expansion drive. I've set up half-a-dozen or so small partitions, as I have a few different distros I would like to 'experiment' with.

My question is this:-

How do I set things up so that the Grub menu will not only access my main dual-boot installations, but also the other distros I want to install in the new partitions on the external drive?

I've been using Linux for about 4 months now. I'm finding my way round quite nicely, including (slowly!) getting the hang of the terminal, and also setting up partitions, etc, but I'm still a relative newbie, so.....any advice would be appreciated, please.

Regards,

Mike.

---

### Post by grahammechanical on 2014-08-09
My experienced is based almost exclusively with Ubuntu and its flavours but I suggest that you keep a few things in mind.

1) the last Linux distribution installed will install its boot loader and that will claim control of the boot menu.

2) On Ubuntu the installer defaults to installing Grub into the MBR/UEFI of sda. This might also be true of other Linux distros.

3) Select a distro to keep in charge of the boot menu. If it is Ubuntu 14.04 then after installing other distros load Ubuntu and run these two commands

```
sudo update-grub
sudo grub-install /dev/sda
```

The update of grub will detect any new OS. The installing of Grub will put 14.04 back in charge of the boot menu. It will be the first item on the boot menu.

4) When installing distros on that other hard disk (sdb) make sure that the boot loader is installed on sdb and not sda.

5) use the BIOS/UEFI to change the boot priory between sda and sdb to do the first re-boot of the new install or carry out point 3 and run those two commands and then re-boot and select the new OS from the updated Ubuntu Grub boot menu.

I have two hard disks. I have my daily use Ubuntu on sdb which has boot priority. In test installs of Ubuntu and its flavours I put the installations on sda and then I do item 3 on this list. Of course, I install Grub into sdb on my system. The principle is the same.

6) If a new install on the external hard drive puts its boot menu on sda and the external drive is disconnected then you will not be able to boot Ubuntu or Zorin because the boot loader is looking for its configuration files on the external disk. So, point 4 is very important when using an external hard disk.

Consider testing the development versions of Ubuntu and its flavours. This is where to get the daily images of Utopic Unicorn

[http://iso.qa.ubuntu.com/qatracker/milestones/315/builds](http://iso.qa.ubuntu.com/qatracker/milestones/315/builds)

Regards.

---

### Post by Mike_Walsh on 2014-08-09
Afternoon, Graham.

Thank you for taking the time to reply.

[ATTACH=CONFIG]255350[/ATTACH]
[ATTACH=CONFIG]255352[/ATTACH]

I've included screenshots of both drives, to hopefully make it more obvious what I'm intending to do.

For now, I want to install Lubuntu 14.04, Xubuntu, and Kubuntu; also, Pc Linux OS and maybe 'Precise' Puppy 5.7.1...not sure about that last one, as Puppy tends to be set up for flashdrive installation.

As you can see, most of the distros are members of the 'buntu family. I might include Mint, too.

The external HDD on my system is a PERMANENT fixture, even though it's USB. I have it 'Blu-tacked' to the top of my tower, and the only time it gets disconnected is during maintenance, when the machine is shut off anyway.

Do I understand you correctly; that new installs on sdb will probably move Grub TO sdb, although sda will still be accessible after running the terminal update commands?

I assume the second one tells Grub which HDD is in overall charge of the boot menu, yes?

Regards,

Mike.

BTW, I might consider trying 14.10...thanks for the information!

---

### Post by grahammechanical on 2014-08-09
If those distros use the Ubuntu installer (Ubiquity) then Grub will be installed by default into sda. Unless we direct it to sdb. In Ubuntu Grub looks into /boot to find the Linux image to load. 

In my way of working I have a Grub in sdb that looks for its files in /boot of Ubuntu on one of the partitions in sdb. I use sda for test installations because it is the smaller of my two drives. I allow the new install to put grub into sda. With this method if the hard disk sdb breaks I can change boot priorty to sda and still have a working OS. Likewise If hard disk sda breaks. But if I allow every install, whether to sda or sdb, to put Grub into sda, then if sda breaks I have a broken computer.

So, my suggestion to you is to make sure that these test installations that you are putting on sdb are putting Grub onto sdb and not sda. Which they will do if you do not stop them.

The command update-grub is actually a script. It runs a Grub utility called grub-mkconfig which creates the Grub configuration file called grub.cfg that is used to create the boot menu. grub.cfg is made up from several scripts. One of which is os-prober. So, running update-grub will detect any new OS that has been installed. And it will update the boot menu.

There is another thing to consider. When an existing test installation gets a kernel update then update-grub is automatically run. So, not allowing those test installs to control Grub in sda will stop them removing 14.04 from the top of the boot menu. But after the kernel has been updated to use that kernel you will have to either change boot priority to sdb or run update-grub from 14.04 on sda and then reboot and use the updated boot menu.

Regards.

---

### Post by Mike_Walsh on 2014-08-09
Thank you, Graham...much obliged to you.

Very concisely and clearly put; I'll marked this as 'Solved', since you've certainly answered the question.

Regards,

Mike.

---

