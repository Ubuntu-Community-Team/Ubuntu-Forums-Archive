---
title: "Should I get 13.10?"
date: 2013-11-19
forum: General Help
---

### Post by ballistic turtle on 2013-11-19
I have 12.04 which I installed through Wubi two or three days ago. Is there any reason I should get 13.10? How would I do it?

---

### Post by Frogs Hair on 2013-11-19
12.10 was the last release to include Wubi. If you plan on sticking with Wubi keep 12.04 because it is supported longer. You might consider tying a traditional dual boot in April when 14.04 is released. Like 12.04 ,14.04 is a long term support release. Unity has come a very long way since 12.04.

---

### Post by Impavidus on 2013-11-19
Just play with wubi until it's around May. Then, if you still like Ubuntu, make backups of all your Ubuntu files, uninstall wubi and install a true dual boot with 14.04. In the meantime, get familiar with the system. This will make things easier when installing a true dual boot.

---

### Post by t0p on 2013-11-19
I also think it's a good idea to keep using 12.04 until the next LTS version is released.  Unless there's something you really really need or want that isn't in 12.04. Horses for courses.

---

### Post by leeper69 on 2013-11-19
Hi  I run both and like the newer version of grub used with 13.10 if you have the room on your hard drive you can to. a good place to dowload 13.10 is distrowatch.com
if you only have one partision you can choose to install 13.10 alongside your existing 12.4 install.
I use xubuntu dont care much for unity but that is a personal choice. the choices are numerous with ubuntu. have fun!

---

### Post by ballistic turtle on 2013-11-19
> **leeper69 said:**
> Hi  I run both and like the newer version of grub used with 13.10 if you have the room on your hard drive you can to. a good place to dowload 13.10 is distrowatch.com

How do I install 13.10 to have Windows 7, Ubuntu 12.04 and 13.10 triple booting

---

### Post by leeper69 on 2013-11-20
Hi keys.snickers
                              if you have three partisions on the hard drive you can pick do somthing else from the install menu then choose the partision that dosent already have window$ or ubuntu 12.4 installed on it and install 13.10. 
                              if you only have two partisions I would sugjest installing another hard drive and partishoning it with gparted so you can install any number of linux desktops you like on your machine. at one point I had 6 on mine.
                              if your computer is a laptop i would sugjest having three seperate partisions to do a tripel boot this may involv removing 12.4 repartishoning your harddrive with gparted from the install disk then reinstalling 12.4 then installing 13.10.
                              sorry I forgot about window$ you would need to use windows to repartision your drive with fdisk but be forwornd this may mean reinstalling window$ and if you dont have the real windows disk even this may not be possible due to        
                              the way some oem versions of window$ are set up.

---

### Post by Impavidus on 2013-11-20
You wrote you installed Ubuntu 12.04 through wubi. This means you're not dual booting right now. It's more like one-and-a-half booting. Adding another Ubuntu on a different partition would make this into something like two-and-half booting, instead of triple booting. The advantage of wubi is (or was) that you don't have to go through the process of repartitioning your drive and restoring the windows boot loader in case you decide to uninstall Ubuntu. If you decide to install a second Ubuntu system you'll have to go through this stuff nonetheless – not really a problem, it's certainly doable – but it defies the whole purpose of wubi. You could better uninstall Wubi-Ubuntu 12.04, repartition your drive, install Ubuntu 12.04 as a dual boot and then add whatever you like to make it a triple boot.

Note: I single boot, just Xubuntu 12.04. It suits my needs.

---

