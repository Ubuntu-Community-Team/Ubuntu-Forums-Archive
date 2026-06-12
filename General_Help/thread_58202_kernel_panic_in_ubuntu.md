---
title: "kernel panic in ubuntu"
date: 2005-08-19
forum: General Help
---

### Post by raakken on 2005-08-19
Hi
I've installed the latest uprgrades for ubuntu this morning, and then turned the computer off. When i turned on the computer later, it loaded for some time, and then this message appered:
Kernel panic - not syncing : VFS : Unable to mount root fs on unknown-block(0,0)

wtf is this? 

offtopic: I can't install g++(c compilator) and cannot install programs from source.
what's that all about? It needs a library, that need another that need g++......
 :mad:  :mad:  ](*,) 
HELP!
I love ubuntu besides these little things... Maybe I got a blue-monday copy of ubuntu?

---

### Post by mikalh on 2005-08-19
Hi,

I get *exactly* this error too, and I'm at a loss for what to do. Maybe this security update  should be withdrawn, if it breaks sytems like this.

One thing I noticed at boot, the kernel image is 2.6.10-5-386, whereas the kernel update I installed is 2.6.10-34.4. Is this correct? From Grub I can find no other kernel image in my boot folder.

I've got an SATA HDD on an NForce 4 Ultra-based motherboard, if that helps.

Thanks for any help anyone can give me!

---

### Post by jesse on 2005-08-19
[QUOTE=mikalh]Hi,

I get *exactly* this error too, and I'm at a loss for what to do. Maybe this security update  should be withdrawn, if it breaks sytems like this.

One thing I noticed at boot, the kernel image is 2.6.10-5-386, whereas the kernel update I installed is 2.6.10-34.4. Is this correct? From Grub I can find no other kernel image in my boot folder.

I've got an SATA HDD on an NForce 4 Ultra-based motherboard, if that helps.

Thanks for any help anyone can give me![/QUOTE]



Hi. I had this kernel panic problem too after upgrading. I think upgrading the linux-image package caused the problem. When it happened I thought my system was doomed and I would never be able to boot again, but I did a search and found a way to solve it. I tried it and it worked, and now not only do I boot without problems but even have an upgraded kernel. 

You need to get an Ubuntu live cd to fix your system. 
Boot with the Ubuntu live cd. Then open a root terminal and type the following. 

mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

DO NOT CLOSE THIS TERMINAL

Then, in the same open root terminal, edit /mnt/linux/etc/apt/sources.list and add the Breezy Badger repositories
To do this, 

type the following: 

gedit /mnt/linux/etc/apt/sources.list

Then In the document sources.list, past the following lines

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

Save and close sources.list

Then in the same terminal which you should NOT have closed type the following commands: 

apt-get update
(while it's updating make sure it loads the Breezy repos)

apt-get install initrd-tools
apt-get install linux-image-2.6.12-4-686

Then, IN THE SAME TERMINAL THAT YOU SHOULD NOT HAVE CLOSED, edit /mnt/linux/etc/apt/sources.list and COMMENT OUT the breezy repos. 
(Put a # symbol in front of each breezy line that you pasted previously and then save sources.list)

Now you can reboot without the cd and you shouldn't get the kernel panic any more. If you still do, tell me. installing the linux image from Breezy worked for me and repaired my system.

---

### Post by Czubek on 2005-08-20
Hi
 
[QUOTE=jesse]
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

DO NOT CLOSE THIS TERMINAL

Then, in the same open root terminal, edit /mnt/linux/etc/apt/sources.list and add the Breezy Badger repositories
To do this, 

type the following: 

gedit /mnt/linux/etc/apt/sources.list[/QUOTE]I did everything exactly You wrote, except one:
mount /dev/hda8 /mnt linux - cause its my "/" partition (when i mount /dev/hda1 /mnt/linux i get: chroot: cannot run command `/bin/bash': No such file or directory)
Now after gedit:
> (gedit:21932): Gtk-WARNING **: cannot open display:
What should i do?

---

### Post by raakken on 2005-08-20
[QUOTE=jesse]Hi. I had this kernel panic problem too after upgrading. I think upgrading the linux-image package caused the problem. When it happened I thought my system was doomed and I would never be able to boot again, but I did a search and found a way to solve it. I tried it and it worked, and now not only do I boot without problems but even have an upgraded kernel. 

You need to get an Ubuntu live cd to fix your system. 
Boot with the Ubuntu live cd. Then open a root terminal and type the following. 

mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

DO NOT CLOSE THIS TERMINAL

Then, in the same open root terminal, edit /mnt/linux/etc/apt/sources.list and add the Breezy Badger repositories
To do this, 

type the following: 

gedit /mnt/linux/etc/apt/sources.list

Then In the document sources.list, past the following lines

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

Save and close sources.list

Then in the same terminal which you should NOT have closed type the following commands: 

apt-get update
(while it's updating make sure it loads the Breezy repos)

apt-get install initrd-tools
apt-get install linux-image-2.6.12-4-686

Then, IN THE SAME TERMINAL THAT YOU SHOULD NOT HAVE CLOSED, edit /mnt/linux/etc/apt/sources.list and COMMENT OUT the breezy repos. 
(Put a # symbol in front of each breezy line that you pasted previously and then save sources.list)

Now you can reboot without the cd and you shouldn't get the kernel panic any more. If you still do, tell me. installing the linux image from Breezy worked for me and repaired my system.[/QUOTE]
 Hi
When I came to where I should open /mnt/linux/etc/apt/sources.list, I got this message:
Gtk warning**: locale supported by C library using the fall-back `C` locale
Gtk warning**: cannot open display

so I did a sudo /mnt/linux... and I got in and did what I supposed to do, but the breezy repsositorys, well, I don't think they were found(got 404 error). And when I tried to restart på computer, just for fun, it didn't start. What did I do wrong?
I got alot of C errors on my computer.(can't install g++, and so on...)

---

### Post by jesse on 2005-08-20
Oops. I'm so sorry. I goofed in my instructions. You should still keep the same terminal open that I told you to keep open, but for editing sources.list using gedit  :roll: you should open and use a different terminal. 

I forgot that you can't run x using chroot.  :roll:

---

### Post by raakken on 2005-08-20
[QUOTE=jesse]Oops. I'm so sorry. I goofed in my instructions. You should still keep the same terminal open that I told you to keep open, but for editing sources.list using gedit  :roll: you should open and use a different terminal. 

I forgot that you can't run x using chroot.  :roll:[/QUOTE]
 then I did it all right, but it didn't work. It didn't find any of the repositorys. I think. I'm a newbie.
Kept getting 404 error...
I think it was to all the breezy repositories...
any idea to might be the problem?
I'll try again just to be sure though
thanks it would be great to get my comnputer up and running, but it seems abit dark at the moment:(

---

### Post by jesse on 2005-08-20
I'm so sorry for my erroneous instructions the first time. They were accidental. Here are my corrected instructions. Doing this should solve the problem. 

Hi. I had this kernel panic problem too after upgrading. I think upgrading the linux-image package caused the problem. When it happened I thought my system was doomed and I would never be able to boot again, but I did a search and found a way to solve it. I tried it and it worked, and now not only do I boot without problems but even have an upgraded kernel.

You need to get an Ubuntu live cd to fix your system.
Boot with the Ubuntu live cd. Then open a root terminal and type the following.

mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

DO NOT CLOSE THIS TERMINAL

Then, IN A NEW DIFFERENT OPEN ROOT TERMINAL, edit /mnt/linux/etc/apt/sources.list and add the Breezy Badger repositories
To do this,

type the following IN THE NEW ROOT TERMINAL:

gedit /mnt/linux/etc/apt/sources.list

Then In the document sources.list, past the following lines

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

Save and close sources.list

NOW CLOSE THE NEW TERMINAL AND GO BACK TO THE OTHER ONE (THE ONE YOU DID THE CHROOT COMMAND IN), WHICH YOU SHOULD NOT HAVE CLOSED, AND THEN type the following commands:

apt-get update
(while it's updating make sure it loads the Breezy repos)

apt-get install initrd-tools
apt-get install linux-image-2.6.12-4-686

Then, IN A NEW ROOT TERMINAL, edit /mnt/linux/etc/apt/sources.list and COMMENT OUT the breezy repos. YOU CAN USE GEDIT TO EDIT SOURCES.LIST IN THE SAME WAY YOU DID BEFORE. 
(Put a # symbol in front of each breezy line that you pasted previously and then save sources.list)

Now you can reboot without the cd and you shouldn't get the kernel panic any more. If you still do, tell me. installing the linux image from Breezy worked for me and repaired my system.

THANKS AND I'M SORRY AGAIN FOR MY INITIAL ERROR.

---

### Post by raakken on 2005-08-20
[QUOTE=jesse]I'm so sorry for my erroneous instructions the first time. They were accidental. Here are my corrected instructions. Doing this should solve the problem. 

Hi. I had this kernel panic problem too after upgrading. I think upgrading the linux-image package caused the problem. When it happened I thought my system was doomed and I would never be able to boot again, but I did a search and found a way to solve it. I tried it and it worked, and now not only do I boot without problems but even have an upgraded kernel.

You need to get an Ubuntu live cd to fix your system.
Boot with the Ubuntu live cd. Then open a root terminal and type the following.

mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

DO NOT CLOSE THIS TERMINAL

Then, IN A NEW DIFFERENT OPEN ROOT TERMINAL, edit /mnt/linux/etc/apt/sources.list and add the Breezy Badger repositories
To do this,

type the following IN THE NEW ROOT TERMINAL:

gedit /mnt/linux/etc/apt/sources.list

Then In the document sources.list, past the following lines

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

Save and close sources.list

NOW CLOSE THE NEW TERMINAL AND GO BACK TO THE OTHER ONE (THE ONE YOU DID THE CHROOT COMMAND IN), WHICH YOU SHOULD NOT HAVE CLOSED, AND THEN type the following commands:

apt-get update
(while it's updating make sure it loads the Breezy repos)

apt-get install initrd-tools
apt-get install linux-image-2.6.12-4-686

Then, IN A NEW ROOT TERMINAL, edit /mnt/linux/etc/apt/sources.list and COMMENT OUT the breezy repos. YOU CAN USE GEDIT TO EDIT SOURCES.LIST IN THE SAME WAY YOU DID BEFORE. 
(Put a # symbol in front of each breezy line that you pasted previously and then save sources.list)

Now you can reboot without the cd and you shouldn't get the kernel panic any more. If you still do, tell me. installing the linux image from Breezy worked for me and repaired my system.

THANKS AND I'M SORRY AGAIN FOR MY INITIAL ERROR.[/QUOTE]
 Hi and thanks for taking the time.
I followed your instructions, and last time it didn't find the repositorys for breezy, but this time I didn't even get there!!!!
Opening /mnt/linux/etc/atp/source.list in another root terminal gave me this:
GnomeUI-WARING**: while connecting to session manager: Authentication rejected, reason: not of authentication(authentic?) protocols specified are supported and host-based authentication failed

ok, so I use sudo in a regular konsol, find the file(which says I changed it today, which is tru, i tried erlyer. but the "other" source.list was changed in 1970!!!! strange stuff)
typed in the lines of repositorys, easy, saved, smooth as silk, but THEN.
apt-get update, and this came:
E: opening /etc/apt/sources.list -ifsream::ifstream (5 input/output error)

for **** sake, whats this? this isn't even the file I edited.
What have I done to deserve this, I'm tired and I don't understand shit(newbie if you haven't noticed, bad temper too:)

what do i do wrong, and again thanks for taking time

---

### Post by alaithea on 2005-08-20
[QUOTE=jesse]apt-get install initrd-tools
apt-get install linux-image-2.6.12-4-686[/QUOTE]

Thanks for your help. I got as far as the quoted text above. For the first line, it tells me I already have the latest version. For the second, it says "E: Couldn't find package linux-image-2.6.12-4-686"

Any ideas?

---

### Post by raakken on 2005-08-20
and when i type: gedit mnt/linux/etc/apt/source.list  it says creating, and it comes blank, then I need to open the file from whitin gedit...
I edited the /etc/apt/source.list too, but it didn't make much difference thoug.. same error
please hepl

---

### Post by alaithea on 2005-08-20
[QUOTE=raakken]and when i type: gedit mnt/linux/etc/apt/source.list  it says creating, and it comes blank, then I need to open the file from whitin gedit...
I edited the /etc/apt/source.list too, but it didn't make much difference thoug.. same error
please hepl[/QUOTE]

Make sure you're typing "sources.list" not "source.list"

---

### Post by alaithea on 2005-08-20
[QUOTE=alaithea]Thanks for your help. I got as far as the quoted text above. For the first line, it tells me I already have the latest version. For the second, it says "E: Couldn't find package linux-image-2.6.12-4-686"

Any ideas?[/QUOTE]

Is there someplace I can find a list of available breezy packages, so that I can verify that I'm typing in the correct name?

Any help would be appreciated. I'd like to get my system back.

---

### Post by jesse on 2005-08-20
You're right. Now I feel like putting my foot in my mouth. It is sources.list not source.list

Sorry I forgot the s when I was typing. 

When running the live cd, you don't want to edit /etc/apt/sources.list

Instead you want to mount your hard drive, which still has your entire system on it, and then edit THAT sources.list. Typing the following commands (pressing enter after each one)

mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

in a root terminal (and make sure it is in fact a ROOT terminal) while running the live cd version of Ubuntu temporarily mounts your / partition on your hard drive, where your entire system and all its files still reside even though you can't yet boot because of the kernel panic, as the folder /mnt/linux in your live cd's filesystem, giving you command line access to the system on your hard drive from within the live cd's system. This gives you access to your hard drive in that terminal, but only command line access. 

To edit the sources.list on your hard drive, as opposed to the one on the live cd, you need to edit /mnt/linux/etc/apt/sources.list as opposed to /etc/apt/sources.list

BUT, you cannot edit /mnt/linux/etc/apt/sources.list from the same root terminal where you entered the commands above (mkdir..., mount... etc). Instead you have to run gedit from a different root terminal and then edit /mnt/linux/etc/apt/sources.list from there. 

Then when you do 

apt-get update
apt-get install initrd

You must do it from the terminal where you entered the mkdir.., mount..., chroot... etc. Otherwise, it will use the sources list in /etc/apt/sources.list, which is for the live cd, as opposed to /mnt/linux/etc/apt/sources.list, which is for your hard drive's system, when updating the repository list. 

If it says it cannot find the specific linux-image package I specified, as you wrote, then, assuming you've actually added the breezy lines to /mnt/linux/etc/apt/sources.list, in that same open terminal where you did mkdir..., mount... etc, type 

apt-get install linux-image

and it should give you a list of possibilities to choose from. 

Then you can choose whichever one says linux-image-2.6-12 or something to that effect. 

Hope this helps.

---

### Post by alaithea on 2005-08-20
I'm not seeing a 2.6.12 kernel available at all, when I type apt-get install linux-image. Just 2.6.10 and 2.6.11, which are what I already have and are broken. Does that mean I'm not accessing the breezy repo's correctly? I verified that I updated the sources.list on the harddrive, using the "special" terminal. Argh.

---

### Post by jesse on 2005-08-20
[QUOTE=alaithea]I'm not seeing a 2.6.12 kernel available at all, when I type apt-get install linux-image. Just 2.6.10 and 2.6.11, which are what I already have and are broken. Does that mean I'm not accessing the breezy repo's correctly? I verified that I updated the sources.list on the harddrive, using the "special" terminal. Argh.[/QUOTE]

Ok. so you added the breezy repos to the sources.list on the hard drive using the special terminal, right? 

Did you type "apt-get update" and press enter in the special terminal and wait for it to update before you did "apt-get install linux-image" in the special terminal? 

If you didn't do the apt-get update first then it won't show you a 2.6.12

Hopefully you have never closed the special terminal since you did the mkdir..., chroot... etc.

Open the firefox browser and type /mnt/linux/etc/apt/sources.list in the address bar and press enter. Then copy what appears in your browser and post it for me in the forum so I can see if you have the breezy repos there and if they're enabled.

---

### Post by alaithea on 2005-08-20
Yes, I did all as described. Just now, in desperation, thinking that some other repo's I have in my sources might be conflicting, I commented out all but the breezy repo's. So here is my file, through firefox pointed at /mnt/linux/etc/apt/sources.list.
```

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


#deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

#deb http://security.ubuntu.com/ubuntu hoary-security main restricted
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

#deb http://security.ubuntu.com/ubuntu hoary-security universe
#deb-src http://security.ubuntu.com/ubuntu hoary-security universe

#deb http://ubuntu.tower-net.de/ubuntu/ warty java
#deb http://ubuntu.tower-net.de/ubuntu/ hoary java

#deb http://archive.ubuntu.com/ubuntu/ warty multiverse

#deb http://dl.sourceforge.net/sourceforge/jedit ./ 
#deb-src http://dl.sourceforge.net/sourceforge/jedit ./ 

#deb http://archive.ubuntu.com/ubuntu hoary multiverse
#deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted


##Breezy sources
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

```

When I run apt-get update, I get:
```

root@ubuntu:/ # apt-get update
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security Release
Hit http://us.archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://us.archive.ubuntu.com breezy/universe Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Fetched 3B in 0s (4B/s)
Reading package lists... Done

```

Then, here's what I get upon trying to install the new stuff:
```

root@ubuntu:/ # apt-get install initrd-tools
Reading package lists... Done
Building dependency tree... Done
initrd-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 89 not upgraded.
root@ubuntu:/ # apt-get install linux-image
Reading package lists... Done
Building dependency tree... Done
Package linux-image is a virtual package provided by:
  linux-image-2.6.10-5-k7 2.6.10-34.4
  linux-image-2.6.10-5-386 2.6.10-34.4
  linux-image-2.6.11-1-k7 2.6.11-0.2
You should explicitly select one to install.
E: Package linux-image has no installation candidate
root@ubuntu:/ #

```
No 2.6.12 versions of the linux-image, as you can see.

Thanks so much for trying to help me out.

---

### Post by jesse on 2005-08-20
It appears from what you're posting that it's showing you the linux-image packages you currently have installed as opposed to options for packages you can install. 

I just had a look at my synaptic with breezy repos enabled and found that linux-image-2.6.12-7-686 is installable. 

Try 

apt-get install linux-image-2.6.12-7-686 

in the special terminal. 

I'm glad to see at least that you're accessing your hard drive's sources.list with apt-get in the special terminal and that your breezy repos are enabled. 

Of course, once you succeed and can boot your system again, I recommend commenting out the breezy repos and enabling the Hoary ones again.

---

### Post by alaithea on 2005-08-20
No go.  :sad:
```
root@ubuntu:/ # apt-get install linux-image-2.6.12-7-686
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-image-2.6.12-7-686
```

---

### Post by jesse on 2005-08-20
[QUOTE=alaithea]No go.  :sad:
```
root@ubuntu:/ # apt-get install linux-image-2.6.12-7-686
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-image-2.6.12-7-686
```[/QUOTE]

I'm at a loss as to why it's not letting you install that package. Have you tried just 2.6.12 without the 7-686? When I use the breezy repos and update synaptic it finds the package, so I don't understand why you're not. 

Believe it or not, we are making progress and this can be done.

---

### Post by alaithea on 2005-08-20
```
root@ubuntu:/ # apt-get install linux-image-2.6.12
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-image-2.6.12

```

I hope it can be done... else I'll be doing a lot of backing up and reinstalling soon.

I'm not missing any breezy repos, am I?

---

### Post by jesse on 2005-08-20
You might also want to try 

apt-get upgrade linux-image

---

### Post by jesse on 2005-08-20
Of course, do 

apt-get update

first before you do anything else.

---

### Post by jesse on 2005-08-20
You don't appear to be missing repos. I saw your sources.list and it looked fine. It also loades the breezy repos when you do apt-get update, right?

---

### Post by alaithea on 2005-08-20
Ooh, that might be getting somewhere. But when I do, it wants to upgrade a whole bunch of other stuff, too. I haven't done it yet, as I'm not really looking to run breezy as a system, yet.  ;-) 

How does this look? If I say "yes," will it be dangerous to my system?

```

root@ubuntu:/ # apt-get upgrade linux-image
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  alsamixergui alsaplayer-common alsaplayer-gtk alsaplayer-oss celestia
  easytag freeciv-client-gtk gimp-svg gnome-gv gnomebaker graveman
  gstreamer0.8-mad irb1.8 libarts1-audiofile libbz2-ruby1.8 libcsiro0
  libdbm-ruby1.8 libexif-ruby1.8 libfcgi-ruby1.8 libgettext-ruby1.8
  libgmime2.1 libmysql-ruby1.8 libopenssl-ruby1.8 libplplot9 librdf-ruby
  libreadline-ruby1.8 nvu pinentry-qt qjackctl rdoc1.8 ri1.8 rosegarden4 sox
  stratagus-gl timidity timidity-interfaces-extra totem-xine
The following packages will be upgraded:
  alsa-oss apcupsd apcupsd-doc athcool bum cdda2wav celestia-common expectk
  firestarter foomatic-gui freeciv-data freeciv-server gemdropx gnome-blog
  gnomp3 guile-1.6-slib irb lesstif2 libdb2 libgal2.0-6 libgal2.4-0
  libgal2.4-common libgimp-perl libgtk-canvas1 libgwrapguile1 liblo0
  libncurses-ruby1.8 libppd0 librd-ruby1.8 libredcloth-ruby1.8
  librmail-ruby1.8 libsoundtouch1 libtar libtdb1 libtermios-ruby1.8
  libzip-ruby1.8 mpage openoffice.org-help-en openoffice.org-thesaurus-en-us
  pdl ppdfilt python-foomatic rdoc ri runit slib suikyo-table xfonts-terminus
  xpdf xpdf-common xpdf-reader xpdf-utils
52 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
Need to get 52.1MB of archives.
After unpacking 2200kB disk space will be freed.
Do you want to continue [Y/n]?

```

Hmm... it doesn't even mention the linux-image in there.

---

### Post by jesse on 2005-08-20
Yes, that's bizzare. You would think it would list a linux-image. I don't recomment saying yest just yet. Let's have another look at your sources.list. I'll post mine.

---

### Post by jesse on 2005-08-20
Wait! I looked at mine, and it appears you are indeed missing repos. 

Here's mine. 

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

Do you have all of this?

---

### Post by jesse on 2005-08-20
I think you truly were missing repos and we didn't notice it. Try pasting mine to your /mnt/linux/etc/apt/sources.list and then doing 

apt-get update
apt-get install initrd-tools 
apt-get install linux-image

again. 

The third should show you a list of options that will include the one for linux-image-2.6.12-7-686

Sorry I didn't notice your missing repos before.

---

### Post by alaithea on 2005-08-20
Yep, I was missing these, from the very top of your file:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restrict

```

It's installing the 2.6.12 image now.

---

### Post by jesse on 2005-08-20
Praise the Lord! 

Did it also install a new initrd-tools? 

I don't think it really matters though as long as it's installing the linux-image, but you should definitely try installing initrd-tools before you reboot. 

I'm curious about your reboot.

---

### Post by alaithea on 2005-08-20
Yes, before I installed the linux-image, I installed a new initrd-tools.

Okay, more fun. On reboot, with my new kernel, I get:

```

Uncompressing Linux... Ok, booting the kernel.
[numbers] audit(numbers):initialized
/init: 59: cannot open /sys/bus/scsi/devices/*/type: No such file
  Unable to find volume group "hda1"
ALERT! /dev/hda1 does not exist. Dropping to a shell!

BusyBox v1.00-pre10 (Debian 20040623-1ubuntu19) Built-in shell(ash)

/bin/sh: can't access tty; job control turned off
#

```

Wonders never cease... But thank you for helping me at least get this far. :)

---

### Post by jesse on 2005-08-20
Ok. That stumps me. I wouldn't give up yet though. 

I assume you rebooted without the cd of course. (I know, dumb question). 

Sometimes you have to reboot a second time after you upgrade a kernel, so just try rebooting again and see what happens. At least it's not the kernel panic any more. Now that your at least getting a terminal when you boot means you should be able to fix it eventually with the help of this forum.  

I'll check in on this forum later, but I'm going to call it a night.

---

### Post by alaithea on 2005-08-20
Alright, thanks again. I'll keep looking.

(I tried several times to reboot, without the CD.)

---

### Post by jesse on 2005-08-20
One thought. When I successfully rescued my system from a kernel panic, I installed linux-image-2.6.12-4-686 (rather than 7-686). Maybe you can go back into the live cd and try removing 7 and installing 4 and then rebooting again.

---

### Post by alaithea on 2005-08-21
Just so nobody spends any more time worrying about my problem... it progressed worse and worse (I decided to back up files and re-install, but after unsuccessfully trying to use Puppy Linux on a USB Flash Drive, so I could use my CDR for backup, I could no longer mount /dev/hda1 at all)... until I just reformatted and reinstalled. *sigh* Now i just wish I could really trust the Ubuntu updates. What repository did that kernel update come from? Could I have avoided this by sticking with more standard repositories in my sources?

---

### Post by Czubek on 2005-08-21
[QUOTE=jesse]One thought. When I successfully rescued my system from a kernel panic, I installed linux-image-2.6.12-4-686 (rather than 7-686). Maybe you can go back into the live cd and try removing 7 and installing 4 and then rebooting again.[/QUOTE]
There are only those images avalible:
linux-image-2.6.12-7-k7-smp 2.6.12-7.11
  linux-image-2.6.12-7-k7 2.6.12-7.11
  linux-image-2.6.12-7-686-smp 2.6.12-7.11
  linux-image-2.6.12-7-686 2.6.12-7.11
  linux-image-2.6.12-7-386 2.6.12-7.11
  linux-image-2.6.10-5-k7-smp 2.6.10-34.4
  linux-image-2.6.10-5-k7 2.6.10-34.4
  linux-image-2.6.10-5-686-smp 2.6.10-34.4
  linux-image-2.6.10-5-686 2.6.10-34.4
  linux-image-2.6.10-5-386 2.6.10-34.4
  linux-image-2.6.11-1-k7-smp 2.6.11-0.2
  linux-image-2.6.11-1-k7 2.6.11-0.2
  linux-image-2.6.11-1-686-smp 2.6.11-0.2
  linux-image-2.6.11-1-686 2.6.11-0.2
  linux-image-2.6.11-1-386 2.6.11-0.2
I will try with: linux-image-2.6.12-7-686
Thanks jessie

---

### Post by raakken on 2005-08-21
Hi, I still have the same problem.
When I type gedit /mnt/linux/etc/apt/sources.list I get this error:
GnomeUI-WARNING**: while connecting to session manager: authentication rejected, reason: not of the authentcation protocols spesified are supported and host-based authentication fail

and then it opens gedit, and at the bottom line it says: sources.list CREATED and it's a blank page(booth in root and normal terminal, root didn't let me enter gedit.... strange) BUT, from there I can open(with the OPEN button) the doc sources.list(which I have two of now...) and I do the changes. I exit the terminal, use the one that's been open all the time and enters apt-get update, then this error comes:
E: Opening /etc/apt/sources.list - ifstream::ifstream (5 input/output error)

just for fun I entered /mnt/linux/etc/apt/ in my filesystem, and there's a source.list and a sources.list (it's a file with a pic of the gnome-foot or what you will call it, and a sources.list_backup witch is a real textdoc.

what am I missing? please help me if someone can
thanks

---

### Post by Czubek on 2005-08-21
[QUOTE=Czubek]
I will try with: linux-image-2.6.12-7-686
[/QUOTE]
As I said I did, but it not affect my Grub config and I still have only my old broken kernel. I don't know what to do now.
Maybe its a problem:
My "/" partition is hda8, "boot" is hda6 and it wasn't mounted when I was installing new image with apt. How should I mount it before I apt-get reinstall?

---

### Post by raakken on 2005-08-21
well, big thanks to jesse(?), I owe you bigtime mate!
Can't get x running, but I bet that's peanuts :razz: compared

---

### Post by jesse on 2005-08-21
I give up on trying to be of assistance and didn't mean to cause anyone any problems. I only wrote about what solved the problem for me when I had the same problem with a kernel panic. 

I think the kernel update that's causing the problem in the first place is in one of the Hoary security repositories.

---

### Post by raakken on 2005-08-22
[QUOTE=jesse]I give up on trying to be of assistance and didn't mean to cause anyone any problems. I only wrote about what solved the problem for me when I had the same problem with a kernel panic. 

I think the kernel update that's causing the problem in the first place is in one of the Hoary security repositories.[/QUOTE]
  cause anyone any problems?  you saved my computer man! that rocks

---

### Post by mikalh on 2005-08-22
Thanks Jesse, I manage to boot using the Breezy kernel too.  I first tried the 686 version of the 'bad' kernel but that didn't work...

However, X didn't work for me either. Eventually I just backed everything up, purged the system, and installed a complete Breezy AMD64, which is working fine at the moment. It's a development install, so cutting edge libraries suit me fine. Indeed, it already had Breezy's libc6 at the time of failure; I wonder if this might be the cause of the problems...?

Funnily, it also has the problem of not finding volume group 'sda3' during boot, though that's definately my root partition, but it copes with it and seems to work fine.

---

### Post by jesse on 2005-08-22
[QUOTE=raakken]cause anyone any problems?  you saved my computer man! that rocks[/QUOTE]


But did you ever get X working. I'm sure there's a way to but unfortunately I don't know the way. My X worked fine after I upgraded my kernel when I had the kernel panic problem. Of course what I upgraded to at the time was linux-image 2.12-4 and I don't think that's even in the repository any more. 

I'm afraid to fully upgrade my system to Breezy since it's still in development and I would hate for everything to break. The mostly Hoary mixture I have now works for me.

---

### Post by stoffe on 2005-08-22
My X refused to work as well, due to nvidia drivers missing or not compatible... also, my network card refused to work for some reason. Going back in, installing nvidia-glx - which demands the 386 version of the kernel instead of 686 at least for me - and booting with the 386 version seems to have solved most or all problems for me: I'm back in and everything seems normal (though I had some odd warnings at boot time).

Hope that helps anyone, I got helped by these posts at least! =)

---

### Post by raakken on 2005-08-23
[QUOTE=stoffe]My X refused to work as well, due to nvidia drivers missing or not compatible... also, my network card refused to work for some reason. Going back in, installing nvidia-glx - which demands the 386 version of the kernel instead of 686 at least for me - and booting with the 386 version seems to have solved most or all problems for me: I'm back in and everything seems normal (though I had some odd warnings at boot time).

Hope that helps anyone, I got helped by these posts at least! =)[/QUOTE]
 atp-get install nvidia-glx ?? and then it worked?
jesse: well, I'm working on it:) and learning a bunch

---

### Post by stoffe on 2005-08-23
[QUOTE=raakken]atp-get install nvidia-glx ?? and then it worked?[/QUOTE]

Yup. Including the other stuff it wants to pull with it, in my case including another kernel... remeber to boot with that kernel, too. =) Of course, this (probably) only applies if you have a Nvidia card and were using the binary drivers before this happened.

---

### Post by zeka on 2005-10-10
hi
if i type mount /dev/hda3 /mnt/linux (ROOT terminal on live cd)
then says "wrong fs type...."
my fdisk shows
....
/dev/hda3    Linux
....

help needed???
--------------------------
Solved

i solved the probel by typing mount -t ext3 /dev/hda3 /mnt/linux

---

### Post by wishyjr on 2005-10-24
hi there, which kernel would you recommend for an amd64 user? im going through the process of installing the new kernel but it doesnt have an image thats 2.6.12-4-amd64.. is there one?

ta

---

