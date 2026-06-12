---
title: "Ubuntu 6.06 Vs. Ubuntu 6.10"
date: 2006-12-14
forum: General Help
---

### Post by lucky_chouhan on 2006-12-14
Hi i want know what is the difference in Ubuntu 6.06 and Ubuntu 6.10 versions. i mean any big updates or etc.

---

### Post by lucky_chouhan on 2006-12-14
ubuntu 6.10 is include all audio and video codecs i mean mp3, mp4, avi etc.

---

### Post by meng on 2006-12-14
> **lucky_chouhan said:**
> ubuntu 6.10 is include all audio and video codecs i mean mp3, mp4, avi etc.
No, you have to install these codecs yourself, as with 6.06.
The differences are relatively minor GNOME 2.16 vs 2.14, Firefox 2 vs 1.5, etc.

---

### Post by lucky_chouhan on 2006-12-14
so only gnome updates.

---

### Post by aysiu on 2006-12-14
> **lucky_chouhan said:**
> so only gnome updates.
Well, unless you're using Kubuntu, in which case they're KDE updates, or Xubuntu, in which case they're XFCE updates.

By the way, technically speaking, Firefox is not a Gnome app, but it is the default web browser in Ubuntu.

---

### Post by meng on 2006-12-14
I don't consider that there are any MAJOR updates.

---

### Post by mcduck on 2006-12-14
> **aysiu said:**
> Well, unless you're using Kubuntu, in which case they're KDE updates, or Xubuntu, in which case they're XFCE updates.

By the way, technically speaking, Firefox is not a Gnome app, but it is the default web browser in Ubuntu.
The kernel in 6.10 has better support for multi-core CPU's. And for some hardware that isn't supported in 6.06 works with 6.10.

Edit: Of course the boot process is once again faster than before. If Ubuntu devs continue like this we won't even need the boot splash any more with Ubuntu 8.10 because nobody would be able to see it :D

Edit 2: Edgy release notes: [https://wiki.ubuntu.com/EdgyReleaseNotes]("https://wiki.ubuntu.com/EdgyReleaseNotes")

---

### Post by der_joachim on 2006-12-14
> **lucky_chouhan said:**
> so only gnome updates.

One of the major differences between 6.10 and 6.06 is a new way of init-scripting. Instead of loading all daemons at boot time, it just loads what it needs. If at some point additional services are needed, they are loaded at the spot. 

6.06 is apparently more stable, but my fresh 6.10 install never had a problem so far. :)

Read the Ubuntu wiki for more information on the upgrade.

---

### Post by yopnono on 2006-12-14
> **der_joachim said:**
> 
6.06 is apparently more stable, but my fresh 6.10 install never had a problem so far. :)


I have found dapper to be more stable and less bugs.

---

### Post by der_joachim on 2006-12-15
> **yopnono said:**
> I have found dapper to be more stable and less bugs.

That's why my laptop at work still has Dapper. I do not want to run into any strange problems when fighting off impatient customers. :)

---

### Post by cborga1985 on 2006-12-15
> **der_joachim said:**
> That's why my laptop at work still has Dapper. I do not want to run into any strange problems when fighting off impatient customers. :)
i still use dapper becuase there are still allot of problems with edgy right now.

---

### Post by az on 2006-12-15
> **lucky_chouhan said:**
> Hi i want know what is the difference in Ubuntu 6.06 and Ubuntu 6.10 versions. i mean any big updates or etc.

The software is written by many many people from different projects.  It is open source, free-libre software.  That means the software connects together at the source level, not at the compiled binary level.

What usually happens in linux distributions is that a few people get together and collect upstream applications together, tweak and compile them to all work together and release the binary packages together.  This is called a "release".  Different distros have different goals and releases happen from time to time.

To get the "cutting-edge" applications running on your system at any time can be difficult, because the way the apps interoperate between each other can change from time to time.  For a whole linux distribution, that's not such a big problem because the maintainers of the distro take care of all that for you.  But if you still want to run a newer version of one single application, you need to compile it from source yourself.  And that may involve tweaking.

What Ubuntu does is pick only a small subset of packages and release them fairly often - every six months.  This is the tradeoff between cutting-edge and stability.

The starts aligned well for Dapper and a few major projects reached a really high peak at the same time - Ubuntu decided to use that to make a LTS release - a release that will be supported for a longer time than a regular release.

If you want the very latest applications, at the expense of some stability, use Edgy.  If you want a rock-solid system for a mission-creittical purpose, use Dapper.

---

### Post by technodigifreak on 2006-12-15
> **azz said:**
> If you want the very latest applications, at the expense of some stability, use Edgy.  If you want a rock-solid system for a mission-creittical purpose, use Dapper.

Exactly!

---

### Post by cmost on 2006-12-15
Besides, Dapper can easily be brought up to speed where needed.  For example, i'm running Dapper with the very latest nVidia 9631 driver (much improved performance by the way,) I have XGL and Beryl 0.1.3 for stunning 3D visuals, and I'm running Firefox 2.0.x with improved security.  I also have installed the compiler toolchain (gcc 4.0, g++ 4.0, kernel sources and headers as well as GTK dev files, etc.)  so I can always compile any program I want from source to get the latest version, and, create my own DEB packages for others if i'm so inclined.  My workstation is a tool, not a toy.  A lot of Linux enthusiasts use their machines for play rather than work and they can afford some instabilities.  I like stability.  Stick with Dapper...it'll be around for five years and you can upgrade to the next LTS release when that occurs.  I hope this helps.

---

