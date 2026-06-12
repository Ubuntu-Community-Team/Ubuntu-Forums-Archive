---
title: "Messed up 13.04 upgrade"
date: 2013-04-26
forum: General Help
---

### Post by GameX2 on 2013-04-26
Hi,

Out of curiosity, I've attempted an upgrade from Ubuntu 12.04 LTS, after  a backup.  I've never done an upgrade before, always clean installs,  but I wanted to try and see how it goes, for experience.  I've read this  webpage:
[http://www.tuxtrix.com/2013/03/how-t...4-to-1304.html[COLOR=#FFFFFF ! important][FONT=arial]**122**[/FONT][/COLOR]]("http://www.tuxtrix.com/2013/03/how-to-upgrade-from-ubuntu-1204-to-1304.html")

After a backup, I started the upgrade ( sudo apt-get dist-upgrade ).   Then I got a few errors at the end, I guess.  After a reboot, LightDM  was not showing the Ubuntu 13.04 logo, but still 12.04.  Logged in, then  I realised that probably broke Compiz / Unity / Nautilus.  According to  the system monitor, I was on Ubuntu 13.04, but had no way to verify.

Well, that wasn't a very good experience for my first upgrade (Wasn't  expecting anything great.  Just curious)!  I do realise I've tried to  skip 12.10, actually, for the upgrade.  Maybe that wasn't a good idea.

Anyways, I restored my Ubuntu_OS partition, everything look fixed.  But I  stupidly replaces my Ubuntu_Home backup (I've realised I've done a  second backup of Ubuntu_OS and erasing my Ubuntu_Home backup...), using  Clonezilla...
I have a working backup of my Home directory 5 days earlier.  I wouldn't  loose a lot of stuff (That I could backup right now anyways), but I  would like to be sure:

Did the messed-up upgrade modified anything in the Home directory?
Everything is running fine, now..

I did tested Raring from a LiveCD, and it look good - maybe I'll just install it next to Precise.

Thanks

---

### Post by sudodus on 2013-04-26
[https://sites.google.com/site/easylinuxtipsproject/upgrade](https://sites.google.com/site/easylinuxtipsproject/upgrade)

has a lot of good advice.

If you want to take risks (and with a good backup it's OK), you can look at the following link

[http://lawrit.lawr.ucdavis.edu/it-help-center/how-to/upgrading-ubuntu-via-command-line](http://lawrit.lawr.ucdavis.edu/it-help-center/how-to/upgrading-ubuntu-via-command-line)

so ```
sudo do-release-upgrade
``` is doing the move from 12.04 to 12.10, and then you need another step from 12.10 to 13.04. I think it is a better idea to run them side by side (Precise and Raring).

---

### Post by GameX2 on 2013-04-26
> **sudodus said:**
> [https://sites.google.com/site/easylinuxtipsproject/upgrade](https://sites.google.com/site/easylinuxtipsproject/upgrade)

has a lot of good advice.

If you want to take risks (and with a good backup it's OK), you can look at the following link

[http://lawrit.lawr.ucdavis.edu/it-help-center/how-to/upgrading-ubuntu-via-command-line](http://lawrit.lawr.ucdavis.edu/it-help-center/how-to/upgrading-ubuntu-via-command-line)

so ```
sudo do-release-upgrade
``` is doing the move from 12.04 to 12.10, and then you need another step from 12.10 to 13.04. I think it is a better idea to run them side by side (Precise and Raring).

Thanks.  I'll probably try that, one version at a time.  I'm especially curious about the speed of Raring everyone mention.  It's actually true that there only are a few features added, but if it's even faster..

The social lens looked interesting, as well.
On my problematic upgrade, is my Home directory untouched?

---

### Post by sudodus on 2013-04-26
I'm not sure, but I don't think your home directory was damaged. But the command(s) you described
```
sudo apt-get update
sudo apt-get upgrade
[COLOR=#ff0000]sudo apt-get dist-upgrade[/COLOR]
```
are all standard commands to keep an installed Ubuntu version up to date. They should be safe; it is considered more risky to forget to do these updates, because of the security updates to prevent attacks from the internet. Once in a great while something is broken, but it will be fixed within a few days in the normal case. However, if you have some packages with PPAs, that are not supervised by the Ubuntu or Canonical people, there might be conflicts.

*Edit*: Read about these commands in the manual pages
```
man apt-get
```

---

### Post by GameX2 on 2013-04-26
> **sudodus said:**
> I'm not sure, but I don't think your home directory was damaged. But the command(s) you described
```
sudo apt-get update
sudo apt-get upgrade
[COLOR=#ff0000]sudo apt-get dist-upgrade[/COLOR]
```
are all standard commands to keep an installed Ubuntu version up to date. They should be safe; it is considered more risky to forget to do these updates, because of the security updates to prevent attacks from the internet. Once in a great while something is broken, but it will be fixed within a few days in the normal case. However, if you have some packages with PPAs, that are not supervised by the Ubuntu or Canonical people, there might be conflicts.

*Edit*: Read about these commands in the manual pages
```
man apt-get
```

Yes, I have multiple (Around 12) PPAs enabled, and I'll see if this cause any problem (This is probable).  I am aware the more PPAs I have enabled, the more risks I take to have a non-working software, or more.

---

