---
title: "How does Thunar mount a device?"
date: 2014-02-08
forum: General Help
---

### Post by vasa1 on 2014-02-08
When I open Thunar after booting my laptop, I see some "Devices" listed in the side-pane. If I want to access "TOSHIBA EXT" which is a 500GB USB disk, I single-click on it.

My question is this: how can I do, in a terminal (and without sudo and without using Thunar in the command) what Thunar does when I single-click on "TOSHIBA EXT" as a normal user?

I don't want to edit */etc/fstab* and have not edited it previously.

---

### Post by Bucky Ball on 2014-02-08
Not sure I follow. You want to open the folders on the device from a terminal? You want a terminal command that will open the folders in a GUI?
 
Where, if not in the terminal, are you wanting the folders to open?

---

### Post by pqwoerituytrueiwoq on 2014-02-08
> **Bucky Ball said:**
> Not sure I follow. You want to open the folders on the device from a terminal? You want a terminal command that will open the folders in a GUI?
 
Where, if not in the terminal, are you wanting the folders to open?
OP is asking how thunar does it without root access, so that OP can do it without root access from a terminal
if you were using sudo
```
sudo mkdir /media/$USER/TOSHIBA\ EXT
sudo mount /dev/sdb1 /media/$USER/TOSHIBA\ EXT
```
but OP wants to do it without sudo

---

### Post by Bucky Ball on 2014-02-08
> **pqwoerituytrueiwoq said:**
> ... but OP wants to do it without sudo

That part is crystal clear. ;)

So, solution? :-k

---

### Post by vasa1 on 2014-02-08
> **pqwoerituytrueiwoq said:**
> OP is asking how thunar does it without root access, so that OP can do it without root access from a terminal
if you were using sudo
```
sudo mkdir /media/$USER/TOSHIBA\ EXT
sudo mount /dev/sdb1 /media/$USER/TOSHIBA\ EXT
```
but OP wants to do it without sudo

The only reason I asked for "without sudo" is that Thunar mounts the device without sudo. I have no objection to using sudo, *per se*, but the question remains: how does Thunar manage to do it without (gk)sudo?

---

### Post by Bucky Ball on 2014-02-08
> **vasa1 said:**
> ... the question remains: how does Thunar manage to do it without (gk)sudo?

Indeed it does. Now I'm curious. Never thought of it before. Perhaps it has something to do with the fact that you have permissions, as the user that logged in to start with, to allow it to do so. Probably about the user and groups ...

My guess, anyway ... ;)

---

### Post by sisco311 on 2014-02-08
Thunar uses udisks: [uhelp]community/AutomaticallyMountPartitions[/uhelp]

---

### Post by vasa1 on 2014-02-08
> **sisco311 said:**
> Thunar uses udisks: [uhelp]community/AutomaticallyMountPartitions[/uhelp]
That seems to be it:
> When you mount a disc normally with the file browser (nautilus etc) it mounts disks by interacting with udisks behind the scenes. from the link. Thanks!
```
[01:41 PM] ~ $ /usr/bin/udisks --mount /dev/sdb1
Mounted /org/freedesktop/UDisks/devices/sdb1 at /media/TOSHIBA EXT
[01:41 PM] ~ $
```
And unmounting uses *--unmount* instead of *--mount*.

---

### Post by Dennis N on 2014-02-09
> **vasa1 said:**
> That seems to be it:
from the link. Thanks!
```
[01:41 PM] ~ $ /usr/bin/udisks --mount /dev/sdb1
Mounted /org/freedesktop/UDisks/devices/sdb1 at /media/TOSHIBA EXT
[01:41 PM] ~ $
```
And unmounting uses *--unmount* instead of *--mount*.

I notice udisks is mounting to **/media/** instead of **/media/<usr>/**. Nevertheless, I put this into a one-line startup script to mount my Lubuntu partition from my Xubuntu partition at login. Seems to be working fine after some brief testing.

Manual mounting output:

```
dn@Sydney:~$ udisks --mount /dev/disk/by-label/Lubuntu-1210 
Mounted /org/freedesktop/UDisks/devices/sda1 at /media/

dn@Sydney:/media$ ls -l
total 8
drwxr-x---+  3 root root 4096 Feb  9 07:13 dn
drwxr-xr-x  23 root root 4096 Jan  3 22:07 Lubuntu-1210

```

Any mounting from the devices section in Thunar's side pane is done to /media/<usr>/

---

### Post by sudodus on 2014-02-09
> **Dennis N said:**
> I notice udisks is mounting to **/media/** instead of **/media/<usr>/**/

This is different between versions. I have noticed that 12.04 mounts in /media, while 13.10 mounts in /media/<usr>

---

### Post by Dennis N on 2014-02-09
> **sudodus said:**
> This is different between versions. I have noticed that 12.04 mounts in /media, while 13.10 mounts in /media/<usr>

I thought that might be. I don't have a Xubuntu 13.10 - I was using Xubuntu 12.10 (in which udisks had to be installed), but the curious thing is I also did the same autostart setup on Linux Mint 16 XFCE (which I believe that is based on 13.10) and find udisks still mounts at /media/ but Thunar in /media/<usr>/.

---

### Post by Dennis N on 2014-02-09
This would explain the different mount points:

This is from Xubuntu 12.10: 

```
dn@Sydney:~$ cd /usr/bin
dn@Sydney:/usr/bin$ ls udisk*
udisks  udisksctl  udisks-tcp-bridge

```
udisksctl is for udisks2, which must be what Thunar is using, since udisks is not installed by default in Xubuntu 12.10 (I installed udisks on it just yesterday). udisks2 must use the newer mount point.

That also explains the Linux Mint 16 XFCE result I mentioned in the previous post, as the Mint people have both installed by default.

ADDED:
Xubuntu 13.10 manifest shows udisks2	2.1.0-4 but no udisks.

---

### Post by vasa1 on 2014-02-09
Mine is a Lubuntu **13.10** install. When I ran *apt-cache search --names-only udisk* I got a list and then I ran *apt-cache policy* on them:
```

gir1.2-udisks-2.0 - GObject based library to access udisks2 - introspection data 	n
libudisks2-0 - GObject based library to access udisks2					2.1.0-4
libudisks2-dev - GObject based library to access udisks2 - development files		n
udisks - storage media interface								1.0.4-8ubuntu1
udisks-doc - storage media interface - documentation						n
udisks2 - D-BUS service to access and manipulate storage devices				2.1.0-4
udisks2-doc - udisks2 documentation								n

```where "n" = "not installed" and a number indicates the version number if installed.

*Tabs are difficult to understand* :(

---

### Post by Dennis N on 2014-02-09
Yes, Lubuntu has them both by default. udisks still mounts to /media as usual. No change.

This is also Lubuntu 13.10.

Using udisks:
```
dn@Roxanne:/dev/disk/by-label$ **udisks --mount /dev/disk/by-label/Mint_16**
Mounted /org/freedesktop/UDisks/devices/sdb9 at **/media/Mint_16**

```

Using udisks2:
```
dn@Roxanne:/dev/disk/by-label$ **udisksctl mount -b /dev/disk/by-label/Mint_16**
Mounted /dev/sdb9 at **/media/dn/Mint_16.**

```

It mounts to /media/<usr>/

Pretty clear the file manager is using udisks2.

---

### Post by vasa1 on 2014-02-09
Thanks, so "udisksctl" it will need to be to get the Thunar experience :)

---

### Post by vasa1 on 2014-02-10
> **Dennis N said:**
> ...
Using udisks2:
```
dn@Roxanne:/dev/disk/by-label$ **udisksctl mount -b /dev/disk/by-label/Mint_16**
Mounted /dev/sdb9 at **/media/dn/Mint_16.**

```
...
@Dennis N, could you please explain the use of **-b**? I didn't find an explanation in *man udisksctl* or in *man mount*.

---

### Post by vasa1 on 2014-02-10
```
Usage:
  udisksctl mount [OPTION...]

Mount a filesystem.

Application Options:
  -p, --object-path         Object to mount
  **-b, --block-device        Block device to mount**
  -t, --filesystem-type     Filesystem type to use
  -o, --options             Mount options
  --no-user-interaction     Do not authenticate the user if needed


```

---

### Post by Dennis N on 2014-02-10
6:30 AM: We have a little time difference - if your location is accurate, here in Arizona is about 12 hrs behind you. Just starting the day here.

As to udisksctl, here's the story: When I tried your commmand in post #8 in Xubuntu 12.10 I found it did nothing. I looked at /usr/bin/ and did not see udisks, but only udisksctl, so I googled that and gave me many links. Since Xubuntu 12.10 did not have udisks, I installed it and then everything worked. Turns out since 12.04, Xubuntu has not included udisks - only the replacement udisks2.

I first got the command usage from here:

[http://askubuntu.com/questions/342188/how-to-auto-mount-from-command-line](http://askubuntu.com/questions/342188/how-to-auto-mount-from-command-line)

Since all my filesystems have labels, I decided to mount by label instead, as you can see in my commands.  

I just saw this last night, which confirms the different mount points:

[http://unix.stackexchange.com/questions/62676/mounting-from-dolphin-vs-commandline](http://unix.stackexchange.com/questions/62676/mounting-from-dolphin-vs-commandline)

Quoting:


> ...There are two versions of udisks, "udisks" and "udisks2". You have probably installed at least one of them. Both ship with commandline utilities. Both should work when Dolphin works.

udisks mounts the filesystems into /media/<label>.

$ udisks --mount /dev/sdc1
Mounted /org/freedesktop/UDisks/devices/sdc1 at /media/<label>
$ udisks --unmount /dev/sdc1

The utility for udisks2 is called udisksctl. It uses /run/media/$USERNAME/<label>

$ udisksctl mount -b /dev/sdc1
Mounted /dev/sdc1 at /run/media/t-8ch/<label>.
$ udisksctl unmount -b /dev/sdc1
Unmounted /dev/sdc1.

There is some controversy over udisk2. Read this:

[http://igurublog.wordpress.com/2012/03/11/udisks2-another-loss-for-linux/](http://igurublog.wordpress.com/2012/03/11/udisks2-another-loss-for-linux/)

I don't know which is the "best" way (if there is one) to automount filesystems on other partitions at login, but this one works for me. I also did automount with a line in fstab, which surely works in any Linux distro, but decided to use this instead. This is easy to set up and easy to disable from startup applications.

---

### Post by vasa1 on 2014-02-10
> **Dennis N said:**
> 6:30 AM: We have a little time difference - **if your location is accurate**, here in Arizona is about 12 hrs behind you. Just starting the day here.
Yes, it is :)

...
> **Dennis N said:**
> 
There is some controversy over udisk2. Read this:

[http://igurublog.wordpress.com/2012/03/11/udisks2-another-loss-for-linux/](http://igurublog.wordpress.com/2012/03/11/udisks2-another-loss-for-linux/)

I don't know which is the "best" way (if there is one) to automount filesystems on other partitions at login, but this one works for me. I also did automount with a line in fstab, which surely works in any Linux distro, but decided to use this instead. This is easy to set up and easy to disable from startup applications.
I skimmed that blog and at least for me, the GNOME aspect doesn't seem to affect things (right now). I'm using the Openbox session of Lubuntu 13.10 with no desktop environment and both your command and plain udisks work just fine. I've put the udisksctl command in my Openbox autostart and will see how things go with a restart although I got the impression that plain udisks is a bit quicker (in terms of the prompt returning in the terminal).

---

