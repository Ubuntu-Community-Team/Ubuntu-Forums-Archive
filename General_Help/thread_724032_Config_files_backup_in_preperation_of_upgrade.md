---
title: "Config files backup in preperation of upgrade?"
date: 2008-03-14
forum: General Help
---

### Post by njparton on 2008-03-14
In anticipation of installing Hardy on my NAS once it's been out a few weeks and stabilised, I've started back up config files for the following:

[LIST]
[*]samba
[*]fstab
[*]crontab
[*]rsync
[/LIST]

Having never done a distro upgrade before I was wondering if this was really necessary and/or what configs would be retained after an upgrade?

Will I also need to re-install services such as 3DM2 (3ware raid monitoring) and programs such as torrentflux?

---

### Post by danwood76 on 2008-03-14
The best thing to do is a complete backup of all your apps, configs, os using the tar method ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)), then try the upgrade.
Obviously when you do the tar method you need to specify it to exclude all your data on your nas as this will obviously make the archive size a lot larger.
Ive never done an upgrade between versions before, always just started afresh.

It shopuld be seamless but if you have installed unstable packages manually and not through synaptic then they may get broken and cause you problems.
If you do a backup first then you have nothing to loose really (except a lot of time obviously)

---

### Post by njparton on 2008-03-14
Thanks for that.

I'm still toying with the idea of removing 7.10 desktop and going for 8.04 server as I'm much more comfortable with the command line now in which case I'll obviously need to start from scratch so that backup method may be helpful.

---

