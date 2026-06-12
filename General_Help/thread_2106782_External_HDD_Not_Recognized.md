---
title: "External HDD Not Recognized"
date: 2013-01-20
forum: General Help
---

### Post by kkillens on 2013-01-20
Hi All!

New here so take it easy on meh! :)


OK so I just backed up all of my data from my Win7 machine to an external USB HDD. On this HDD, I have also placed the Ubuntu .iso file which I will be booting to and beginning my trek into the world of Linux (as a primary OS). 

SO, I have a few questions about some issues I'm having:

1. While in my VMPlayer Ubuntu, I am unable to see the external HDD in the GUI. I'd like to know as well which generic Linux command will allow me to view all disks/properties in the terminal as well as why it is that my Ubuntu box is not recognizing it. 

2. I would like to know if I will be able to not only boot off of this external to the USB .iso file, but if I will also be allowed at some point during the installation to wipe and completely format the HDD which my Windows machine and files are located on.


Thanks so much for y'all's help!

-K

---

### Post by ld114 on 2013-01-20
Not sure I fully follow your issues, but here is my take:

Not seeing your external usb hdd in "VMPlayer Ubuntu" may well be an issue relating to the VMPlayer setup. However, I would put VMPlayer on one side for the moment. It is best to boot into Ubuntu from a DVD or a USB stick (booting from an external hdd is not straightforward and would put your data there at risk).

Download and refer to a Getting Started with Ubuntu guide from [http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)) and then boot your PC using the DVD or USB stick you have created. You may need to change the bios settings to enable boot from a dvd or ucb stick (this is usually done by pressing f2 as you start the pc).

You can try out Ubuntu, or install it. Try it out first and see if Ubuntu will recognize your external hdd. If it is FAT formatted (this is usually the default supplied on external usb hdd drives) it should read it ok. If having tried out Ubuntu, it can read your external hdd, and you are happy to continue with Ubuntu then:

1) Make sure you have created windows restore discs so that you can retreat to windows in the future (though you can install Ubuntu alongside WIndows if you want, and then have a dual boot pc).

2) Double check that all the data you want to keep is backed up on to the external hdd.

3) Run the Ubuntu installer - it will give you the option to completely wipe the hdd inside your PC before installing Ubuntu.

4) Once the installation is complete, then you should be able to access the data on your external usb hdd.

Hope this helps, but best advice is to read the Getting Started manual before doing anything.

---

### Post by kkillens on 2013-01-20
I know that the External is not FAT formatted as I have been using it with Windows exclusively and have formatted it as such. Will this be an issue with a Linux machine? Also, what command(s) do you recommend for viewing all connected devices or External HDD from the CLI?

---

### Post by ld114 on 2013-01-20
See this link for some info about mounting an external hdd:

[http://askubuntu.com/questions/177825/how-to-mount-an-external-hdd](http://askubuntu.com/questions/177825/how-to-mount-an-external-hdd)

As noted, *sudo fdisk -l* will list connected drives and tell you the format etc.

I have read that using a windows formatted ntfs disk can be problematic, so I would recommend using FAT (unless you have individual files larger than 4GB which FAT can't handle). I have not used an ntfs disk, so don't have any direct experience with it.

Hope this helps.

---

### Post by ld114 on 2013-01-21
Actually I remember I did use an NTFS format once for an external disk, but that was in Debian Squeeze to export a VirtualBox setup (came to 7GB). This worked ok in Debian, and I could import it back again - so maybe Ubuntu (which is based on Debian) will manage ok. Try some good tests first though. 

Maybe others will have some evidence/experience.

---

