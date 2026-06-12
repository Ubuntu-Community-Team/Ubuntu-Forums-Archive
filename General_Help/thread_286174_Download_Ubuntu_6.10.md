---
title: "Download Ubuntu 6.10"
date: 2006-10-27
forum: General Help
---

### Post by XP1 on 2006-10-27
Where can I find the download to the Ubuntu 6.10 DVD?
File: ubuntu-6.10-dvd-i386.iso

---

### Post by Choad on 2006-10-27
there is no dvd version (edit: afaik)

---

### Post by brianfast on 2006-10-27
> **Choad said:**
> there is no dvd version (edit: afaik)
Why?

---

### Post by Choad on 2006-10-27
because it all fits on a cd

---

### Post by XP1 on 2006-10-27
> **Choad said:**
> there is no dvd version (edit: afaik)

There will never be? :(

---

### Post by Choad on 2006-10-27
why would there be? what more do you want?

---

### Post by Pinoy915 on 2006-10-27
It's good to keep it on CD. That means it's not super bloated and any other add ons can be downloaded.

---

### Post by ianmacgregor on 2006-10-27
And I hope it never changes too. One of the reasons I switched from Fedora is that I don't really feel like downloading 5 cd's.

---

### Post by XP1 on 2006-10-27
> **Choad said:**
> why would there be? what more do you want?

I was thinking like an extras disc where the DVD includes something that the CD version does not.
From the 6.06.1 version DVD:
The combined install/live DVD allows you either to install Ubuntu permanently on a computer, or (by entering 'live' at the boot prompt) to try Ubuntu without changing your computer at all.

> **Pinoy915 said:**
> It's good to keep it on CD. That means it's not super bloated and any other add ons can be downloaded.

I like having all the addons/extras installed because I don't like having to install something everytime to get what I want. If I can have it on the hard drive ready to go, why have time wasted installing it?
It's like comparing Firefox to Opera. Firefox is a bare browser which can have addons/extensions added and Opera is a feature rich browser with everything included. For the same reason, I prefer Opera because I don't have to go searching for it when I need it.

Everybody has thier own preferences. What I'm hoping for is a choice.

---

### Post by XP1 on 2006-10-27
> **ianmacgregor said:**
> And I hope it never changes too. One of the reasons I switched from Fedora is that I don't really feel like downloading 5 cd's.

I'm not saying I'd like the bare install to be 5 CDs or something like that. The DVD versions includes the live option. Making a choice between them is why I started this topic.

---

### Post by skymt on 2006-10-27
I think the DVD version comes out a bit later. It should be up within a week.

---

### Post by ianmacgregor on 2006-10-27
> **XP1 said:**
> ... why have time wasted installing it?


You have to "install" it one way or another.. whether from the cd or via sudo apt-get install :) If Ubuntu went to several cd's, I would probably move to another distro, and I'll bet others would too. 

You can do what I did, find the apps you like and make a script that installs them all:

ex.
```

#!/bin/bash

sudo aptitude install firestarter mozilla-thunderbird 3ddesktop gftp revelation seahorse irssi

```

---

### Post by XP1 on 2006-10-27
> **skymt said:**
> I think the DVD version comes out a bit later. It should be up within a week.

Good to hear. I'll be waiting. :) 

> **ianmacgregor said:**
> You have to "install" it one way or another.. whether from the cd or via sudo apt-get install :) If Ubuntu went to several cd's, I would probably move to another distro, and I'll bet others would too. 


Having them already downloaded on disc that installs itself during the system installation is better than downloading them from the Internet afterwards IMO.
I don't want the bare Ubuntu to make seperate CDs, I just want the DVD like with version 6.06.1. ;) 

> **ianmacgregor said:**
> You can do what I did, find the apps you like and make a script that installs them all:

ex.
```

#!/bin/bash

sudo aptitude install firestarter mozilla-thunderbird 3ddesktop gftp revelation seahorse irssi

```

Hmm, maybe I'll try that sometime.

---

### Post by vbgunz on 2006-10-27
I never downloaded the dvd and failed to find any info about it. I would like one if it provides all repos on it for offline usage. Is this the case because if so, I would like my repos offline when possible. Anyone know if this is the case?

---

### Post by ianmacgregor on 2006-10-27
> **XP1 said:**
> Good to hear. I'll be waiting. :) 



Hmm, maybe I'll try that sometime.

Here's is a excerpt from my master2.sh script

```

#!/bin/bash
#

# Check for admin rights, refuse to run if not an admin user
if [ $UID != 0 ]
then
   echo "You need to be root to run this script! Exiting.."
   exit
fi

sudo aptitude install firestarter numlockx sysv-rc-conf irssi xmms
xmms-cdread xmms-skins gkrellm gkrellm-alltraxclock2 gkrellmms
gkrellm-volume gkrellweather grip lame easytag xchat mcrypt
libnotify-bin gnome-schedule seahorse revelation gnomebaker elinks
gftp gimp-data-extras gimp-helpbrowser gimp-help-en gimp-svg meld
imagemagick 

```

I have three master scripts, actually.. one tweaks the system, one uninstalls unneeded apps and installs desired apps, he other is a clean up script. This is why installing Ubuntu on a fresh hard drive takes no more than an hour. Install the distro, run the scripts and go have lunch :)

---

### Post by Henry Rayker on 2006-10-27
The CD has the live feature too...you can run from just the CD...

Also, I prefer not having them all on one disk because, if you reinstall so frequently, you'll probably just have old packages on the disk. They'll have to be downloaded and updated just the same.

Also, I think maybe a reason the for the 6.06.1 DVD might have been the LTS status of that release...I have doubts that a DVD will definitely be available for 6.10...

---

### Post by ianmacgregor on 2006-10-27
> **Henry Rayker said:**
> Also, I prefer not having them all on one disk because, if you reinstall so frequently, you'll probably just have old packages on the disk. They'll have to be downloaded and updated just the same.


That's a very good point.

---

### Post by XP1 on 2006-10-27
Hmm, I think I found it but it says "Daily Build" and may not be the final version.
[http://cdimage.ubuntulinux.org/dvd/current/]("http://cdimage.ubuntulinux.org/dvd/current/")

DVD:
[http://cdimage.ubuntulinux.org/dvd/current/edgy-dvd-i386.iso](http://cdimage.ubuntulinux.org/dvd/current/edgy-dvd-i386.iso)

> **vbgunz said:**
> I never downloaded the dvd and failed to find any info about it. I would like one if it provides all repos on it for offline usage. Is this the case because if so, I would like my repos offline when possible. Anyone know if this is the case?

Not sure but this site may hold the answer:
[http://cargol.net/~ramon/ubuntu-dvd-en]("http://cargol.net/~ramon/ubuntu-dvd-en")

"Ubuntu doesn't offer DVDs ready to download with its main, universe and multiverse repositories. With the contents of this howto you can do it yourself and, for those not able to or not willing to do all the stuff here, I have prepared the DVD images ready to download as .torrent files."

> **Henry Rayker said:**
> The CD has the live feature too...you can run from just the CD...
Never tried the CD version myself so I never knew. :o 
I supposed the CD version didn't have the live option becuase of how the DVD description was written, so I've always downloaded the DVD version.

> **Henry Rayker said:**
> Also, I prefer not having them all on one disk because, if you reinstall so frequently, you'll probably just have old packages on the disk. They'll have to be downloaded and updated just the same.
True

> **Henry Rayker said:**
> Also, I think maybe a reason the for the 6.06.1 DVD might have been the LTS status of that release...I have doubts that a DVD will definitely be available for 6.10...

Maybe, we'll see. ;)

---

### Post by KillerBOB on 2006-10-27
As a matter of fact there is a DVD-version of Ubuntu even this time.
Find it here
[http://cdimages.ubuntu.com/releases/edgy/release/](http://cdimages.ubuntu.com/releases/edgy/release/)

---

### Post by XP1 on 2006-10-27
> **KillerBOB said:**
> As a matter of fact there is a DVD-version of Ubuntu even this time.
Find it here
[http://cdimages.ubuntu.com/releases/edgy/release/](http://cdimages.ubuntu.com/releases/edgy/release/)

Thanks, but the site is loading very slowly.

---

### Post by Aditz on 2006-10-27
Have a look at [http://torrent.ubuntu.com/releases/edgy/release/dvd/](http://torrent.ubuntu.com/releases/edgy/release/dvd/)

---

### Post by KillerBOB on 2006-10-27
Yes I noticed that it is very slow =(. I downloaded the torrent from there on the day of Edgy's launch. I'm also seeding (along with lots of others) so I think you should try the torrent

---

### Post by jocko on 2006-10-27
> **XP1 said:**
> Thanks, but the site is loading very slowly.

I think if you want to find a good mirror you'll have to say where you are.
If you're in northern europe try [this]("ftp://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/edgy/release"). It's really quick for me (but then again it's hosted on a server on my campus)

---

### Post by XP1 on 2006-10-27
> **Aditz said:**
> Have a look at [http://torrent.ubuntu.com/releases/edgy/release/dvd/](http://torrent.ubuntu.com/releases/edgy/release/dvd/)

Thanks, using torrent now.

> **KillerBOB said:**
> Yes I noticed that it is very slow =(. I downloaded the torrent from there on the day of Edgy's launch. I'm also seeding (along with lots of others) so I think you should try the torrent

The torrent is much faster and still speeding up. :D 

> **jocko said:**
> I think if you want to find a good mirror you'll have to say where you are.
If you're in northern europe try [this]("ftp://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/edgy/release"). It's really quick for me (but then again it's hosted on a server on my campus)

Yes, it works but it is still slower than the torrent. The torrent is working fine so I'll stick with the torrent for now.

---

### Post by FirePrince on 2006-10-27
DVD have an higher transfer rate than CD, so to have Ubuntu on a DVD means speeder boot time using live version and speeder setup.

---

### Post by XP1 on 2006-10-27
> **FirePrince said:**
> DVD have an higher transfer rate than CD, so to have Ubuntu on a DVD means speeder boot time using live version and speeder setup.

One more reason I'll be using the DVD version :)

Finished downloading the DVD, I'll be sure to seed :D

---

