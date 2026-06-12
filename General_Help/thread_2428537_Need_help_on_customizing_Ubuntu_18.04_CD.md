---
title: "Need help on customizing Ubuntu 18.04 CD"
date: 2019-10-05
forum: General Help
---

### Post by blason78 on 2019-10-05
Hi Folks,

We have our own native developed software that we would liek to distribute it through Custom OS. Hence we decided to create a customized OS where 

[LIST=1]
[*]Installation should be automatic
[*]Installation Look a& Feel to be automatic
[*]Display names while installation to be changes instead of Ubuntu.
[*]Background logo of Ubuntu to be removed.
[/LIST]

We then have opted for Kickstart but somehow this stuff is not working. ISO is still prompting for Locale,TimeZone and all those features.
Can someone pls guide us as to know which files to be modified to achieve the above?

[LIST]
[*]Also, can we install preseed file instead of ks.cfg?
[*]Which one has better advantage?
[/LIST]

TIA
Blason R

---

### Post by Frogs Hair on 2019-10-05
Please see the links regarding preseed and re-branding . 

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)


[https://github.com/kamilion/customizer/wiki/Rebranding](https://github.com/kamilion/customizer/wiki/Rebranding)

---

### Post by blason78 on 2019-10-06
hey there,

I have created my preseed file and given option but dont know why Ubuntu Isntaller for 18.04 is still prompting for the setup. Here is my seed file

more ../traplox/isolinux/txt.cfg
default trap
label trap
  menu label ^Install Trap 1.2
  menu default
  kernel /casper/vmlinuz
  append  preseed/file=/cdrom/preseed/trap.seed debian-installer/locale=en_US console-setup/layoutcode=us boot=casper initrd=/casper/initrd ramdisk_size=16384 root=/
dev/ram rw quiet  ---


Any other file I need to customize?

---

