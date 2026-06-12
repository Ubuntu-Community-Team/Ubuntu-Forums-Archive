---
title: "should i get Desktop or Server?"
date: 2007-01-05
forum: General Help
---

### Post by erv2 on 2007-01-05
Hi,

i am a totally newbie in the linux world, although i use suse at work and know some basic commands for the terminal.

i want to built a small family network using linux (file server, mail server, dns, dynamic DNS client),and also i need a server for me to play around Ruby on Rails.

i have a wireless router, i am not so sure if i can turn it into an AP then use the linux server to get more control, like DHCP, connection per ip address

now comes the question:
i want both Desktop and the Server solution, can i install the Desktop cd then install the server package? is it easy to install? 

according to my spec, which version of ubuntu should i get, is there anything known compatibility problem?

my spec is:
AMD64 3000+
2G RAM
80G Barracuda PATA
160G Baracuda SATA
320G Baracuda SATA 
6200 Turbo Cache Graphic card
3com network card (onboard one doesn't work)
SB Audigy sound card

thanks everyone.

---

### Post by madmetal on 2007-01-05
i suggest installing 6.10 desktop and you will be fine!
i am afraid SB audigy might create you problems...:-k  (although i hope not :cool: )

---

### Post by _simon_ on 2007-01-05
Audigy card should be fine, I run an Audigy 2 ZS.

---

### Post by PetePete on 2007-01-05
the difference between server and desktop is that desktop includes GUI's (KDE, gnome etc) and obviously all the desktop software which you would need. whereas server, funnely enough, contains all the various network services which you would need. But behind them both is the same ubuntu system.

if you have a spare old computer, use that as the server and install ubuntu server on it and it should run fine :)

---

### Post by The_Apprentice on 2007-01-05
I had the same thoughts when I first wanted to install Ubuntu.
I was replacing a Windows 2000 Server with a website and mail server on it.

Everyone said install the Desktop version, which I did.
I then had to think about installing PHP, mySQL, etc.  This was a mare for a n00b, so I went for XAMPP which was a breeze to install, but does not update/patch itself.

A few months later I decided to install a server at work, and this time went for the server installation, which installed PHP, mySQL etc for me.
Needless to say it does not install a desktop, but this can easily be done (see: [http://www.ubuntuforums.org/showthread.php?t=186298](http://www.ubuntuforums.org/showthread.php?t=186298))

You should now have a pretty complete server install that patches itself.

EDIT:
btw, I will be re-installing my server tonight/this weekend so should have refreshed my memory of any issues I had (like getting the correct screen config).
I'll keep an eye on the forums whilst I am at it.

Why am I re-installing?
'cos I over wrote my sources.list with an edgy one (by mistake/not thinking) and did a "apt-get update" and "apt-get upgrade".
Needless to say things went a bit downhill after that  :$

---

### Post by erv2 on 2007-01-05
do i have to get the AMD64bit version? or i can just use the i386 without any trouble? how much faster will the 64bit be? if it's not like a 20-30% advantage, why would i half my memory for using it?

plus, is there plenty of 64bit software to use, or the 64bit version can run 32bit software with no problem?

thanks.

---

### Post by vladanian on 2007-01-05
I think one good way to go is to install VMware Player or VMware Server, both of which are free, and run your headless edgy or dapper server from a vm,  If you use vmware server, you can make a snapshot and revert to it if you screw things up -- that's good for messing around...

---

### Post by The_Apprentice on 2007-01-05
Just to say that the install was a breeze.

I chose to DHCP my NIC, then I set static IP settings in /etc/network/interfaces and the DNS settings in /etc/resolv.conf
(Well I think that was the names/paths)

I installed the Gnome desktop using the thread I mentioned, but that installs a vanilla gnome desktop.

I decided to uninstall that and I am now installing the ubuntu-desktop metapack.
sudo apt-get install ubuntu-desktop

All in all about 2 hours work, one hour either side of watching the last episode of Torchwood (a Dr Who spin-off).

Needless to say I will need to tidy up the installation and set up some of the finer points, but the base server is running.

---

### Post by NumberOne on 2007-01-05
I installed the 6.10 LAMP server, then installed the ubuntu desktop.  The LAMP install sets up all basic server components for you (except for FTP and Mail server).  It was very esay this way.

---

