---
title: "Does 5.10 come with a kernel source?"
date: 2005-10-24
forum: General Help
---

### Post by ecletrik on 2005-10-24
Does 5.10 ship with a kernel source?

(Allowing me to build linux-wlan right out of the box)

Or might a Netgear MA111 USB Wireless Adapter work without having to do anything?

---

### Post by Knowles on 2005-10-24
nope it doesnt

you can whoever open up the Synamptic Package Manager and search for Kernel and install it that way. Make sure you have your installation disk at hand (i htink), if you asking about the kernel source then I would make sure you get the build-essential pack too!

I forget the apt-get commands

---

### Post by daller on 2005-10-25
sudo apt-get install build-essential kernel-package libncurses5-dev   (Which of these are needed???)

sudo mkdir /usr/src/   (Does /usr/src exist in breezy per default??? - Can't remember whether or not I created it...)

cd  /usr/src/

sudo apt-get source linux-image-2.6.12-9-386

sudo ln -s linux-source-2.6.12-2.6.12 linux

cd linux

sudo vi MakeFile   (To edit the extraversion (If you don't edit this, it will overwrite the present kernel-image)

sudo make menuconfig

***EDIT AND SAVE***

make

sudo make install

sudo update-grub


...It's a long time ago I did it last (In my debian-days!!!) - So please excuse me, if I'm wrong about anything...

---

