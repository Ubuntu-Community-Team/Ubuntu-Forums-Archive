---
title: "Zune on Ubuntu"
date: 2007-07-05
forum: General Help
---

### Post by eashishkalra on 2007-07-05
Does any one has worked with zune on ubuntu. i am planning to buy a new zune but on my Home PC i have only ubuntu 6.06 installed and no other OS is it possible to transfer songs and video to zune from my home PC?.
Can i use Zune like a USB drive and transfer media to it?

---

### Post by CheeseEatingBulldog on 2007-07-05
Why on earth would you inflict a Zune on yourself?

---

### Post by vanadium on 2007-07-05
The same argument is valid for Apple iPods. It is equally bad. That aside, I cannot help you specifically on support of Linux for the Zune. The iPod is around longer, and is immensely popular, hence the better support on Linux.

---

### Post by yopnono on 2007-07-05
It's alway possible to install windows in a virtual machine like vmware, parallel, virtualbox, etc,etc. Or try using the wine. And the install the Zune software.

---

### Post by toddbmobile on 2007-08-02
Il have to put my 2 cents in on the old post the Zune video is much much better than Ipod video. Sorry Ive seen them both, and Zune's video just is. So I bought one. Hate how MS pooch screwed the wifi though.

---

### Post by Club17 on 2007-09-01
> **yopnono said:**
> It's alway possible to install windows in a virtual machine like vmware, parallel, virtualbox, etc,etc. Or try using the wine. And the install the Zune software.

Hi all. I have 1 Zune. The player is perfect... for Windows. Now, I'm using entire disk with my new Ubuntu 7 and installed Wine, but... when try to install Zune software, Wine says: Can't load .html file.

Anybody have a idea how to fix via Wine. Or, anybody try via Virtualbox???

---

### Post by ev5unleash1 on 2007-09-02
Yea, I'm trying to do the same and having the same problem. I also have a ZUNE two acually and I want to completely replace Windows if I have the same abiltys between the two.

If there is some kind of plugin for a linux player like there is an Ipod.

I think we need to ask winehq.

---

### Post by Lord Illidan on 2007-09-02
Well, if the Zune doesn't work on Ubuntu, you know whom to call..Microsoft!!

---

### Post by willz06jw on 2007-11-14
Well, if the iPod doesn't work on Ubuntu, you know whom to call..Apple!!  I know how Apple loves third party software (and hardware).

btw the Zune has a FM Radio

---

### Post by tech9 on 2007-11-14
> **Lord Illidan said:**
> Well, if the Zune doesn't work on Ubuntu, you know whom to call..Microsoft!!

now, why would you want to call Microsoft :lolflag:

---

### Post by timcredible on 2007-11-14
i haven't seen anyone get a zune to work with linux, maybe because most linux people don't really like microsoft products.  so, if you like the zune, then you should probably run windows so you can use your zune.  letting a music/video player determine what kind of OS you run seems kind of like the tail wagging the dog, but it's your choice.

---

### Post by fearevilleet on 2007-11-15
The new zunes actually look pretty nice, I would get one but I can not find any real solid information on how well it works with linux. (I am sure mac support is out of the question) If the ipod works so well on linux why cant the zune?

---

### Post by Namakemono456 on 2007-11-15
Theres a dev team working on zune-linux compatibility atm, as well as linux on the zune. seems like they are biting off more than can chew to me... 

BTW i have a zune and an ipod, i like the zune more, its a tank and MS is great about firmware updates, all of the players use the same firmware in essence, just a few unavailable features disabled cross product so updates are guaranteed for a long time. Plus now that the zune can sync wirelessly like the ipods, theres nothing than makes the ipod stand out anymore other than flashy graphics lol.

---

### Post by DjBones on 2007-11-15
if it makes any difference.. i installed rockbox on my ipod video to replace the firmware,
and that made it soo much easier to put music on it (considering you just had to drop files into it through the file manager)
i think if they make rockbox for that screen size, you can try that.
read up on the [site]("http://www.rockbox.org/") though

---

### Post by philidox on 2008-01-22
> **DjBones said:**
> if it makes any difference.. i installed rockbox on my ipod video to replace the firmware,
and that made it soo much easier to put music on it (considering you just had to drop files into it through the file manager)
i think if they make rockbox for that screen size, you can try that.
read up on the [site]("http://www.rockbox.org/") though

omg thx for the info i was always wondering if there was a way to revamp the firmware on my ipod.  I hope they get this thing crackin.  I just traded my ipod for a zune.  I got the the zune for the challenge of hacking it.  I know it will be a hard and difficult task but I'm sure linux will come thru.

---

### Post by money2themax on 2008-01-28
> **fearevilleet said:**
> The new zunes actually look pretty nice, I would get one but I can not find any real solid information on how well it works with linux. (I am sure mac support is out of the question) If the ipod works so well on linux why cant the zune?
you can't get the zune to work with anything but windows because we don't know how to get to it's drive as a HDD it's blocked unless you can get it to work like the iPod does with AmaroK or any other Linux music player your gonna have to use windows Xp or Vista

---

### Post by seventhc on 2008-01-28
Does it show up on your desktop when you plug it into your computer??

---

### Post by money2themax on 2008-01-28
> **seventhc said:**
> Does it show up on your desktop when you plug it into your computer??
nope

---

### Post by Luinfana on 2008-02-24
The Zune is an amazing little media device. I'm an avid Linux fan and an avid Zune fan - that seems to be pretty rare.

Your Zune isn't going to mount under Linux at all (show up in /media/, etc), because it's not a normal mass storage device, It's designed to use Microsoft's Media Transfer Protocol to send and recieve data over its USB connection. There has been some progress using [libmtp]("http://libmtp.sourceforge.net/") to communicate with the Zune, but files can only be *read or deleted*. Write-access (when the Zune displays "connected" on the screen) is not enabled until the Zune recieves a secret passkey from the Zune software, and thus Linux-based media managers (amarok, rhythmbox, etc) can't really manage the Zune and you can't browse it like a normal drive (for now, at least).

To get your music off, just reverse-sync it with the Zune software in Windows and copy the music files into Ubuntu. You can find more info on reverse-syncing [here]("http://zuneinsider.com/archive/2007/02/23/reverse-sync.aspx"), although this tutorial is for the old Zune software...if you have the updated 2.0 version, the procedure will be a little different.

Good luck, and happy Zuning...

---

### Post by zed41 on 2008-02-29
Don't know if anyone has done this yet, but I have successfully connected the zune through virtual box with full USB 2.0 support. IT is possible,

---

### Post by XFocus on 2008-03-07
I read zed's message and after an hour or two of tweaking, I was able to get my Zune to sync through virtualbox.  :-D

---

### Post by DirtDawg on 2008-03-07
> **DjBones said:**
> if it makes any difference.. i installed rockbox on my ipod video to replace the firmware,
and that made it soo much easier to put music on it (considering you just had to drop files into it through the file manager)
i think if they make rockbox for that screen size, you can try that.
read up on the [site]("http://www.rockbox.org/") though

Rockbox is the friggin bomb. My ipod nano first gen now plays videos, which it never did before, plus lots of free games, the ability to customize (with skins, icon sets, fonts, etc), a gameboy emulator, it's (much) easier to add/remove music and files, there's even a text editor!

Before switching to Rockbox, I was like, "man, this ipod is cool, but it could be so much cooler!". Rockbox made my nano that "cooler" i was looking for. I've been using it for a little under 2 years now and I'm still gushing! It's sad Apple didn't use the ipods full potential in the first place.

---

### Post by jdgiotta on 2008-03-13
> **XFocus said:**
> I read zed's message and after an hour or two of tweaking, I was able to get my Zune to sync through virtualbox.  :-D

Care to share your tweaking methods? I got a Zune when Woot.com was selling them for $80 (cheapest 30gb MP3 player).

I was 2 breathes away from installing Ubuntu on my new laptop, but then I remembered my Zune.

---

### Post by jdgiotta on 2008-03-13
> **zed41 said:**
> Don't know if anyone has done this yet, but I have successfully connected the zune through virtual box with full USB 2.0 support. IT is possible,

You'd think virtual box would be able help figure out the handshake.

---

### Post by bijanafx on 2008-03-17
> **zed41 said:**
> Don't know if anyone has done this yet, but I have successfully connected the zune through virtual box with full USB 2.0 support. IT is possible,


just wanted to confim this. i installed the newest version of virtualbox with usb 2.0 support. it works perfectly. just blasted my windows partition, zune sync was the last thing holding me back. yeeeesssss!

this may help someone (replace USER with your username...):
after downloading and installing the latest .deb from the virtualbox website, i ran

```
sudo adduser USER vboxusers
```

```
sudo addgroup usbfs
```       (noting here the output gid to use in the /etc/fstab line below, ****)

added this line to /etc/fstab:

```
none /proc/bus/usb usbfs devgid=****,devmode=664 0 0
```

then ran

```
sudo adduser USER usbfs
```

and ```
sudo mount -a
```

logged off and back in (Ctrl+Alt+Backspace)

then configured the usb settings in the virtualbox gui, installed the zune software and done!

---

### Post by Xalabam on 2008-03-31
I am trying to follow this guide, but, when i plug the zune, nothing seems to happen, ill provide some snaps, i hope you could guide me.

/Etc/fstab/

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c47329f9-72f9-4579-bbed-e826572b87b0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=36307DB2307D79A7 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=****,devmode=664 0 0[/PHP]

[[IMG]http://img228.imageshack.us/img228/7451/screenshotzunesettingsgd9.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshotzunesettingsgd9.png)

[[IMG]http://img503.imageshack.us/img503/4131/screenshotzunerunninginoy3.th.png[/IMG]](http://img503.imageshack.us/my.php?image=screenshotzunerunninginoy3.png)


Atm, i am clueless about what to do next in order to get the zune to be seen at VirtualBox, so any help would be more than welcome, thx a lot.

---

### Post by Xalabam on 2008-03-31
I found out the problem :)
at
none /proc/bus/usb usbfs devgid=[COLOR="Red"]****[/COLOR],devmode=664 0 0 

**** = your User ID wich can be found under System--Administration--Users and Groups

i had not idea till 5 minutes ago :)

By the way, my Zune already works under VirtualBox :guitar:

---

### Post by paraplegicpanda on 2008-04-03
Okay, I have a problem. When I go into my VirtualBox GUI and open up the Settings, there is no USB tab in the list on the left. Any idea why?

---

### Post by helfrez on 2008-04-03
question, why not just use wireless sync? use 1.1 mode to get the device configured, and then just use the zune software in the vm and sync over wifi? Assuming you have a wifi network of course...

---

### Post by paraplegicpanda on 2008-04-07
Good call... Thanks!!!

---

### Post by paraplegicpanda on 2008-04-08
Okay, the wireless sync idea didn't work... You have to connect your Zune through USB first, then you can set up your wireless zync. Fortunately, I did figure out what my problem was... I had an old build of VirtualBox. I updated from v1.5.0 to v1.5.6, and I now have USB support!!! I am reinstalling XP right now, so I'll let everybody know how it goes once I get my Zune working!!!

---

### Post by bhuthogg on 2008-04-08
hope this works out but what ive seen of rockbox on the i pods it would be amazing on the zune.
we really need a solid no going back to windows solution.



> Okay, the wireless sync idea didn't work... You have to connect your Zune through USB first, then you can set up your wireless zync. Fortunately, I did figure out what my problem was... I had an old build of VirtualBox. I updated from v1.5.0 to v1.5.6, and I now have USB support!!! I am reinstalling XP right now, so I'll let everybody know how it goes once I get my Zune working!!!

---

### Post by paraplegicpanda on 2008-04-08
Okay, so the Zune works without a hitch in VirtualBox. Just install the latest version, install XP, update your copy of XP and install Zune software. Then add yourself to the group "usbfs" in Ubuntu, plug up the Zune, and you're ready to go!!!

---

### Post by bhuthogg on 2008-04-08
could you do a GUIDE post for this please cmd line stuff etc

Also would this work with Vi$ta and vitrualbox ?


> **paraplegicpanda said:**
> Okay, so the Zune works without a hitch in VirtualBox. Just install the latest version, install XP, update your copy of XP and install Zune software. Then add yourself to the group "usbfs" in Ubuntu, plug up the Zune, and you're ready to go!!!

---

