---
title: "LVM Setup &amp; Configure"
date: 2014-03-07
forum: General Help
---

### Post by mbrown2441 on 2014-03-07
I have a laptop that is running Ubuntu 14.04. I have two or three external hard drives. I want to make them appear as one logical drive. I have been recommended to use LVM. My only question is that the only disk space I want to use is that of the three external hard drives and not of the hard drive that the O/S is running off of. The three disk sizes are shown below.

250GB
320GB
500GB

The 250 and 320 I do not care and I can reformat them if needed. The 500GB I have a bunch of data on that and was wondering do I have to format all three?

In addition, would I start the LVM steps on one of the external drives or on the local hard drive as that is where everything will be mounted to? 

Thanks for your help

---

### Post by Herman on 2014-03-08
There is a nice LVM Installation Guide in Ubuntu Community Help Wiki, called [SettingUpLVM-WithoutACleanInstall]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall"). I have not tried it and it looks like it could do with a few minor edits here and there to bring it up to date. I presume that's what you have in mind doing to get your existing installation into LVM first?
The linked web page also provides a link to another alternative option, using something called [blocks to LVM]("https://github.com/g2p/blocks"), which is supposed to be able to do an in-place conversion. 
I have not tried either of those, but you should be aware of them before making a decision about how you want to go about things. 

The simple way which most ordinary people would probably prefer would be to back up all of your data and re-install. 
You can re-install using the Ubuntu 12.04 'Alternate Installation CD'. The .iso for that can be burned to a CD and run in your computer and you can use it to set up LVM and install Ubuntu 12.10 in your computer. 
For more recent Ubuntu releases, starting with 12.10 there is LVM support in the Ubuntu 'Desktop' Live CD, and the 'Alternate Installation CD is no longer available. I don't know anything about 14.04 yet. You can set up LVM in your computer's hard disk during your Live session if you boot to the Desktop first. Set up your LVM before starting the installation. The Ubuntu installer in the 'Desktop' LiveCD is unable to create LVM during installation, but when you already have LVM set up prior to starting the installer you can select your logical volumes and install into them.

Once you have Ubuntu installed in LVM in your computer's hard disk then you can register partitions in other hard disks such as your USB external hard disks as PVs, ('Physical Volumes'), make them part of your volume group, (or 'VG'), and add them to your logical volume, (or LV). You don't need to format your entire disk if it already has a partition with a file system containing data. If necessary just resize the partition and make it smaller to leave some free space on your disk and create a new partition for a PV. As always, it's best to back up data before working on partitions.

These are just my ideas about how I would go about it if I were you, but LVM is very flexible and Ubuntu is too, so all kinds of other ways to do things would also work. You could make a fresh installation in one of your USBs first, and play around with LVM until you get used to it before doing a serious installation. It also won't matter too much whether you just keep the external USB Ubuntu and move the files from your internal HDD into it and later make the internal HDD part of your LVM. Be aware though, that reads and writes through the USB2 interface will slow your operating system down a little.

---

