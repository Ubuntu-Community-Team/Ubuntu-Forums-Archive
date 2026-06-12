---
title: "Old Compaq (win98) wanna install xubuntu"
date: 2008-06-12
forum: General Help
---

### Post by summuner848 on 2008-06-12
Well, i figure that before wiping my 98's harddrive, i would like to have a little feedback on how it will run xubuntu. It has an 11.3gb HD, and im not sure about the rest of the specs, but it runs decently as long as its not being overloaded by a billion programs running at once (which is why i want to put linux on there, because it runs linux, not one hundred programs that are needed to run windows)

A little feedback would be appreciated as to how it will cope with the wiping of its hard drive and booting to a disk and then installing from the disk.

Also, i would like to know if booting to a flashdrive will let it run faster than booting from a disk.

Edit:
I believe it has 256 or 512 Mb of ram because it was a higher end computer back in '98

Processor and graphics card shouldn't be a problem because it runs most games fine.

Edit #2:
For the record, I'm just installing xubuntu for the reason of getting a crappy gui and program incompatibility out of that system. So, I will be completely overwriting windows '98.

---

### Post by snowpine on 2008-06-12
Hi Summuner, I recently installed Ubuntu on an old Windows 98 laptop. It was a really fun project and it rescued this computer from collecting dust in the closet! We will be able to give you better advice if you can tell us more about your specs, especially how much RAM you have. 

My laptop has 256 ram. It runs both Ubuntu and Xubuntu rather well. They are not blazingly fast, but acceptable for browsing the web, word processing, etc. Right now I am trying out Fluxbuntu. It is noticably quicker, but not as easy for a beginner to use as Xubuntu.

One thing to keep in mind is that you can't boot from USB on a lot of old computers, so your flash drive idea may not work. 

Good luck!

---

### Post by snowpine on 2008-06-12
ps The xubuntu installer works very well, wiping the hard drive was easy. You can also set up a dual boot and keep Windows 98 if you think you'll ever need it again.

---

### Post by Kevbert on 2008-06-12
You can install Xubuntu with win98 dual boot with very few problems.  I've done this on an Athlon 900MHz 512Mb ram and 32Mb Voodoo Banshee video card.  First I set up some partitions formatted FAT32.  The first I installed win98 on. The second I installed Xubuntu and the third was used as swap for Xubuntu.  The Xubuntu one should be set to ext3 format (via the install CD) and the third should be at least twice the ram size.  Disk sizes should be approx. 3Gb (win, depending on what you want to run), 7Gb (Xubuntu mount point / ) and 1.5Gb (swap for me).
Xubuntu (Hardy) isn't that fast on my machine, but it's usable.  Two things I had problems with were the video card (it's very old) and the memory (which initially failed the memtest due to dust in the machine) -  even though Windows seemed to work fine.  A bit of using the vacuum cleaner and playing around with xorg.conf resolved the problem.

---

### Post by eriqjaffe on 2008-06-12
Be aware that if your system has less than 256mb of RAM (or is that 384 now?), you won't be able to install using the standard CD, you'll need the Alternate CD, which has a text-based (but still easy to follow) installer.

If you really want to make the most of your system, and have a low amount of unnecessary stuff on there, I'd recommend doing a command-line install and just add on the things you're going to really need.  It's also a great way of getting more in-depth with Linux.

---

### Post by summuner848 on 2008-06-12
bump!

---

### Post by snowpine on 2008-06-12
Xubuntu should run fine with 256mb ram, even better with 512. However, with 256 you will need to install from the alternate CD (as eriqjaffe pointed out).

---

### Post by summuner848 on 2008-06-12
what exactly is the alternate cd, and where can i get it if i need it?(just incase, for i have not tried booting to the cd yet, im still downloading the Xubuntu Hardy 8.04 Desktop iso)

---

### Post by snowpine on 2008-06-12
> **summuner848 said:**
> what exactly is the alternate cd, and where can i get it if i need it?(just incase, for i have not tried booting to the cd yet, im still downloading the Xubuntu Hardy 8.04 Desktop iso)

Hi Summuner, you can get the alternate CD [here]("https://help.ubuntu.com/community/GettingUbuntu"). It is an .iso image that you burn to a CD, but unlike the Live CD, you can't run it from the CD--you have to install. It is less taxing on older systems than the Live CD, but the installer is still easy enough to use (just text instead of graphical).

---

### Post by summuner848 on 2008-06-12
Thanks, I'll try this after the live CD.
Just because im not sure how much ram it has exactly.

---

### Post by x1a4 on 2008-06-12
> **summuner848 said:**
> what exactly is the alternate cd, and where can i get it if i need it?(just incase, for i have not tried booting to the cd yet, im still downloading the Xubuntu Hardy 8.04 Desktop iso)

The alternate CD has a little less bloat than the standard does.  It also doesn't have a graphical installer which is great for low-end systems.  Please note that although it doesn't have a graphical installer it's still easy to use.  I put Xubuntu Dapper on my Win95 box using the alternate CD and it worked great.  

To get the alternate CD, just visit [xubuntu.org/get]("http://www.xubuntu.org/get/") to find the mirror nearest you.  If you want an earlier release, select the mirror you want, then click the 'Parent Directory' link, then the 'Parent Directory' link again, and you will have a list of links to the last 5 releases.

---

### Post by summuner848 on 2008-06-12
So, it's basically a text installer?
Text installers aren't all that bad, and yet, Debian Linux's text installer was horrible, i had no clue which point of the installation i was in.

---

### Post by yaknowwat on 2008-06-12
you may want to look at UbuntuLite

It is very lightweight and fast the pre release canidate version came out last night it plans only using 56 MiB of RAM on boot with the LXDE environment ( [http://lxde.org](http://lxde.org) ) which is fairly simple and very fast.

[http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/)

In order to install ubuntu lite you must get ubuntu server edition install the basics of it which will give you a command line version of ubuntu after the install.

once ubuntu server is installed you login then run the listed commands which are :
```
wget http://download.tuxfamily.org/ubuntulite/nouveau/install_ubuntulite_nouveau
sudo bash install_ubuntulite_nouveau
```

---

### Post by summuner848 on 2008-06-12
Oh, wow, thanks.
I guess I'm gonna have to check that out.

---

### Post by x1a4 on 2008-06-12
> **yaknowwat said:**
> you may want to look at UbuntuLite

Or [Fluxbuntu]("http://fluxbuntu.org/") which uses [Fluxbox]("http://fluxbox.sourceforge.net/") as its default GUI.

---

### Post by snowpine on 2008-06-12
> **x1a4 said:**
> Or [Fluxbuntu]("http://fluxbuntu.org/") which uses [Fluxbox]("http://fluxbox.sourceforge.net/") as its default GUI.

+1 I am a big Fluxbuntu fan, however, you can install Xubuntu and then install Fluxbox later if you are interested. For that matter, once you have Xubuntu installed, you can install several windows managers (gnome for ubuntu, kde for kubuntu, xfce for xubuntu, fluxbox, etc) and play around with them until you find one you like best. That is the process I went through and I ended up liking Flux and Gnome the best (but really it is a matter of personal preference).

---

