---
title: "Ubuntu server or desktop as basis for home NAS?"
date: 2007-10-17
forum: General Help
---

### Post by njparton on 2007-10-17
As soon as 7.10 is released I'm going to begin buying components to build a home made headless NAS device based around an AM2 Sempron uATX setup with a 3ware 9650SE running 2xSATA drives in RAID 1 (or possibly 3 in RAID 5). I've not yet decided whether to go for the 32 or 64 bit version version of Ubuntu...

The NAS will serve as storage for documents, photos and HD video and will be connected to a gigabit switch. All computers (including the NAS) will have gigabit NICs and all sit behind a HW firewall. 

I'm planning on installing ubuntu on an 8GB CF card (connected to an IDE adapter) to save space and some heat in a small case.

My question is which of the following 2 approaches should I take in order to get as streamlined a system as possible for a NAS device:

[LIST]
[*]Ubuntu server, decline to install as a LAMP server during setup (to avoid apache, mysql and php being installed) and then install Samba, VNC server and gnome; or
[/LIST]

[LIST]
[*]Ubuntu desktop, remove all unnecessary packages, then install samba and VNC server?
[/LIST]

A minimal server install seems like a good approach, but reading around this forum seems to suggest that installing ubuntu-desktop on top to get gnome will also install various other unwanted things such as open office, email etc etc. Is there a lite version of gnome available?

The desktop version approach would seem a bit more straight forward, but will removing a whole host of unwanted packages leave me with a sluggish system because of remnants left within the OS? Perhaps this fear is from my Windows background whereby installing/uninstalling lots of programs and games gradually leads to a very sluggish system!

I'd like to avoid too much command line admin which is why I'm keen to get gnome up and running (I of course realise that some will be necessary).

I've already discounted FreeNAS (hardware compatibility issues and poor samba performance) and Openfiler (LDAP and user authentication issues for a home network).

Thanks in advance for any advice received!

---

### Post by LanDan on 2007-10-17
advice is usually what worked for someone else, no guarentees it will work for you tough ;)

in general what makes linux and unix in general such a great performer as a server is that you don't need a desktop, in other words, what isn't there can not break....

i would strongly advise you to do the minimal server install and then simply install samba (assuming you want to use a windows network)

simply editing 1 single file from the commandline will give you a reliable NAS solution for many years to come without any worries once it is finally done.


[http://doc.ubuntu.com/ubuntu/serverguide/C/windows-networking.html](http://doc.ubuntu.com/ubuntu/serverguide/C/windows-networking.html)

---

### Post by njparton on 2007-10-17
OK, good point and advice. However it will be headless so can I install a VNC server or something similar without gnome? I'll be administering over http or https from Windows.

I'll also want to play around with some power saving, disk spinning settings etc and all in all I just thought that having a window manager installed would help.

I could install gnome and just stop gdm as I logout assuming that vnc sever will continue to run allowing me to startx on next login?

---

### Post by qrazi on 2007-10-19
If you want to use VNC or similar remote protocol, you need a Desktop installed, i.e. Gnome, KDE etc.... But the good news is that there are a lot more, less demanding options, such as XFCE (Xubuntu). Other names dont come to my mind at the moment (Openbox? Blacksomething?)

For a basic server install, perhaps access trough SSH is the better option. In windows you use PuTTy to gain access trough ssh to your server. You then have complete commandline access to your server from your Windows machine.

---

### Post by njparton on 2007-10-19
Thanks for that. I was looking at Xubuntu last night...

Given my limited command line experience in Linux I've decided not to go down the server/ssh route and to go for a lightweight desktop.  There's a post somewhere in this forum for how to achieve this with gnome.

I'll probably then stopx when I'm not logged in remotely and fire gdm back up when I need to get in. I guess I'd need to do the latter via ssh then as vnc server daemon will stop running once gnome closes down?

---

### Post by LanDan on 2007-10-19
don't think that a desktop is what you want

may i suggest you take a look at webmin or ebox?
you will find a lot of info on google and i think its what you are looking for

---

### Post by pasta514 on 2007-11-09
Well I don't know if this is allowed or not, but here goes...

I am working with Unbuntu because I am trying to setup a mythtv system.  Prior to that (here's the risky part)  I have a fantastic Clarkconnect :redface:system which does exactly what you have decribed.  Well, actually more than you describe... Firewall, Router, Content Filter (yea!!) and Samba Server with raid5... And fully managed by web browser interface, None of this VNC or XDMCP or other things that make me want to tear my hair out.  ](*,)

Also have installed Webmin which is a bit more advanced than I really am capable of using, but I like to poke around in it and pretend I understand it all.:cool:

I too have attempted an install on a CF card, but was not able to boot from it after the install.  Have you had any luck with that yet?

---

### Post by njparton on 2007-11-09
I ditched the CF card as performance, even with Xubnutu was unacceptably poor.

I'd only use the CF card if I switched to FreeNAS or Openfiler.

I've actually also switched distro to openSUSE 10.3 as Ubuntu 7.10 was way too buggy and unstable for me.

So far, openSUSE has been 100% stable... :)

However, I have to acknowledge that this may be because I learnt a lot of lessons in how to tweak certain things in ubuntu - I just find openSUSE easier to tweak as for most components this can be done through YAST.

I'm still faced with similar sleep and s2ram issues though.

---

### Post by pasta514 on 2007-11-09
Since I am trying to do an all-in-one box it seems to me it may not ever sleep with a family of 5 and the various functionality I'm loading on it.  As such I have not yet tried to tackle sleep management.  

Instead I have built my system around the 45W brisbane core BE-2300, Abit AN-52N (no onboard graphics) and an Antec Earthwatts 380W PSU. 3 fans, 1 HDD, 1 NIC and 1 TV tuner, 4GB Crucial RAM (2x2GB built with 1Gb chips). no graphics card.

Idles at 50W.  65W under memtest86.  Will replaces my current machine which uses 175W @ idle.  Besides being faster and more capable.

Now if I could only get the bloody thing working!!

---

### Post by njparton on 2007-11-10
What sort of problems are you having?

Check out openSUSE 10.3 too. It's a lot more involved but much more stable I've found.

---

