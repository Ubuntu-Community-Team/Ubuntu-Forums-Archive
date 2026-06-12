---
title: "Problem Whit Breezy Badger Boot"
date: 2007-11-15
forum: General Help
---

### Post by sXniZzeN on 2007-11-15
Hi!


I have innstalled Breezy Badger on my laptop, It is an Compac Armada 1750. I have a problem with the boot, I have installed it just fine, and when it was setting up the packages after the cd have done his work,  the laptop suddenly shutdown, when I started it up again, it don't complete the boot, I can only write in like a full screen terminal, where I must login, and when I login there its just like the terminal.  It does not complete to the login screen like it is supposed  to..
:confused:

Any one who can help me??

I'm new to Ubuntu... So I need all the help I can get!

---

### Post by geirha on 2007-11-15
Breezy Badger isn't supported anymore, it's way old. You should install 6.06 Dapper Drake or 7.10 Gutsy Gibbon.

---

### Post by PaganHippie on 2007-11-15
Sounds like Xorg and/or your desktop manager either can't start (in which case you should see an error message to that effect) or did not get installed at all, which sometimes happens on low-memory installs.  

If it's the former, you will probably need to adjust some settings in xorg.conf .  Hard for me to say what those adjustments are, though, without seeing the error message(s).

If it's the latter, which it probably is if the computer goes straight to the Login prompt without any error messages, you can usually finish the installation by entering either _**one**_ of the following two lines, depending on whether you want Gnome or KDE:

```
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
```I'm curious, though, why you're using Breezy, which is no longer supported?  Not that it's a bad version, not at all, but there may be better options out there.  If I were you, I'd try either Dapper (6.06) or Feisty (7.04), but of which *are* currently supported and quite stable.  Gutsy (7.10), from what I'm seeing in these forums, is only for the brave and the patient, at least until they iron out some annoying bugs.

---

### Post by sXniZzeN on 2007-11-15
I'm using Breezy because i'ts an old laptop:p It only have 128mb ram.. and about 400MHz CPU.. So I don't know of any other versjon it can run.. any suggestions?

---

### Post by hardyn on 2007-11-15
try a different distro.  you would be much better off with something newer, you might have a fighting chance of having the hardware recognised.

---

### Post by sXniZzeN on 2007-11-15
any distrobutors that you can recomend then?? I was thinking about Red Hat...

---

### Post by hardyn on 2007-11-15
DSL, puppy or other designed for lighweight systems.

---

### Post by sXniZzeN on 2007-11-15
OK=) Thx for the help

---

### Post by PaganHippie on 2007-11-15
FWIW, I'm running Dapper with Xfce on an even older laptop, slower and with less RAM.  I'm not saying it's fast, but it can be done if you still want the 'Ubuntu Experience.'  Otherwise, any of the small-footprint distros mentioned by hardyn should be fine.

---

### Post by sXniZzeN on 2007-11-15
I got a better computer I can run any Ubuntu I want on.. It's just that i want an Unix system on the Laptop.. so about any linux is okay.. I jus looked at Ubuntu first beacause it is the only system I've tried before...

---

### Post by jfinkels on 2007-11-15
Try Fluxbuntu, and try the most recent version ( [http://www.fluxbuntu.org/js.html](http://www.fluxbuntu.org/js.html) ). It is lighter than Ubuntu. An older version DOES NOT mean "works better with older hardware". If anything, the opposite is true: a newer version will perform better.

---

### Post by sXniZzeN on 2007-11-16
I know.. But at the older versions U dont have to run the live cd... it is the live cd that needs better hardware..

---

### Post by PaganHippie on 2007-11-16
There are 'alternate' install CDs of all the newer versions of *ubuntu that just boot directly into a text-based installer.  They work on a lot of systems that can't handle the live CDs. Fluxbuntu appears to only offer live CDs, though.

---

### Post by kd7swh on 2007-11-16
Puppy is good but debian would work too.... 

debian is as light as you want it to be :)

---

### Post by zvacet on 2007-11-16
[http://ftp.cw.net/xubuntu/releases/feisty/release/]("http://ftp.cw.net/xubuntu/releases/feisty/release/")

[http://ftp.cw.net/xubuntu/releases/gutsy/release/]("http://ftp.cw.net/xubuntu/releases/gutsy/release/")


Select alternate CD to download.

---

### Post by Nevon on 2007-11-16
I would highly recommend xubuntu. I'm on Fluxbuntu right now, and unless you're an experienced Linux user, I wouldn't recommend it. Something as easy as changing the wallpaper requires some googling. In fact, my wallpaper still changes back into the default one after about 1 second. :P Xubuntu is also designed for low-end systems, but seems to be a bit easier to use than Fluxbuntu.

---

### Post by sXniZzeN on 2007-11-16
I must say THX for all the help!:)

---

