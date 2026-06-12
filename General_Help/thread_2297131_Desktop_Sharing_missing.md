---
title: "Desktop Sharing *missing*??"
date: 2015-10-01
forum: General Help
---

### Post by BarryD9545 on 2015-10-01
I just did a 15.04 clean install, and while Ubuntu Software Center says I have Desktop Sharing installed, I can't find it anywhere.

Yes, I went to Applications>System Tools>Preferences, and everywhere else the menu had to offer.

Logging out and switching out from Gnome didn't make it appear either.

Where's it hiding?

I know I probably passed it in the aisle all day, but *I* just don't see it.

Thanks.

---

### Post by howefield on 2015-10-01
Is this default 15.04 Ubuntu ?

If you really don't see it, try 

```
vino-preferences
```

from the terminal.

---

### Post by BarryD9545 on 2015-10-01
Yep.  Downloaded the ISO direct from Ubuntu to burn the disc from.

And get this little mind popper:

[ATTACH=CONFIG]264768[/ATTACH]

This seems...odd.

---

### Post by howefield on 2015-10-01
Try reinstalling it.

```
sudo apt-get update
```
```
sudo apt-get install --reinstall vino
```

---

### Post by BarryD9545 on 2015-10-01
No Luck

[ATTACH=CONFIG]264769[/ATTACH]

But this *is* weird, right?

---

### Post by howefield on 2015-10-01
What looks weird is the vino_3.13.90-1ubuntu1~utopic2_i386.deb package in your screenshot.

In an (*almost) fresh 15.04 I get the following..

```
hugh@vivid-laptop:~$ sudo apt-get install --reinstall vino
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-15 linux-headers-3.19.0-15-generic linux-image-3.19.0-15-generic linux-image-extra-3.19.0-15-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 21 not to upgrade.
Need to get 0 B/142 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 246850 files and directories currently installed.)
Preparing to unpack .../vino_3.8.1-0ubuntu5_amd64.deb ...
Unpacking vino (3.8.1-0ubuntu5) over (3.8.1-0ubuntu5) ...
Processing triggers for libglib2.0-0:amd64 (2.44.1-1ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Setting up vino (3.8.1-0ubuntu5) ...
hugh@vivid-laptop:~$ 
```

---

### Post by BarryD9545 on 2015-10-01
Here's more weird ... 
Only vino 3.13.90, what I have, is found on [launchpad]("https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3/+packages?field.name_filter=vino&field.status_filter=published&field.series_filter=").

Unless one of us is on a different timeline.

Repository I'm using is ppa:gnome3-team/gnome3

---

### Post by buzzingrobot on 2015-10-01
Vino 3.8.1 is in the Vivid repo: [http://packages.ubuntu.com/vivid/vino](http://packages.ubuntu.com/vivid/vino).

The version in the Gnome PPA is 3.13.90 and copied over from the Gnome Staging PPA, which carries its customary warning: "The packages here have been deemed not ready for general use, they have  known bugs and/or regressions, sometimes of a critical nature."

My approach would be to remove the PPA package, disable the PPA, and try another 'sudo apt-get install vino' which should pull the one in the repo. If Synaptic is installed, you can look to see which version is on offer. 

Desktop Sharing is a standard feature and should be there after a standard install, without bothering with a PPA. (Things like this -- getting the wrong version of a package -- can happen using a PPA: Someone enables a PPA to get Package A, but the PPA also contains other potentially incompatible packages that get pulled in as dependencies or because they're later releases).

---

### Post by BarryD9545 on 2015-10-02
Thank you buzzingrobot,

A purge vino, your advice, and a log out/log in brought things back to normal(ish).

I'll mark this one solved.

---

