---
title: "Can OS be easily changed from Ubuntu to Ubuntu Studio?"
date: 2007-07-27
forum: General Help
---

### Post by techuser on 2007-07-27
Just wondering if the move from standard Ubuntu Fiesty to something like Ubuntu Studio can be done without loosing any file info already stored on my system? 
This also brings up a question of how the next upgrade will get handled. Seeing I am new to Ubuntu, is the migration from an earlier version to the current/latest release as simple as using the update option?
:popcorn:

---

### Post by nichipet on 2007-07-27
On the Studio question, it's easy and safe to upgrade. I'll try to find a page with instructions, but off-hand I think [http://www.ubuntustudio.org](http://www.ubuntustudio.org) may have them.

---

### Post by nichipet on 2007-07-27
Here's a page from Ubuntu.com: [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty)

---

### Post by Scheater5 on 2007-07-27
Yes.  And yes, with provisions.

Installing Ubuntu Studio on top of Fesity is as easy as adding a repository to your sources.list and typing in a few commands in a terminal.  In fact, that's precisely what Ubuntu Studio recommends you do if you don't have a DVD burner.  Add the line 
> deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
to etc/apt/sources.list and then, in a terminal, run

```
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O-  | sudo apt-key add -
sudo aptitude update
sudo aptitude install ubuntustudio-desktop
```

and then follow that up with 
```
sudo aptitude install ubuntustudio-audio ubuntustudio-audio-plugins
```
or
```
sudo aptitude install ubuntustudio-graphics
```
or 
```
sudo aptitude install ubuntustudio-video
```

And as for the upgrade process, provided you don't install too many third party application, the upgrade process is as simple as executing a command.
```
sudo aptitude dist-upgrade
```
Most of the time it goes off without a hitch.  Occasionally it doesn't.  It's been getting better and better with each successive release.  The basic rule of thumb is, before you do something that big a deal, back up, back up, back up.

---

### Post by techuser on 2007-07-27
Wow thanks for your responses:):).
The info was very helpful
Thanks
:popcorn:

---

### Post by kystorms on 2007-09-13
So does Studio park itself over Feisty or make itself like xfce, a session? Will it wipe out all I have as far as compiz fusion ( not that I mind that, at all) and such things as chat programs? What would I lose by doing this as far as programs I have now on Feisty?

thanks for any answers

:confused:

---

