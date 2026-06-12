---
title: "How: replicate an installation on several computers"
date: 2006-12-11
forum: General Help
---

### Post by johann_p on 2006-12-11
I have Ubuntu Edgy installed on one of my computers, and I have changed a lot in comparison to the standard list of installed packages and configuration settings.

Now I would like to essentially do a fresh install on other computers, but with exactly the same packages installed, and with nearly all the configuration parameters duplicated there too. 

Other distros have was how to do an "auto-install" based on the saved settings of the installation/configuration tool (openSuse) or based on a file containing meta-information (e.g. system-config-kickstart under Redhat). 

How would one do this under Ubuntu? I do not want to mirror the harddisk per se ... I want to replicate the installation/configuration without actually mirroring the data and files.

BTW, there is a package for system-config-kickstart for Ubuntu, but it is so broken that it is totally unusable.

---

### Post by smoker on 2006-12-11
i think this would only work if all the computers had the exact same hardware and specs, if that is so, you should be able to create a disk image, and copy this to each computer. but any differences in hardware would cause problems.

---

### Post by johann_p on 2006-12-11
> **smoker said:**
> i think this would only work if all the computers had the exact same hardware and specs, if that is so, you should be able to create a disk image, and copy this to each computer. but any differences in hardware would cause problems.

No - I do not agree. The set of packages to install is completely hardware independent. And as for the configuration details, it would of course be necessary to specify which configuration details to transfer, e.g. running initscripts, but not the X11.conf stuff. 

The point is this: you would create one base configuration/installation and have the information about it on a small USB stick. Then you could install other computers, getting 90% of the things installed and configured automatically, doing only what is necessary to be done differently on each PC (probably not much more than the partitions and graphics hardware).

---

### Post by smoker on 2006-12-11
i think i understand what you mean, but is this not going to be a lot of work. unless, of course, you are talking about a lot of computers.

---

### Post by johann_p on 2006-12-11
Well I think it is already too much work for a single computer, my working time being precious AND expensive. As I said, this is not a new crazy idea by myself but something that has been used and works with other OS/distros for years now. I just wanted to know if it is also possible to do it with Ubuntu.

---

### Post by pandu.rs on 2006-12-11
you might want to have a look at my postings in this thread

[http://ubuntuforums.org/showthread.php?t=304746](http://ubuntuforums.org/showthread.php?t=304746)

---

### Post by klanman8908 on 2006-12-11
How do you make an image of the install?  I asked something similar to this in a different thread because I would like to use my own cutom kernel with out having to compile it on all the computers I plan on using it on.

---

### Post by johann_p on 2006-12-11
> **pandu.rs said:**
> you might want to have a look at my postings in this thread

[http://ubuntuforums.org/showthread.php?t=304746](http://ubuntuforums.org/showthread.php?t=304746)

Thanks ... that takes care of the packages to be installed, which is arguably the biggest chunk. I probably have edited a couple of config files since the original install, but I can't remember which, so I'll probably learn that the hard way.

Unfortantely, Linux does not really distinguish between true config files and stuff that could easily be re-generated. For example, my /etc directory contains more than 25MB! Of which probably just a few bytes of kB are actually important and to be remembered. 
There are probably a couple of other config files scattered in the file hierarchy that I a now forgot about ...

---

### Post by technodigifreak on 2006-12-11
This assumes that your data is on a seperate partition.

Partimage ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)) which is integrated into the SysRescueCD ([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) is perfect for what you are describing.  Make an image of the system partitions (non-data) and then write the image to your other machines.  I've used this several times successfully.

The other option is simply tar'ing the system folders from the machine you want to copy.  Then untaring it on the other machines after doing a base install from your Ubuntu live CD.  There is a very good how-to on this in the FAQ's on this forum.

---

### Post by koenn on 2006-12-11
I've been asking myself the same question.
Here's a write-up :

[http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm) 

I was playing around with debian at the time, but I gather it would also work  with Ubuntu, and it should work independent of the hardware, because it does a real installation so the hardware recognition etc play their parts - but i'ts (quasi-) automatic; a,d customized as you can collect information from an existing system and apply it to the new to be installed systems

---

### Post by rioghal on 2006-12-11
I have 5 computers and here is what I did.

1) Install Ubuntu on one computer

2) Boot into System Rescue CD on that computer and run partimage to make images of any partitions you want on that first computer.

3) Burn those images to CD/DVD

4) Take the System Rescue CD, and the images you made, to the other computers and set up the partitions on the other computers

5) Then run partimage and restore the images you made to the other computers.

This may sound like a lot of work, but restoring the images to the other computers took about 10 minutes per computer versus the 1+ hours it took to install Ubuntu, install desired apps, tweak apps, edit configs, etc. on the first computer. Partimage only images the used space on a partition so an 80Gb partiton that only has 3Gb of data on it will copy only the 3Gb of data since the other 77Gb are free space.. plus partimage uses compression, I've noticed that a few Gb's of data will compress down to around 700Mb. I would think that 10Gb would compress down to fit on a single layer DVD.. not bad.

Seriously, System Rescue CD is quite awesome and there is a new version out recently. It now has gparted, Firefox, irssi and more stuff on it. I recommend this livecd to everyone who runs Linux.

Get it: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by bodhi.zazen on 2006-12-11
See this thread:

[http://duggmirror.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc/](http://duggmirror.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc/)

---

