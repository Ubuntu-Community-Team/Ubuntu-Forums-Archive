---
title: "Need To speed up machine!!"
date: 2008-03-21
forum: General Help
---

### Post by Raccoon1400 on 2008-03-21
I have a 700MHz PIII , 128MB RAM laptop.
I just installed fluxbuntu with XFCE. I need to speed it up a large amount, because it is very sluggish.
I cleaned up startup with bum startup manager. Anything else? Resolution is 1024x768. Would lowering that or using a vesa driver help? Disabling more startup items?

left enabled:
hal
dbus
cupsys
makedev
avahi-daemon
gdm
cron

---

### Post by sports fan Matt on 2008-03-21
With only 128 mb Ram, have you looked at Puppy Linux or Damn Small Iinux (DSL)?

---

### Post by uberlube on 2008-03-21
I second the DSL, and also Wlovix Cub might be good for you.

---

### Post by sports fan Matt on 2008-03-21
Here is DSL: [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by kerry_s on 2008-03-21
> **Raccoon1400 said:**
> I have a 700MHz PIII , 128MB RAM laptop.
I just installed fluxbuntu with XFCE. I need to speed it up a large amount, because it is very sluggish.
I cleaned up startup with bum startup manager. Anything else? Resolution is 1024x768. Would lowering that or using a vesa driver help? Disabling more startup items?

left enabled:
hal
dbus
cupsys
makedev
avahi-daemon
gdm
cron


dude, go custom start from the ground up it's easier to control what's installed.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

debian, would be faster on those specs.

---

### Post by Raccoon1400 on 2008-03-21
> **kerry_s said:**
> 
debian, would be faster on those specs.
The newest release?

---

### Post by tenach on 2008-03-21
> **sox fan Matt said:**
> With only 128 mb Ram, have you looked at Puppy Linux or Damn Small Iinux (DSL)?

I third DSL from experience running it on a Pentium III 500MHz, 64mb RAM.  It's faster than any Microsoft product I've put on it.

---

### Post by kerry_s on 2008-03-21
> **Raccoon1400 said:**
> The newest release?

yeap.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

base install, that means when it gets to the package selection part uncheck both/all.

log in as root
apt-get install xorg gdm synaptic xfce4
reboot(ctrl+alt+delete)

log in as the user you made
open synaptic and continue installing what you want.

if you want newer stuff add the lenny repo, the lines are exactly the same as the etch lines, but you change etch to lenny. i just changed the src repo's to lenny.

why xfce4? you should go as light as you can.

here's my repo's->
```
deb http://ftp.us.debian.org/debian/ etch main contrib non-free
deb http://ftp.us.debian.org/debian/ lenny main contrib non-free

deb http://security.debian.org/ etch/updates main contrib non-free
deb http://security.debian.org/ lenny/updates main contrib non-free

deb http://www.debian-multimedia.org lenny main

```

i use jwm for my wm like in dsl, my laptops 450mhz 256mb ram.
mines built for speed, no frills. :)

---

### Post by FakeOutdoorsman on 2008-03-22
DSL and Puppy will work, but they are ugly.  Get the Ubuntu alternate disc or [Ubuntu minimal disc]("https://help.ubuntu.com/community/Installation/MinimalCD") and do a "command-line install".  From these you can build up: installing only what you want.  I once did a custom Ubuntu install for an ancient Toughbook with 128 MB ram.  It wasn't the fastest beast in town, but it worked just fine.  Debian should be similar to install and would be a bit faster due to less "baggage" in the minimal install.  I've also used Wolvix Cub which is nice.

Another good choice is [Arch Linux]("http://archlinux.org/"), which has a "keep it simple" approach and is optimized for post-386 processors. I just installed it on a 400 MHz 256 MB Dell Latitude LS.  You will need a little more Linux experience to install Arch, but you'll definately learn a lot.  Arch and Ubuntu are my favorites.

 I prefer Openbox (without a desktop manager like Gnome or KDE) as a windows manager: it's clean, simple, fast, and customizable.  You can also add a panel like [lxpanel]("http://www.gnomefiles.org/app.php/LXPanel"), pypanel, fbpanel, etc.
[URL="https://help.ubuntu.com/community/Installation/LowMemorySystems"]
Installation on Low Memory Systems[/URL] [Ubuntu Wiki]
[Lightweight Gnome]("http://ubuntuforums.org/showthread.php?t=298835") [Ubuntu Forums]
[Urukrama&#8217;s Openbox guide for Ubuntu]("http://urukrama.wordpress.com/openbox-guide/")
[Howto: Set up Gutsy for speed, v1.2]("http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/")

---

### Post by Raccoon1400 on 2008-03-22
I am trying Puppy. It works fine on the livecd, but when I install it, the menu bar and icons don't load.

---

### Post by Raccoon1400 on 2008-03-22
Reinstalled. Works fine.

---

### Post by timzak on 2008-03-23
> **kerry_s said:**
> yeap.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

base install, that means when it gets to the package selection part uncheck both/all.

log in as root
apt-get install xorg gdm synaptic xfce4
reboot(ctrl+alt+delete)

log in as the user you made
open synaptic and continue installing what you want.

if you want newer stuff add the lenny repo, the lines are exactly the same as the etch lines, but you change etch to lenny. i just changed the src repo's to lenny.

why xfce4? you should go as light as you can.

here's my repo's->
```
deb http://ftp.us.debian.org/debian/ etch main contrib non-free
deb http://ftp.us.debian.org/debian/ lenny main contrib non-free

deb http://security.debian.org/ etch/updates main contrib non-free
deb http://security.debian.org/ lenny/updates main contrib non-free

deb http://www.debian-multimedia.org lenny main

```


Thanks for this post.  I'm installing as you outlined above on an old laptop.  Is there something else you have to do to get these repos working?  I added them to Synaptic->Settings->Repositories and I get errors when reloading:

E: Dynamic MMap ran out of room.
and a few other lines ending with "The package lists or status file could not be parsed or opened."

Thank you.

---

### Post by kerry_s on 2008-03-23
> **timzak said:**
> Thanks for this post.  I'm installing as you outlined above on an old laptop.  Is there something else you have to do to get these repos working?  I added them to Synaptic->Settings->Repositories and I get errors when reloading:

E: Dynamic MMap ran out of room.
and a few other lines ending with "The package lists or status file could not be parsed or opened."

Thank you.

uncheck the multimedia repo and try, then you can turn it back on after the lenny updates.

there is a work around for up'ing the cache, but i didn't need it, i added the multimeda repo way later.

---

### Post by kuja on 2008-03-23
I think the  #1 thing you could do to speed up a machine with tthos specs would be to put in as much memory as the MB supports. Worth every penny as cheap as RAM is anymore.

---

### Post by Raccoon1400 on 2008-03-23
I installed dsl, but can't find anything to install!
i need open office
graphical package manager

---

### Post by timzak on 2008-03-23
> **kerry_s said:**
> uncheck the multimedia repo and try, then you can turn it back on after the lenny updates.

there is a work around for up'ing the cache, but i didn't need it, i added the multimeda repo way later.

Hi, can you direct me to this workaround?  It's still not working.  After unchecking the multimedia, I still get the following:

> E: Dynamic MMap ran out of room
E: Error occurred while processing libgnome2-ruby1.8 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.debian.org_dists_lenny_updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: Cannot read vendors.list file

Could any of this be related to not having "Launch Gnome services on startup" checked under Sessions and Startup?  I was wondering if I had to check that or not.

Thanks.

---

### Post by kerry_s on 2008-03-23
have you tried unchecking the etch repos? no it's a common error, there was a limit on repo's. 
it's wierd your getting it though did you fully update from etch first?
apt-get update && apt-get dist-upgrade
then add lenny repo's, then again> apt-get update && apt-get dist-upgrade
or 
just skip the etch updates and go straight lenny

you can not just add the repo's, that's to many packages that will be new.

this is the suppose to fix it.
[B]su
apt-get update -o APT::Cache-Limit=50000000
apt-get update 
apt-get dist-upgrade
[/B]

---

### Post by timzak on 2008-03-24
Thanks, that part about upping the cache seemed to fix it...it's downloading all the upgrades right now.

Take care.

---

### Post by PCMan on 2008-03-24
> **Raccoon1400 said:**
> I have a 700MHz PIII , 128MB RAM laptop.
I just installed fluxbuntu with XFCE. I need to speed it up a large amount, because it is very sluggish.
I cleaned up startup with bum startup manager. Anything else? Resolution is 1024x768. Would lowering that or using a vesa driver help? Disabling more startup items?
left enabled:
hal
dbus
cupsys
makedev
avahi-daemon
gdm
cron

Please, you must try this.
[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)
This is the right desktop environment for you.

---

