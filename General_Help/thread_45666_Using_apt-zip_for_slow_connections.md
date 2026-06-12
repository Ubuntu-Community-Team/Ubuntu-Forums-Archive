---
title: "Using apt-zip for slow connections"
date: 2005-07-01
forum: General Help
---

### Post by j_goldie on 2005-07-01
There's a link on [http://sistemac.carnet.hr/index.php?&id=89&backPID=107&begin_at=15&swords=apt&tt_news=311&cHash=7bbe489d70](http://sistemac.carnet.hr/index.php?&id=89&backPID=107&begin_at=15&swords=apt&tt_news=311&cHash=7bbe489d70)
for debian, but sadly it's in croatian, so there's a rough translation...

apt-zip enables to transfer with some portable media (ZIP drive, USB flash disk,

etc.) packages from high speed link computer to eg. home computer with slow link.

First, in /etc/fstab add the line(assuming that we have USB flash disk on /dev/sda)

**/dev/sda1 /mnt/usbkey vfat user,noauto 0 0**

Later in /etc/apt/apt-zip.conf configure the following lines

[B]# MEDIUM should be defined in /etc/fstab with option `noauto'.

MEDIUM=/mnt/usbkey[/B]

[B]# DEFAULT_APTGETACTION is the action taken by apt-get when neither

# the --aptgetaction nor the --packages options are given.

# Possible actions include: dselect-upgrade(default), upgrade and dist-upgrade

DEFAULT_APTGETACTION=dist-upgrade[/B]

Of course, one can choose method other than dist-upgrade. For instance, i wanted to install gnucash. Then I had put on command line apt-zip-list --aptgetaction=upgrade --packages=gnucash. 

Now refresh your repository

**# apt-get update **

Now put on USB flash disk list of needed packages:

**# apt-zip-list**

Of course, one can choose method other than dist-upgrade. For instance, i wanted to install gnucash. Then I had put on command line **apt-zip-list --aptgetaction=upgrade --packages=gnucash**.

One gets on USB flash disk to files:
- apt-zip.options which is conf file
- fetch-script-wget-<machine name> which is used for downloading

Now go with USB stick on some UNIX machine with high speed link, mount it and type
**# sh fetch-script-wget-ico-notebook **

Once the script had downloaded all needed packages, take the USB stick home, put it in USB port and write
**# apt-zip-inst**
For gnucash i used **# apt-zip-inst --aptgetaction=upgrade --packages=gnucash** 
To finish gnucash installation(tu put shortcut it in the gnome menu) i used
Unofficial Ubuntu 5.04 Starter Guide. 
[http://ubuntuguide.org/#gnucash](http://ubuntuguide.org/#gnucash) 
That's it!
Anyway, consult apt-zip documentation (like man page in order to )
In hope that someone will find it useful...

---

### Post by intangible on 2005-07-01
You should post this as a "howto" in **Hoary 5.04 Customization Tips & Tricks** [http://www.ubuntuforums.org/forumdisplay.php?f=58](http://www.ubuntuforums.org/forumdisplay.php?f=58)

---

