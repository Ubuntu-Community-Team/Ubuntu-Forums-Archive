---
title: "Error when updating/installing on Ubuntu."
date: 2016-03-18
forum: General Help
---

### Post by Posuk13 on 2016-03-18
When I am updating I am getting folloving error:
```
Sorry, a problem occurred while installing software. Package: google-chrome-stable ubuntu
```

I have tried several tips how to fix this issue (including this: [http://ubuntuforums.org/showthread.php?t=1642173](http://ubuntuforums.org/showthread.php?t=1642173)) but with no help. 
I have also disable.

And here are some diagnostic date.

Command:
```
sudo apt-get install -f
```

Output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up google-chrome-stable (49.0.2623.87-1) ...
xdg-icon-resource: size argument must be numeric
Try 'xdg-icon-resource --help' for more information.
dpkg: error processing package google-chrome-stable (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 google-chrome-stable
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Command:
```
cat /etc/apt/sources.list
```

Output:
```
# deb cdrom:[Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)]/ wily main restricted
deb-src http://tux.rainside.sk/ubuntu/ wily main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://tux.rainside.sk/ubuntu/ wily main restricted
deb-src http://tux.rainside.sk/ubuntu/ wily multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://tux.rainside.sk/ubuntu/ wily-updates main restricted
deb-src http://tux.rainside.sk/ubuntu/ wily-updates multiverse main restricted universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://tux.rainside.sk/ubuntu/ wily universe
deb http://tux.rainside.sk/ubuntu/ wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://tux.rainside.sk/ubuntu/ wily multiverse
deb http://tux.rainside.sk/ubuntu/ wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://tux.rainside.sk/ubuntu/ wily-security main restricted
deb-src http://tux.rainside.sk/ubuntu/ wily-security multiverse main restricted universe #Added by software-properties
deb http://tux.rainside.sk/ubuntu/ wily-security universe
deb http://tux.rainside.sk/ubuntu/ wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu wily partner
# deb-src http://archive.canonical.com/ubuntu wily partner
deb http://download.virtualbox.org/virtualbox/debian wily contrib
# deb-src http://download.virtualbox.org/virtualbox/debian wily contrib

```

Command:
```
sudo apt-get remove --purge google-chrome-stable
```

Output:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  google-chrome-stable*
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
1 not fully installed or removed.
After this operation, 186 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 213641 files and directories currently installed.)
Removing google-chrome-stable (49.0.2623.87-1) ...
xdg-icon-resource: size argument must be numeric
Try 'xdg-icon-resource --help' for more information.
dpkg: error processing package google-chrome-stable (--purge):
 subprocess installed pre-removal script returned error exit status 1
xdg-icon-resource: size argument must be numeric
Try 'xdg-icon-resource --help' for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 google-chrome-stable
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help will be appreciated.

---

### Post by QDR06VV9 on 2016-03-18
See if this gets you sorted out.

```
sudo find /var/lib/dpkg -exec grep -l "google-chrome-stable" {} \;
```

and
```
gksudo gedit /var/lib/dpkg/info/google-chrome-stable.prerm
```

Then add a first line
```
exit 0
```

And now
```
sudo dpkg -P google-chrome-stable
```
Hope this is helpful...

---

### Post by Posuk13 on 2016-03-18
Thanks a million - it works. I have tried quite a few thinks but non worked until now. If you will have a minute it will be great if you could explain a bit what actually are this commands doing so I can understand better how it works. But if not, I understand you might be busy. Thanks a lot for your help again.

---

### Post by QDR06VV9 on 2016-03-18
Your very welcome glad it helped.
My dialog when explaining terminal commands...well it is like i am speaking a new gibberish.[IMG]http://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG]
It is more or less using a small hammer for unsticking half installed packages.
At least that is my story...:D
If you would be as kind to mark the thread solved as to help others.
Kind Regards

---

