---
title: "Gnome Help system not working"
date: 2006-07-11
forum: General Help
---

### Post by greengrocer on 2006-07-11
Hello all,

When I click the Help Icon in the Panel menu in Gnome, the mouse pointer turns into that animated circle thingy for about 5 seconds and then nothing happens.

I am using Ubuntu 5.10 Breezy Badger.

It used to work when I originally installed Breezy, but somewhere along the line it has died.

I have installed the following software since original install:

- Mozilla Thunderbird latest
- (Upgraded) Mozilla Firefox from 0.8 to 1.5.4
- Google Earth beta
- Skype beta that supports ALSA and OSS
- Added some fonts which are appearing fine in Open Office 2.x (open office was installed by default)

- Xine (which is excellent)
- MPlayer (which is not so excellent)
- Museek
- mkttfdir (i think that is the name of the package)
- All system updates have been applied using the built in Ubuntu update system


I have edited and made changes to the following files:

- Unhashed universe and multi universe repos in /etc/apt/sources.list
- Modified the way one of my file systems mounts in /etc/fstab
- Prettied up the Grub boot manager in /boot/grub/menu.list
- Modified the screen resolution settings in /etc/X11/xorg.conf

So as you can see, I havent made that many changes to the system, and fairly common ones too. So why would my Gnome help menu stop working? Is anyone aware of common factors that can kill the Gnome help system?

Edit:

I have discovered that the version of Mozilla Frirefox (1.5.0.4) that I had installed has caused the problem.  I had used the version downloaded directly from Mozilla.com

This had affected the Gnome help system 'yelp' which relies on some libraries in the original Firefox version that is installed from Ubuntu repo's.  In particular: libgtkembedmoz.so

Luckily I had backed up the original Mozilla-Firefox directory, so I had the files neccessary to fix the problem.


Morals to the story:

1) Always Backup things before changing them.
2) Always try to use software that comes from official repo's

---

