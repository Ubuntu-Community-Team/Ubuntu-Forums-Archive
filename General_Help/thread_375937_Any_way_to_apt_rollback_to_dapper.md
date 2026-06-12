---
title: "Any way to apt rollback to dapper?"
date: 2007-03-04
forum: General Help
---

### Post by vinitlee on 2007-03-04
I recently tried to upgrade to edgy eft by
> Using apt-get

Edit your /etc/apt/sources.list as root. Change every occurrence of dapper to edgy.

Use any prefered editor. If you have a CD-ROM line in your file, then remove it.

sudo vi /etc/apt/sources.list

or

use the following Simple command

sudo sed -e ’s/\sdapper/ edgy/g’ -i /etc/apt/sources.list

Now you need to update the source list using the following command

sudo apt-get update

Upgrade using the following command

sudo apt-get dist-upgrade

It returned quite a few errors, and I restarted, and it dumped me into a tty and gave me an error saying X had failed. I also got a few other errors which are not listed here.

Basically, I am wondering if there is any way that I can use apt to get the dapper packages  back, the ones which I replaced with edgy packages.

If anyone knows another way I can rollback or restore the system, please post.

All help aprreciated.

---

### Post by bapoumba on 2007-03-04
Hello,
as far as going back to dapper, you will have to reinstall it. Do you have a separate /home partition ?
For you current edgy install, have you tried **sudo dpkg-reconfigure xserver-xorg** ? What type of video card and driver are you using ?

---

### Post by vinitlee on 2007-03-05
Okay. I do not have a seperate partition, but I can back it up onto another computer using a live CD.
Yes, I've tried. It gave me an error.
I'm probably just going to reinstall.

On that point, what should I do, if I want to reinstall and then replace the home directory with my old one?
Should I install Dapper (the system was dapper until I tried to upgrade) or would edgy work with my home directory (and /etc directory)?

Thank you!

---

### Post by bapoumba on 2007-03-06
Either you back up your personal files on a different device, and reinstall dapper. Your current /home directory, which currently is within your root (/) partition will be recreated from scratch, nothing left. Then you can put your files back there. All your user config files will also be recreated, so you'll have to go to all the set up and adjustments again.

Or you can move your current edgy /home folder on a separate partition following this tutorial:
[http://psychocats.net/ubuntu/separatehome]("http://psychocats.net/ubuntu/separatehome")
and then reinstall dapper on the root partition. When installing dapper, tell where the /home partition is, and do not format it. Backup your files too, just in case.

There is a mid-term to these two options: backup your personal files, reinstall dapper and choose to make a separate /home at this point. You'll loose your config (well, you'll get the standard ones, think about a backup of contacts, email folders etc.. because all will be erased), but then you'll have a separate /home, which is way more convenient imho.

---

