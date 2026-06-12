---
title: "A beginner to Ubuntu... but not a beginner to pcs... read my long list of agony."
date: 2007-04-23
forum: General Help
---

### Post by Zellio on 2007-04-23
So I have this old Celeron 500... I decided I wanted to give it Ubuntu!

So in order to do that, it needs an OS.

I have an 11 gig hdd, perfect.  But I equip it, dead!

So I can only use my old 4 gig hdd...

It has Win98 on it.  I update it to Xp Home Upgrade.  I then go to download ubuntu 6.06 (Yes, at the time it was 6.06).

I rip it in one of the newer pcs, and put it on the old pc... But the old thing is so old the cdrom doesn't read burnt cds!

The second cdrom reads burnt cds and destroys them, I took it out immediately :( 

So, not really wanting to take another pc off and put a dvd or cd rom/rw in it, I put this idea on hiatus for a month, putting music on the thing instead.  After a month, I go back to the idea.  This time, I try to download ubuntu.  But it won't read it :confused: 

So I FINALLY add a real dvd drive to it, and of course, I come to find THE 4 GIG DRIVE IS TOO SMALL.

But this is an old emachines, with the wierd configuration.  So I end up getting a 5.25 enclosure, and putting a 30 gig drive in...

But, since I'm booting from the 4 gig drive, it won't boot up from the 4 gig drive!

SO...  I gotta copy to the 30 gig drive, and since the 4 gig drive is pio and very old.......... it took hours.  I finally get it to copy when windows is all screwed up.  So I reinstall windows to find I can't reinstall my cd key.  So I decide, now is the time, I have my 7.04 cd copied from the ubuntu site, time to install.

I also add my old edtv to this setup, so I can watch dvds on it.  It's a 20" tv at 800x600...  Didn't know the problems THAT would cause...

I first boot it up, couldn't get a picture... kept reseting... finally plugged in my old crt, figured out it's set to automatically boot at 1024x768, and my lcd doesnt support it.  So I gotta install from the crt.

So I install the 7.04.  It doesn't pick up my wireless usb adapter.  After a few reboots, it... dies.  It wouldn't load, and then just gives a blnak screen.

So I have a 6.10 cd from old, and go back to it.  It picks up my wireless adapter, but can't connect.  I decide, by some stupidity, I should go back to 7.04!

So I do.  And OMG, It's picking up my wireless usb adapter (???), and it works now (???), so I go to try to configure my wireless adapter... and...

I have my router set for PPPOE, which is a problem to begin with, so I dunno what to do.

Anyways, I first try to configure my adapter, no luck.  I then download a pppoe configuration tool, no luck.  I then try to pppoeconf, no luck.  I then try to config for wpa, still no luck.

The problem is, I can't get online to download the repositories to add universe and multiverse to ubuntu, which apparantly, going online is required to get these, even if you can't.

I tried downloading these files off the bs ubuntu site, and it wouldn't let me.

I'm seriously fed up with this.

Is there anyway I could download repositories, or make this work without the repositories being on, just somehow get this thing working?  I'd like to get this working and I can't seem to.

Just as an example, I've tried these two guides:

[http://www.ubuntux.org/how-to-install-broadband-adsl-pppoe-client-rp-pppoe](http://www.ubuntux.org/how-to-install-broadband-adsl-pppoe-client-rp-pppoe)

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Neither work, and I understand why because I can't enable repositories, but at the same time I can't go online to get them >_<

---

### Post by hardyn on 2007-04-23
I kinda understand what you are trying to do... but you HAD to expect finding a bunch of old questionable condition parts would not go smoothly... i mean you started a project and thats what you got; you were hoping for compututing alchemy i guess?

what is your utimate goal?

maybe look around for used machines that are a little better than a celeron 500... last year i flipped two AMD 1800s for 80$ and 125$ with a monitor... i didn't want them anymore, and i would rather see them loved, than go to waste... so deals are out there. 

soo... come up with a plan... watch the papers/craigs list/local recyclers/buy and sell... and see what you can do.

good luck.

---

### Post by Zellio on 2007-04-23
Heh, I have better machines, and if ubuntu somehow goes better, I may put it on them as well ;).

Right now they are running Vista.  That could be added too.

I only added it to my old machine because this was all it could run, and I wanted a nice looking os for it.

All I really have this machine set up as is a music player and a dvd player.  I'm starting to like Ubuntu though, I may put it on another machine or two.  Tell me it's not as hard to install on newer machines?

I could easily dual boot in Vista by simply taking out the hard drive vista has and then installing ubuntu, and then putting the vista hard drive back in.  I'd hard switch hard drives in bios every time I'd wanna load between ubuntu and vista, not a problem.

EDIT:  Would also hafta kill the little thing Vista uses to start up itself every time.

---

### Post by hardyn on 2007-04-23
naww... its as easy as windows... IF your hardware is compatible... ergo... stay mainstream and not bleeding edge.

why not dual boot on the same drive?  i do it... its great...  i use ubuntu 99% of the time, but i have a few windows only applications.

---

### Post by MacD on 2007-04-23
try xubuntu- works much better on slower machines.  I'm not sure about the HD requirement, though?

---

### Post by Zellio on 2007-04-23
I give up.

I'm gonna put in a ethernet port from an even earlier pc (Yes friends, this pc, doesn't have an ethernet port!), in it and connect it directly to the router, and download like that, then return it and use pppoe.  This is going nowhere.

---

### Post by mr_niceguy on 2007-04-23
Welcome to the world of consumer rights. :) Believe it or not, this issue is related to the same battle that occurred a short generation ago when auto manufacturers were resisting demand to put seatbelts in all their cars. Who exactly benefited from a lack of seatbelts? A few bucks worth of equipment and we can keep people from flying through the windsheild. But Nader et. al. fought until consumers got their rights.

While it is not the same manner of life and death issue, hardware support is one of the major areas where you see the grip of the Microsoft monopoly in action. A lot of vendors only supply closed drivers and only for Windows. Again, it is difficult to see anyone who clearly benefits. Fortunately there are some hardware vendors who do not punish their customers and supply open specs. These Linux can support. There are also some drivers which have simply been reverse engineered. 

When building a Linux box you can save a lot of pain if you first do a search for supported hardware. Fortunately there are lists for hardware which is compatible with Ubuntu. As Ubuntu grows that puts pressure on hardware vendors. Some are already coming on board, some are still resisting. But every one of us who purchases hardware from cooperating vendors is making a statement that we will not be denied our rights. And we will stand by those who respect our rights.

[Ubuntu Hardware Support](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by jpatton on 2007-04-23
> **Zellio said:**
> So I have this old Celeron 500... I decided I wanted to give it Ubuntu!

So in order to do that, it needs an OS.

I have an 11 gig hdd, perfect.  But I equip it, dead!

So I can only use my old 4 gig hdd...

It has Win98 on it.  I update it to Xp Home Upgrade.  I then go to download ubuntu 6.06 (Yes, at the time it was 6.06).

I rip it in one of the newer pcs, and put it on the old pc... But the old thing is so old the cdrom doesn't read burnt cds!

The second cdrom reads burnt cds and destroys them, I took it out immediately :( 

So, not really wanting to take another pc off and put a dvd or cd rom/rw in it, I put this idea on hiatus for a month, putting music on the thing instead.  After a month, I go back to the idea.  This time, I try to download ubuntu.  But it won't read it :confused: 

So I FINALLY add a real dvd drive to it, and of course, I come to find THE 4 GIG DRIVE IS TOO SMALL.

But this is an old emachines, with the wierd configuration.  So I end up getting a 5.25 enclosure, and putting a 30 gig drive in...

But, since I'm booting from the 4 gig drive, it won't boot up from the 4 gig drive!

SO...  I gotta copy to the 30 gig drive, and since the 4 gig drive is pio and very old.......... it took hours.  I finally get it to copy when windows is all screwed up.  So I reinstall windows to find I can't reinstall my cd key.  So I decide, now is the time, I have my 7.04 cd copied from the ubuntu site, time to install.

I also add my old edtv to this setup, so I can watch dvds on it.  It's a 20" tv at 800x600...  Didn't know the problems THAT would cause...

I first boot it up, couldn't get a picture... kept reseting... finally plugged in my old crt, figured out it's set to automatically boot at 1024x768, and my lcd doesnt support it.  So I gotta install from the crt.

So I install the 7.04.  It doesn't pick up my wireless usb adapter.  After a few reboots, it... dies.  It wouldn't load, and then just gives a blnak screen.

So I have a 6.10 cd from old, and go back to it.  It picks up my wireless adapter, but can't connect.  I decide, by some stupidity, I should go back to 7.04!

So I do.  And OMG, It's picking up my wireless usb adapter (???), and it works now (???), so I go to try to configure my wireless adapter... and...

I have my router set for PPPOE, which is a problem to begin with, so I dunno what to do.

Anyways, I first try to configure my adapter, no luck.  I then download a pppoe configuration tool, no luck.  I then try to pppoeconf, no luck.  I then try to config for wpa, still no luck.

The problem is, I can't get online to download the repositories to add universe and multiverse to ubuntu, which apparantly, going online is required to get these, even if you can't.

I tried downloading these files off the bs ubuntu site, and it wouldn't let me.

I'm seriously fed up with this.

Is there anyway I could download repositories, or make this work without the repositories being on, just somehow get this thing working?  I'd like to get this working and I can't seem to.

Just as an example, I've tried these two guides:

[http://www.ubuntux.org/how-to-install-broadband-adsl-pppoe-client-rp-pppoe](http://www.ubuntux.org/how-to-install-broadband-adsl-pppoe-client-rp-pppoe)

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Neither work, and I understand why because I can't enable repositories, but at the same time I can't go online to get them >_<

What a great story! Not that I have one better, but I certainly have installed Fiesty on a MUCH older machine, I installed Fiesty on a dual pentium pro micron machine! It's so old, the only boot options in the bios are Floppy and Hard-drive! lol...look for the post's here:

[http://ubuntuforums.org/showthread.php?t=415905](http://ubuntuforums.org/showthread.php?t=415905)

I had to download this really cool boot disk that let me boot to the cdrom, and for me the install went fine. I installed the server because this box will host my backups and such and i didn't want any extra garbage on it. 

Good Luck!

---

