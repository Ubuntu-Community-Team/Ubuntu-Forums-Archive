---
title: "cannot start or re-configure Xserver"
date: 2007-07-24
forum: General Help
---

### Post by paletti on 2007-07-24
when starting ubuntu, instead of getting a graphical interface, i get a blue screen with the message **failed to start Xserver. /usr/bin/x: error loading shared libraries: /usrlib/libXfont.so.1 cannot read data file: invalid argument**

i tried the following commands but they don't work:

*sudo dpkg-reconfigure xserver-xorg* gives message: **unable to excecute /usr/sbin/dpkg-reconfigure: permission denied**

*sudo dpkg --configure -a* gives message **unable to excecute /usr/sbin/dpkg-reconfigure: permission denied**

i also entered *sudo gedit /etc/x11/xorg.conf* but then i get the message **cannot open display: (null)**

pleeeaase, i'm stuck! :( who can help me? thanks for your time!

---

### Post by bigken on 2007-07-24
its sudo  dpkg --configure -a

---

### Post by paletti on 2007-07-24
> **bigken said:**
> its sudo  dpkg --configure -a

it gives me the message: [B]unable to excecute /usr/sbin/dpkg-reconfigure: permission denied
[/B]
somehow it seems that it is a sudo problem rather than a re-configure problem!

---

### Post by Seisen on 2007-07-24
Try reinstalling X

```
sudo apt-get install x-window-system-core
```

---

### Post by paletti on 2007-07-24
> **Seisen said:**
> Try reinstalling X

```
sudo apt-get install x-window-system-core
```

I did that but no improvement :(:

[LIST]
[*]still blue sceen after boot
[*]when i try to (re-)configure: **unable to excecute /usr/sbin/dpkg-reconfigure: permission denied**
[/LIST]

---

### Post by distroman on 2007-07-24
```
sudo nano -w /etc/X11/xorg.conf
```
Might help you accessing xorg.conf and fix if that's the place needed finxing.

---

### Post by paletti on 2007-07-24
> **distroman said:**
> ```
sudo nano -w /etc/X11/xorg.conf
```
Might help you accessing xorg.conf and fix if that's the place needed finxing.

I can edit this file :) but I'm not sure what I have to edit exactly. In the section "DEVICE" I changed 

*Driver "ati"* to *Driver "vesa"* but it didn't help. Should I change anything else?

---

### Post by distroman on 2007-07-24
I don't know, you could post the output of;
```
cat /etc/X11/xorg.conf
```

When did it happen? What was the last thing you did before it broke?

---

### Post by paletti on 2007-07-25
A few days before this crash I cancelled a some ubuntu updates (kernel and perhaps some drivers) because downloadspeed was too low, but apart from that i didn't install any new software.

In the terminal I get an output of *cat /etc/X11/xorg.conf* but I have no idea how to  post it here on this forum (the GDM obviously doesn't work so i cannot easily copy/paste into browser).

Meanwhile I tried to mount my external harddisk (at least to get some iimportant files from the ubuntu partition to my external HD) but no succes either. Command* sudo /etc/fstab* replied with **permission denied**

I'm getting pretty frustrated by now. It seems that, no matter what, sudo doesn't have the permission to actually read, excecute or edit files...:confused:

---

### Post by logos34 on 2007-07-25
Try using the livecd instead. Then you'll have internet access.
> 
Command sudo /etc/fstab replied with permission denied

it's** sudo gedit /etc/fstab**

---

### Post by paletti on 2007-07-25
Hi logos, I tried sudo gedit /etc/fstab as well but again... no luck (permission denied).

But now i have an even bigger problem :(! I don't know even where to start, it's a looong story but here it goes..

I decided to give up trying to fix Xserver and just do a clean ubuntu install. However, first I really really needed some important files from the ubunu partition (/dev/hda2) so i logged in as 'ubuntu' after booting with the install cd (don't know if that is the same as the livecd).

From there I mounted the original ubuntu partition using **mount /dev/hda2 /mnt **(i had no permission to make a new directory inside /mnt) and that enabled me to see the directories on my original ubuntu partition...
But I couldn't actually read/access/copy the files/dirs because i'm not logged in as the owner 'paletti'. So i tried to switch user and log in with 'paletti' but it says i use wrong username/password (but those are correct). So i guessed I should login into ubuntu (without using the cd) and from there change the file permissions. But now Ubuntu doesn't want to start at all!!!!! It says that /dev/hda2 has errors in the filesystem and when fixing them with fsck takes forever....

What should I do??? Is there a way so I can login as 'paletti' (using the install cd) and get back some files which are stored on /dev/hda2?

---

### Post by distroman on 2007-07-25
You can't use gedit it's a gui application you need to use nano or equivalent.

You could try; 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
just to see what happens.
Hope it works out.
gl

---

### Post by paletti on 2007-07-25
GOOD NEWS! I retrieved my important files from the ubuntu partition!!!!

Here's what I did:
- I used Ubuntu CDROM to log in as user ubuntu
- In terminal I switched to root user by typing sudo -i
- I mounted ubuntu partition using: mount /dev/hda2 /mnt
- I changed the file permission of the folder "vit 1c" using: sudo chmod 777 /mnt/home/paletti/Desktop/vit\1c
- Copied files to internal SD drive
The only thing I don't understand yet is how to change the file permissions of all the files inside a folder....

So next step will be a fresh install of Ubuntu, yay!!:)
Oh yeah and I won't cancel any more ubuntu updates in the future (I suscpect it has something to do with it!)

Thank you all for your help guys, awesome!:guitar:

---

### Post by logos34 on 2007-07-25
> The only thing I don't understand yet is how to change the file permissions of all the files inside a folder....

Add recursive option:

sudo chmod **[COLOR="Red"]-R[/COLOR]** 777 /path/to/directory

---

