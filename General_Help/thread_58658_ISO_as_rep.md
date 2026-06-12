---
title: "ISO as rep?"
date: 2005-08-21
forum: General Help
---

### Post by qalimas on 2005-08-21
I do quite a bit of apt-getting, and a lot of hte times it'll get a library it wants from the CD, and it's a hassel to dig through my CDs to find my Ubuntu every time.

So, is there some way to use the Uvuntu ISO image as a repository in the place of the CD?

---

### Post by Spudgun on 2005-08-21
If you remove the CD from your apt-get sources.list, apt-get will just download everything off the net.

---

### Post by OzzyFrank on 2007-08-05
That's true... but he was actually asking how to add an iso to the repo, hehe.

Here's the answer, and we're assuming you're using an "Alternate" install CD iso image (since they actually have more packages on them than the Live CDs, and for example you can't install "kubuntu-desktop" from a Live CD); obviously just replace "ubuntu-7.04-alternate" with the appropriate iso name. First off, you need to **create a mount point** for the iso:

**[COLOR="Purple"]sudo mkdir /media/ubuntu-7.04-alternate[/COLOR]**

Preferably you want to **mount the iso automatically upon boot**, so edit **fstab**:

**[COLOR="#800080"]sudo gedit /etc/fstab[/COLOR]**

Add the line (replacing "username" with your username, and adding subfolder if need be):

[B]/home/username/ubuntu-7.04-alternate.iso /media/ubuntu-7.04-alternate iso9660 ro,loop,auto 0 0
[/B]
If you'd like to mount that quickly and without rebooting, just mount everything in **fstab**:

**[COLOR="#800080"]sudo mount -a[/COLOR]**

Either fire up the Software Sources app or edit the list manually:

**[COLOR="#800080"]sudo gedit /etc/apt/sources.list[/COLOR]**

Either way, add the following line (edit it to your needs if you named the mount point something else. If it is an earlier or later version, you'll need to replace "feisty" with "edgy" or "gutsy"):

**deb file:/media/ubuntu-7.04-alternate/ feisty main restricted**

Actually, if you just open the sources.list file and edit it directly, the line should read:

**deb file:///media/ubuntu-7.04-alternate/ feisty main restricted**

If you used the app, it will want to refresh the list automatically before you close it. Otherwise:

**sudo apt-get update**

It should now use the .iso image as a repository. Hope that helps!

---

### Post by strabes on 2007-08-05
Open your /etc/apt/sources.list:```
sudo gedit /etc/apt/sources.list
``` and remove the line that looks like this:> deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted

---

### Post by OzzyFrank on 2007-08-05
Oh, and here are Nautilus scripts to add to the Scripts menu when you right click your iso images (you need to have nautilus-scripts installed, and the .iso images need to be somewhere within your home folder).

First, go to ~/.gnome2/nautilus-scripts/ and create 2 files:** iso-mount** &** iso-unmount** (you can add .sh extension if you want, but it isn't needed). Into the mount one paste:

[COLOR="Blue"]#!/bin/sh 
# 
for I in "$*" 
do 
foo=`gksudo -u root -k -m "Please Enter Your Password..." /bin/echo "got r00t?"` 
sudo mkdir /media/"$I" 
sudo mount -o loop -t iso9660 "$I" /media/"$I" && nautilus /media/"$I" --no-desktop 
done 
done 
exit0[/COLOR]

For the unmount, paste:

[COLOR="Purple"]#!/bin/sh 
# 
for I in "$*" 
do 
foo=`gksudo -u root -k -m "Please Enter Your Password..." /bin/echo "got r00t?"` 
sudo umount "$I" && zenity --info --text "Successfully unmounted /media/$I/" && sudo rmdir "/media/$I/" 
done 
done 
exit0[/COLOR]

To make them executable, right-click > Properties > Permissions, and allow them to be executed.

I've used these useful mount and unmount scripts without problem. Only one weird thing when I actually had the Xubuntu Alternate .iso mounted at the same time as I had the CD of it in the drive... the CD wouldn't eject manually, by right-clicking or using the **eject** command, and I noticed it was no longer listed in Computer, and only ejected after **sudo eject**, hehe! I think it got confused about having 2 "discs" with the same name running at once... which might explain why it kept telling me I didn't have permission to eject Windows XP, hehehe!

---

### Post by ProfessionalNewbie on 2008-06-28
Does it matter if you use a newer ISO image to the currently installed ubuntu level.
I have ubuntu 7.10 installed & want to use the ISO 8.04?

---

