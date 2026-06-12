---
title: "Grub Boot Error"
date: 2008-03-23
forum: General Help
---

### Post by Drewmanfuu on 2008-03-23
I recently installed Ubuntu on my Fujitsu P1120 via the network install and since I had to many partitions on my hard rive I VERY STUPIDLY deleted one and now whenever I boot up my laptop it says GRUB BOOT ERROR 17. SO I cant boot up anything now and I just want to wipe everything off the hard drive and reinstall windows but I have no clue how and I'm getting very fustrated...can anyone please help me out here?:confused:

---

### Post by spo0neybard on 2008-03-23
Well if you want to delete everything then just insert your windows CD wait for it to load
and delete all the partitions.

---

### Post by Drewmanfuu on 2008-03-23
I would but the thing is my laptop is a ultra portable and has no CD rom drive or floppy...and every time I try to use a external usb Cd drive nothing happens...

---

### Post by smoker on 2008-03-23
you can reinstall/repair grub if you want, rather than delete everything, have a look and download this:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by smoker on 2008-03-23
> **Drewmanfuu said:**
> I would but the thing is my laptop is a ultra portable and has no CD rom drive or floppy...and every time I try to use a external usb Cd drive nothing happens...

you will probably have to change the bios boot settings to get the laptop to boot first from a usb cd-rom, or other usb device

---

### Post by Drewmanfuu on 2008-03-23
I've also tried that and then upon boot up I would even go to the boot menu and select USB CD-ROM Drive and still it would just skip that and go to the grub boot error.

---

### Post by smoker on 2008-03-23
try changing all boot priority setting to usb cd-rom, as in, first cd-rom, second, cd-rom, third, etc, etc, or set all but cd -rom to disable,

best of luck

---

### Post by Drewmanfuu on 2008-03-23
ok ill try that.....and thanks for responding so quickly, greatly appreciated.

---

### Post by Drewmanfuu on 2008-03-23
Alright, so I dowloaded the Grub thing and burned it to a CD hoping to reinstall grub and I changed the Bios settings to only enable booting from a CD drive and The computer boots up and then I get this message: Operating System Not Found. Any idea whats going on here?

---

### Post by smoker on 2008-03-23
hmm, the bios seems to be moving on before detecting there is a bootable usb device attached. i would check all the usb settings in the bios to ensure they are all enabled, eg, usb legacy devices, etc.

also, change any settings, eg, 'fastboot enabled', etc.to normal

i would write down all the changes you make so you can easily experiment with different settings and always get back to the original if required.

best of luck

---

### Post by Drewmanfuu on 2008-03-26
Well I have been trying and trying but unfortunately nothing seems to be working:(. Its getting very frustrating and all I want is to wipe everything off the drive and reinstall windows, and the thing is I don't have any valuable files or anything at all I need on there so its O.K. to loose data.

---

### Post by Drewmanfuu on 2008-03-28
Anyone?? Please??

---

### Post by smoker on 2008-03-28
sorry you're still having trouble, you could perhaps try installing linux on a usb flash drive if you have one handy, there are some good easy guides here: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

or, if you reinstall windows, perhaps you could install linux on top of windows, and access linux that way,
[http://wubi-installer.org/](http://wubi-installer.org/) (this is still a beta version),

best of luck

---

### Post by Drewmanfuu on 2008-03-30
So I Installed Linux on the A Flash Drive and I tried it on my desktop...works fine but I get nothin from my Laptop. I tried lookin through all the bios settings but nothing shows booting from USB Flash Drive.:confused:

---

### Post by smoker on 2008-04-01
i suppose your bios may not support booting from usb, you could maybe check the support page of the manufacturer and see if there is a bios update that may allow this. this is not something to be done lightly though, and to be honest, i'm not sure how you would do it without a floppy! i would follow any directions in this regard very carefully.

can't think of anything else to try at the moment,

best of luck

---

### Post by Drewmanfuu on 2008-04-20
I recently borrowed a USB Floppy Drive from a friend and dowloaded the program for windows that lets you make  bootable windows XP floppy disks and everthing works fine untill i put the 5th(you need 6 floppy disks for the install) foppy disk in and its says somthing like cdrom.sys file currupted and quits the whole  setup porcess....bummer!!!!

---

