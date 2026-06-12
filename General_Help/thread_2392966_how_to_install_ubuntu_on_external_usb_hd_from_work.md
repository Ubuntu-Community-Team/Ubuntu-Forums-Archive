---
title: "how to install ubuntu on external usb hd from working ubuntu pc"
date: 2018-05-28
forum: General Help
---

### Post by seekertom on 2018-05-28
My pc has two internal hds, one running ubuntu 18.04 lts and the other running winxp pro. I can switch between booting ubuntu or winxp at boot time with f12, or after ubuntu boots to a menu of ubuntu, some tests, or nt system. all this works fine.

now ive added an external hd attached to usb port, and I want to install ubuntu 16.04 on it, and make it bootable. I expect to install it internally in another pc, and run ubuntu 16.04 there.

I tried booting and installing from dvd, but get lost. during the process it only offers to install on ubuntu 18.04 hd or winxp hd. One choice is erase disk and install ubuntu, but im not so sure its talking about the blank hd, so i chose something else option.
The blank hd is shown as sdc and sdc1. theres a box to check format. theres a box to +/- change partition size, etc. It hollared at me once about needing swap space, and other things I hadn't done right.

So my question is, after I choose something else, and I see the list of drives, and I see the blank hd listed as sdc and sdc1 (hope it's all the same drive...) what do I do to format the drive, including swap space, and continue to install ubuntu 16.04. the blank hd is 1 tb.
Thanks,
st
:confused:

Today I made some progress. yancek got me thinking, and I found a great sequence on ask site, for using something else. Trying to do this really taught me a lot. Now, after installing 16.04 on external usb ssd on system normally running 2 hdds, one ubie 18.04 and the other winxp, i can f12 at bootup and have access to all three drives, and be running 16.04 on the usb ssd, or, I can boot defaults and run 18.04 or xp. I have to say, this is slickern greased owlsht.
thanks for yalls help. life is fun again... for now!
st

---

### Post by yancek on 2018-05-28
> I expect to install it internally in another pc, and run ubuntu 16.04 there.

You should be able to do that but if the 2nd machine has different hardware, you are likely to run into some problems booting and running it.

You are doing a very non-standard install and you will have to use the manual option, in Ubuntu that is referred to as Something Else.

> after I choose something else, and I see the list of drives, and I see the blank hd listed as sdc and sdc1 (hope it's all the same drive...) what do I do to format the drive,

If you have an sdc1 partition, make sure it does not take up the entire drive.  Leave some space for a swap partition.  Use the change tab to set the size of the partition and click the box next to Format to format it, select the filesystem type, ext4 is default. select as Mount point /.  Repeat the process to create a swap partition and another data partition if you want.  At the bottom of that window you will see Device for bootloader installation.  If the drive you are installing to is /dev/sdc, you will need to select that by clicking on the down arrow to the right of that line.  Otherwise it will do the default and install to /dev/sda which is one of your internal drives.  The link below has fairly detailed instructions on this process.

[https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653](https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653)

---

