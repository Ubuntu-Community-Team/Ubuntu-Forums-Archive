---
title: "Ubuntu on legacy system"
date: 2007-07-01
forum: General Help
---

### Post by Red Moose on 2007-07-01
How well would Ubuntu or Ubuntu Studio run on a Pentium 2 (350mHz) with 512mb ram and an ATI Radeon 7000 (64mb) compared to Debian?  I currently have Debian with Gnome installed on that system, and it's a little slow but it doesn't bother me too much.  I heard about Ubuntu Studio and I really like the looks of it.  Unfortunately, I don't have the budget to purchase a new computer at this moment.:(  I'm 15 and really into graphic design and 3d animation.:D

I hope this is the right place to post this...

Thanks, a lot!
Matt

---

### Post by meatpan on 2007-07-01
Debian + Gnome is very similar to the default ubuntu installation, so there probably won't be much of an observable speed difference.

The graphics applications are the most likely programs to slow down your system.  Consider running ubuntu with a window manager such as fluxbox.  Fluxbox is very light-weight (in terms of resource consumption) and will work well on your system.  You can install fluxbox from the main ubuntu repositories via synaptic.  

Linux is a great choice for older hardware.  I wouldn't call your system 'legacy' though... some of us might feel a bit old ;)

---

### Post by kerry_s on 2007-07-01
It will be just as slow if not slower. Why didn't you go with the xfce4 install?( [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso) ) it would have been faster on that system. If you really want speed you need to go custom and install light applications and only what you need.

i use debian+fluxbox custom install on a 450mhz 256ram. it's etch upgraded to lenny/sid.

[http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso)

[B]minimal install (uncheck everything when it comes to package selection)
login as root
apt-get install xorg gdm synaptic fluxbox
reboot(ctrl+alt+delete)
select fluxbox in the session menu and login[/B]

open synaptic and add what ever else you want.

That is for a setup that's just enough to get you a gui.

For now just add fluxbox to your current install and learn to use it.
[B]su
apt-get install fluxbox
update-menus
logout
select fluxbox from the session menu and log back in.[/B]

Just a reminder, nautilus has to be run with> **nautilus --no-desktop** or it will take over the desktop and you will lose the right click. I recommend you install a lighter faster file manager> **apt-get install emelfm ** or one of those icon based filemangers like thunar,pcmanfm, or rox.

---

### Post by Red Moose on 2007-07-02
> **meatpan said:**
> I wouldn't call your system 'legacy' though... some of us might feel a bit old ;)
Sorry, I wasn't sure how old a computer needs to be before it can be called a legacy.:)

I tried Fluxbox, and Xfce on Debian, and KDE on Freespire.  The only one I liked was Gnome.  I'm going to stick with Gnome.  I just wanted to know if Ubuntu was going to be any faster compared to Debian.  I think I'll try it and see what happens.  I may even try Ubuntu Studio.  It looked pretty cool.8-)

Thanks a million, and if anyone has any more advice feel free to give it to me!;)

Oh, one of the reasons I wanted to switch to Ubuntu, is the community!  Right now on this forum, there are 4185 active users!  After I posted, and came back a few hours later, I had to do a search to find my post!
Now, that's what I call cool!8-)

---

### Post by RedSquirrel on 2007-07-03
> **Red Moose said:**
> I tried Fluxbox, and Xfce on Debian, and KDE on Freespire.  The only one I liked was Gnome.  I'm going to stick with Gnome.  I just wanted to know if Ubuntu was going to be any faster compared to Debian.  I think I'll try it and see what happens.  I may even try Ubuntu Studio.  It looked pretty cool.8-)

I would give it a shot. At least then you can see for yourself how it feels. I doubt it would be faster (as the others have said).

And since you've tried out a lot of other setups, why not try IceWM as well...


> **Red Moose said:**
>  Oh, one of the reasons I wanted to switch to Ubuntu, is the community!  Right now on this forum, there are 4185 active users!  After I posted, and came back a few hours later, I had to do a search to find my post!
Now, that's what I call cool!8-)

That is cool. You can also setup your forum account to automatically create a subscription to any thread you create or reply to. Look under **User CP -> Edit Options** and then "Default Thread Subscription Mode". It'll save you having to search next time. ;)

There sure is a lot of [COLOR=Red]Red[/COLOR] on these forums...

---

### Post by Red Moose on 2007-07-03
Ok, cool!  I thought this thread was long-gone.:D  I've tried IceWM too.  It's not a desktop manager, it's just a window manager, right?  I didn't like it either.  

I haven't set the email subscription to default, but I usually set it when I post.

Who else is [COLOR="Red"]red[/COLOR]?

---

### Post by tgalati4 on 2007-07-04
I have Dapper installed on a PII/300 MHz machine.  It's usable but not fast.  Try Dynebolic.  I use it on the same system, booting with the Dynebolic Live CD.  This system is geared for media production with a low-latency, real-time kernel.

Ubuntu Studio may be better suited to newer hardware.  Dynebolic is optimized for older hardware.

---

### Post by Red Moose on 2007-07-04
I looked at Dynebolic.  I'm not sure if I like that it doesn't actually install to your hard drive.  I know that you can copy the folder over, but is that really the same?  Have you seen [Elive]("http://www.elivecd.org/")?  Looks to me like a really good system for older hardware.  The system requirments are:
> Minimum Requeriments: The minimum hardware for running Elive is a 100 Mhz CPU and 64 MB of RAM, but the minimum recommended hardware is 300 Mhz and 128 Mb of RAM. You don't need any special graphic card or 3D acceleration to run Elive.


Come to think of it, I can't actually install Ubuntu Studio on my computer because I don't have DVD drive.  Unless there's some way to install Ubuntu, and then upgrade to Studio

---

### Post by RedSquirrel on 2007-07-04
> **Red Moose said:**
> Ok, cool!  I thought this thread was long-gone.:D  I've tried IceWM too.  It's not a desktop manager, it's just a window manager, right?  I didn't like it either.  

Indeed, IceWM is "only" a window manager. I had a feeling that you had already tried it, but I just thought I'd toss it on the pile. ;)

> **Red Moose said:**
>  Who else is [COLOR=Red]red[/COLOR]?

Lots of users, actually. I was just being silly. :D


It seems that you can install Studio from Ubuntu feisty fawn. Have a look:

[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty)

I haven't tried it myself. I'm happy with my Ubuntu Server and Fluxbox.

I don't imagine Ubuntu Studio will "fly" on your specs, but if you have some time to kill it might be an interesting project to install it and see how responsive it is.

Have fun.

---

