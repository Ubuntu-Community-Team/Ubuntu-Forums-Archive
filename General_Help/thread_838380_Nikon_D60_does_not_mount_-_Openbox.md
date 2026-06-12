---
title: "Nikon D60 does not mount - Openbox"
date: 2008-06-23
forum: General Help
---

### Post by goferrr on 2008-06-23
Hello!

My camera - **Nikon D60 works just fine under Ubuntu** (Gnome) but recently I switched to Openbox
as a window manager and then problems started.

My external drive connected via USB didn't mount automatically as well but I changed */etc/fstab* and now it does.
But **surely fdisk does not recognize my camera** so I cannot fix it that way.
Under Gnome when I plug the camera f-spot starts and downloads pictures.
Under openbox, however, only *lsusb* and *dmesg* change - **f-spot does not react**.
```

dmesg
[ 3101.017919] usb 5-6: new high speed USB device using ehci_hcd and address 2
[ 3101.150016] usb 5-6: configuration #1 chosen from 1 choice
```

```
lsusb
Bus 005 Device 002: ID 04b0:041e Nikon Corp.
```
I found out that **gnome-volume-manager** does the job undr Gnome - but I don't have one anymore.

**As a result I cannot download pictures**. Switching to Gnome every single time I need to use my camera is obviously very annoying.
Any ideas? 
Thanks for your help:)

---

### Post by dnile on 2008-06-25
Sorry to be off topic!

I also have a Nikon D60, although I am having problems downloading the pictures from the camera...

Whenever F-stop starts and I try to import I get a message stating 'could not claim the usb device'

I am wondering if you had to do something to get yours to work??

Cheers!

---

### Post by cariboo on 2008-06-25
dnile, I usually get this error if a folder opens up at the same time as F-spot.

goferr does dmesg tell what device it is eg: sda1 sdb1, etc. if it does, then you can just mount it manually

Jim

---

### Post by goferrr on 2008-06-25
> **cariboo907 said:**
> 
goferr does dmesg tell what device it is eg: sda1 sdb1, etc. if it does, then you can just mount it manually

Jim

No, **dmesg and fdisk-l** obviously  don't tell a word about that. Same cameras, portable music players etc. don't mount in this 'old-fashioned' way;) like external drives do.

I found out that under Gnome (pretty sure about that) **Nautilus manages cameras**. If I start Nautilus (with option --no-desktop because I dont want it to spoil my desktop) and then plug the camera nothing happens - although I've got 'opening by fspot' set in Nautilus' preferences.

BTW. In Gnome and in Openbox dmesg and lsusb give the same answer. 

So **Dnile** check out its preferences and change maybe its default action? **I had no problems using D60 under Ubuntu.**

---

### Post by urukrama on 2008-06-25
You mentioned that it works in Gnome with gnome-volume-manager. Do you have a volume manager running in Openbox? 

You can use gnome-volume-manager (you can install it seperately, without installing Gnome), thunar-volman (if you use Thunar as your file manager), or ivman. They should all automount removable devices or disks, such as cameras, external hard disks, flash drives, cd-roms and dvds.

---

### Post by dnile on 2008-06-25
> **goferrr said:**
> So **Dnile** check out its preferences and change maybe its default action? **I had no problems using D60 under Ubuntu.**

Are you talking camera preferences or F-stop?

Here is what I am seeing...



[This is when I first insert the usb cable]("http://i286.photobucket.com/albums/ll111/blairtinant/Screenshot-1.png")
[Here is which camera I am trying to download from.]("http://i286.photobucket.com/albums/ll111/blairtinant/Screenshot-3.png")
[And this is the error message I get.]("http://i286.photobucket.com/albums/ll111/blairtinant/Screenshot.png")

Sorry about the last picture I had the screen capture program under the message but it is still readable.

btw I also tried my Canon SD1000 and still got the same results... :confused:

---

### Post by goferrr on 2008-06-25
> **urukrama said:**
> 

You can use gnome-volume-manager (you can install it seperately, without installing Gnome), thunar-volman (if you use Thunar as your file manager), or ivman. They should all automount removable devices or disks, such as cameras, external hard disks, flash drives, cd-roms and dvds.

Some tests performed:
1. I could download pictures via
```
sudo gnome-volume-manager-gthumb
```
which is kind of workaround if you want to get rid of gnome.
2.thunar+thunar-volman work! but... **I need to start thunar FIRST and THEN plug the camera** - which is **quite** ok;)
I wonder if some kind of lightweight daemon could do the job?? I mean plug the camera and get fspot to work automatically(under gnome it works like this with Nautilus).
3. I have no idea why Nautilus dooes not work like that under Openbox:( 
4.@dnile no, preferences in Nautilus. But youve got a problem with fspot-I don't know...

---

### Post by dnile on 2008-06-26
Hey guys thanks for you help.

I was able to find a solution here;

[http://ubuntuforums.org/showthread.php?t=784864]("http://ubuntuforums.org/showthread.php?t=784864")

Cheers!

---

### Post by toddesing on 2008-08-24
I just bought one too and had the same problem with mounting. 
I opened up _Picasa_ and selected it to import. Worked.

---

