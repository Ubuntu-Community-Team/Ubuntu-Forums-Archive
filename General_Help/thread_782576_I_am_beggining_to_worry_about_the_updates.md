---
title: "I am beggining to worry about the updates"
date: 2008-05-05
forum: General Help
---

### Post by heatblazer on 2008-05-05
I still have not received any updates for my Hardy. My mom already has linux kernel .17 even a week ago and I still have not a single one update. Can you give me any info? I am attached to ipact server for Bulgaria. Even when I change the reps. there is no difference.

---

### Post by cb951303 on 2008-05-05
I got only 3 updates so far but they may be from other unofficial repos that I have in my source list.

---

### Post by p_quarles on 2008-05-05
There have been very few updated packages since the release. Nothing to worry about. 

As for your mom having received a newer kernel (2.6.24-17, I'm guessing you meant), is she using Ubuntu? The current kernel in Hardy is 2.6.24-16, and as far as I know, the only way of getting a newer one is to compile it yourself.

---

### Post by heatblazer on 2008-05-05
So to be accurate - here is what I got from synaptic History:

Commit Log for Sat May  3 12:48:31 2008


Upgraded the following packages:
libldap-2.4-2 (2.4.7-6ubuntu3) to 2.4.7-6ubuntu4.1
lshw (02.12.01-2ubuntu1) to 02.12.01-2ubuntu1.1

I took this from my history in synaptic. Nothing after the upgrade on 24.04.08. But there is a kernel .17 I know that because my mom`s xubuntu was upgraded already... Is there a problem in my PC?

---

### Post by Aearenda on 2008-05-05
There have only been a couple of small updates for me in Australia. All of my PCs are using the -16 kernel.

---

### Post by heatblazer on 2008-05-05
My mom is on ubuntu but I have installed XFCE session because 8.04 appears to be much "heavier" than the new Gnome and she began to receive a tons of upgrades. I am living separately so I can`t help you with the history log but I saw over 19 updates (probably xfce based) and a new kernel  .17

---

### Post by p_quarles on 2008-05-05
> **heatblazer said:**
> My mom is on ubuntu but I have installed XFCE session because 8.04 appears to be much "heavier" than the new Gnome and she began to receive a tons of upgrades. I am living separately so I can`t help you with the history log but I saw over 19 updates (probably xfce based) and a new kernel  .17
All I can say is that I would be interested to see the results of these two commands from your mom's computer:
```
uname -r
```
and
```
lsb_release -a
```
I'm still unsure what you mean by "kernel .17", but the output of those commands will clear it up.

---

### Post by heatblazer on 2008-05-05
I promise to report ASAP. I`ll do this from my mom`s PC. Even if the thread is lost I`ll report in a new one!

---

### Post by TheExplorer on 2008-05-05
2.6.24.17 is in 'hardy-proposed' only for now.

Since I have it enabled I've received pretty lotsa updates already.

---

### Post by forestpixie on 2008-05-05
If she's running ubuntu perhaps she has proposed and backports enabled I have and 

kevin@kevin-desktop:~$ uname -r
2.6.24-17-generic

---

### Post by forestpixie on 2008-05-05
> I promise to report ASAP. I`ll do this from my mom`s PC. Even if the thread is lost I`ll report in a new one!

Now don't be starting a new thread - find this one again

---

### Post by p_quarles on 2008-05-05
> **TheExplorer said:**
> 2.6.24.17 is in 'hardy-proposed' only for now.

Since I have it enabled I've received pretty lotsa updates already.
Ah, that explains it. I didn't notice any packages being held back, but I wasn't going out of my way to look, either.

---

### Post by heatblazer on 2008-05-05
So there is nothing to worry about, right?

---

### Post by p_quarles on 2008-05-05
> **heatblazer said:**
> So there is nothing to worry about, right?
Correct.

---

### Post by vishzilla on 2008-05-05
Patience, my dear. Patience! :p

---

### Post by heatblazer on 2008-05-05
I am posting all history from mom`s pc for you:

Commit Log for Fri Apr 25 12:54:57 2008


Upgraded the following packages:
ca-certificates (20070303-0ubuntu0.7.10) to 20070303-0ubuntu0.7.10.1

Commit Log for Mon Apr 28 13:39:12 2008


Upgraded the following packages:
compiz-fusion-plugins-main (0.7.4-0ubuntu4) to 0.7.4-0ubuntu5
foomatic-filters (3.0.2-20071204-0ubuntu2) to 3.0.2-20071204-0ubuntu2.1
gtk2-engines-pixbuf (2.12.9-3ubuntu2) to 2.12.9-3ubuntu3
gvfs (0.2.3-0ubuntu4) to 0.2.3-0ubuntu5
gvfs-backends (0.2.3-0ubuntu4) to 0.2.3-0ubuntu5
gvfs-fuse (0.2.3-0ubuntu4) to 0.2.3-0ubuntu5
libgtk2.0-0 (2.12.9-3ubuntu2) to 2.12.9-3ubuntu3
libgtk2.0-bin (2.12.9-3ubuntu2) to 2.12.9-3ubuntu3
libgtk2.0-common (2.12.9-3ubuntu2) to 2.12.9-3ubuntu3
libgtk2.0-dev (2.12.9-3ubuntu2) to 2.12.9-3ubuntu3
libgvfscommon0 (0.2.3-0ubuntu4) to 0.2.3-0ubuntu5
lshw (02.12.01-2ubuntu1) to 02.12.01-2ubuntu1.1

Commit Log for Tue Apr 29 17:56:35 2008


Upgraded the following packages:
bsdutils (1:2.13.1-5ubuntu1) to 1:2.13.1-5ubuntu2
evolution (2.22.1-0ubuntu3) to 2.22.1-0ubuntu3.1
evolution-common (2.22.1-0ubuntu3) to 2.22.1-0ubuntu3.1
evolution-data-server (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
evolution-data-server-common (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
evolution-plugins (2.22.1-0ubuntu3) to 2.22.1-0ubuntu3.1
gnome-system-monitor (2.22.0-1ubuntu3) to 2.22.1-0ubuntu1
libcamel1.2-11 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libebook1.2-9 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libecal1.2-7 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libedata-book1.2-2 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libedata-cal1.2-6 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libedataserver1.2-9 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libedataserverui1.2-8 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libegroupwise1.2-13 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libexchange-storage1.2-3 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libgdata-google1.2-1 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libgdata1.2-1 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libldap-2.4-2 (2.4.7-6ubuntu3) to 2.4.7-6ubuntu4.1
mount (2.13.1-5ubuntu1) to 2.13.1-5ubuntu2
update-manager (1:0.87.24) to 1:0.87.25
update-manager-core (1:0.87.24) to 1:0.87.25
util-linux (2.13.1-5ubuntu1) to 2.13.1-5ubuntu2
util-linux-locales (2.13.1-5ubuntu1) to 2.13.1-5ubuntu2
wine (0.9.59-0ubuntu4) to 0.9.59-0ubuntu5

Upgraded the following packages:
apport (0.108) to 0.108.1
apport-gtk (0.108) to 0.108.1
capplets-data (1:2.22.1-0ubuntu4) to 1:2.22.1-0ubuntu4.1
gnome-about (1:2.22.1-0ubuntu6) to 1:2.22.1-0ubuntu6.1
gnome-control-center (1:2.22.1-0ubuntu4) to 1:2.22.1-0ubuntu4.1
gnome-desktop-data (1:2.22.1-0ubuntu6) to 1:2.22.1-0ubuntu6.1
hal (0.5.11~rc2-1ubuntu7) to 0.5.11~rc2-1ubuntu8
kdebase-bin (4:3.5.9-0ubuntu7) to 4:3.5.9-0ubuntu7.1
kdebase-bin-kde3 (4:3.5.9-0ubuntu7) to 4:3.5.9-0ubuntu7.1
kwin (4:3.5.9-0ubuntu7) to 4:3.5.9-0ubuntu7.1
libgnome-desktop-2 (1:2.22.1-0ubuntu6) to 1:2.22.1-0ubuntu6.1
libgnome-window-settings1 (1:2.22.1-0ubuntu4) to 1:2.22.1-0ubuntu4.1
libhal-dev (0.5.11~rc2-1ubuntu7) to 0.5.11~rc2-1ubuntu8
libhal-storage-dev (0.5.11~rc2-1ubuntu7) to 0.5.11~rc2-1ubuntu8
libhal-storage1 (0.5.11~rc2-1ubuntu7) to 0.5.11~rc2-1ubuntu8
libhal1 (0.5.11~rc2-1ubuntu7) to 0.5.11~rc2-1ubuntu8
libnautilus-extension1 (1:2.22.2-0ubuntu4) to 1:2.22.2-0ubuntu5
nautilus (1:2.22.2-0ubuntu4) to 1:2.22.2-0ubuntu5
nautilus-data (1:2.22.2-0ubuntu4) to 1:2.22.2-0ubuntu5
python-apport (0.108) to 0.108.1
python-problem-report (0.108) to 0.108.1
sudo (1.6.9p10-1ubuntu3) to 1.6.9p10-1ubuntu3.1


Commit Log for Sat May  3 11:23:23 2008


Upgraded the following packages:
apparmor (2.1+1075-0ubuntu9) to 2.1+1075-0ubuntu9.1
apparmor-utils (2.1+1075-0ubuntu9) to 2.1+1075-0ubuntu9.1
jockey-common (0.3.3-0ubuntu7) to 0.3.3-0ubuntu8
jockey-gtk (0.3.3-0ubuntu7) to 0.3.3-0ubuntu8
linux-generic (2.6.24.16.18) to 2.6.24.17.19
linux-headers-generic (2.6.24.16.18) to 2.6.24.17.19
linux-image-generic (2.6.24.16.18) to 2.6.24.17.19
linux-libc-dev (2.6.24-16.30) to 2.6.24-17.31
linux-restricted-modules-common (2.6.24.12-16.34) to 2.6.24.12-17.35
linux-restricted-modules-generic (2.6.24.16.18) to 2.6.24.17.19
nvidia-glx (1:96.43.05+2.6.24.12-16.34) to 1:96.43.05+2.6.24.12-17.35
python-virtkey (0.50build1) to 0.50ubuntu0.1
update-manager (1:0.87.25) to 1:0.87.26
update-manager-core (1:0.87.25) to 1:0.87.26

Installed the following packages:
linux-headers-2.6.24-17 (2.6.24-17.31)
linux-headers-2.6.24-17-generic (2.6.24-17.31)
linux-image-2.6.24-17-generic (2.6.24-17.31)
linux-restricted-modules-2.6.24-17-generic (2.6.24.12-17.35)
linux-ubuntu-modules-2.6.24-17-generic (2.6.24-17.24)


the last one is with the weird kernel upgrade. Hope that was helpful

---

### Post by forestpixie on 2008-05-05
Check in software sources (Admin -System) on the update tab for a check mark in the proposed updates box.

It might be best if you're not sure what's going on that you don't have it enabled, it's not the only thing there that was updated from proposed updates.

---

### Post by heatblazer on 2008-05-05
I`ll do it. I was just worried if my update manager was working, but it is. I hope to give some useful info to all of you. I`ll leave the other machines that I am administrating with 7.10 for now until 8.04 becomes more stable. ( I am maintaining over 20 ubuntu PCs at the hospital and the people are extremely happy with it and are very grateful to CANONICAL )

---

### Post by sports fan Matt on 2008-05-05
Not to be a worrywart, but inho, one of the reasons and the beauty of updates i feel is if the updates come, they come.  I just feel that "not having updates" honestly means evrything is ok and if its not, we wait till they are released to fix problems..Am i the only one not honestly bothered by not receiving the updates or have I offically lost my mind?:lolflag:

---

