---
title: "help with IDE hdd filled to capacity, can't login!"
date: 2015-05-12
forum: General Help
---

### Post by Retro_Garage on 2015-05-12
Hello all, ubuntu power user here.... apparently torrent files will use ALL free space with no restrictions or fail safe and not allow you to login because there is "not enough space to create theme file."

straight ubuntu 13.10
xfce 4
IDE hdd with 99gb/dual boot XP with 75gb IDE which i have access to and can boot to.
768mb ram (runs good believe it or not do video and audio editing and more)

Filled to capacity, so I cannot login. I tried using a live cd to delete some files, but the home folder is protected, no read/write permissions.

Any help you folks could provide me with maybe drop to a root shell and a simple command to delete some stuff? As long as i can guess the file path names i may be able to get it done.

Thanks!

---

### Post by Bucky Ball on 2015-05-12
Boot from the live media> Try Ubuntu> Open a terminal at the desktop> launch the file manager with 'gksudo nautilus', replace nautilus if you're using something different. Can you now delete the files? When you are booted from the live media, you do have the /home partition, or the partition the /home directory is on, mounted and you are trying to delete the files from the correct /home folder? Silly question, but doesn't hurt to ask. ;)

Incidentally, 13.10 is well out of date, reached EOL some time ago. When you get this sorted I advise you upgrade to a supported release.

---

### Post by Retro_Garage on 2015-05-12
well you're making me think I overlooked the sudo technique altogether, so I will attempt again. I have xubuntu 13.10 and ubuntu 13.10 live cd versions so I will give it a shot! thanks for the tip. When I log in to the live session, both HDDs automatically mount and I can access everything except the home folder on my primary ubuntu hdd. So if the super user do 'gksudo' will make a difference then hopefully I'm good. And i do plan on upgrading to 15.10 eventually.. but I'll be building a new machine soon because the HP pavillion I'm using is just old now but still works! I tend to live by the belief "if it ain't broke, don't fix it."

---

### Post by jerryferry on 2015-05-12
If you've access to another pc with a cd writer you might try one of the Puppy Linux variants. Makes for a useful Swiss Army Knife for solving Pc problems. Boots to an 'XP' like interface with lots of installed programs. Most importantly the media can be removed once its booted so you can archive stuff off to the cd/dvd or external media. Some puppy variants work well on most hardware but it might be worth trying more than one.

---

### Post by Retro_Garage on 2015-05-12
never actually had to go out of my way to try puppy linux, usually any other *buntu live cd has most tools needed, I have used the Gparted live cd numerous times on customers systems for different issues on windows and linux.

---

### Post by jerryferry on 2015-05-12
You can remove puppy disk after boot & its got a slightly out of date gparted. Pretty fast too.

---

### Post by Retro_Garage on 2015-05-12
yes, i've been aware of puppy linux for some years now, always seems to be geared toward very very low end systems with very little ram like under 512mb, as far as i've heard. I'm sure one day i will come across a use for it... but for now I have 2 2001 model imacs which run Lubuntu 12.04 just fine, no need for it just yet! I imagine maybe a Pi system or something would be good, ARM arc? Thanks for the info.

---

### Post by Bucky Ball on 2015-05-13
I certainly agree with 'if it ain't broke, don't fix it'. That's my motto! And that's why I use an LTS release rather than the interims. Try installing 14.04 LTS when you get there. It is supported until 2019, 15.04 (and 15.10) give you nine months. LTS releases happen every two years and are supported for five (next LTS 16.04 LTS, at least, that's the plan). ;)

You might be able to upgrade to 14.04 LTS via the update manager/Software Updater, but getting back on topic, where are you at with your original problem?

---

