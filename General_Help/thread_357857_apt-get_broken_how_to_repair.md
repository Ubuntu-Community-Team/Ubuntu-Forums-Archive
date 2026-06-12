---
title: "apt-get broken??? how to repair"
date: 2007-02-10
forum: General Help
---

### Post by krantix on 2007-02-10
I cannot update anymore... this is what i get...

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I've tryed to substitute status with status.old but nothing changes...

my /var/lib/dpkg/status file is as follows...

```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:christian
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,christian
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,christian
floppy:x:25:haldaemon,christian
tape:x:26:
sudo:x:27:
audio:x:29:christian
dip:x:30:christian
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:christian
sasl:x:45:
plugdev:x:46:haldaemon,christian
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
ssl-cert:x:104:cupsys
crontab:x:105:
ssh:x:106:
messagebus:x:107:
avahi:x:108:
lpadmin:x:109:christian
haldaemon:x:110:
scanner:x:111:cupsys,hplip,christian
slocate:x:112:
gdm:x:113:
christian:x:1000:
admin:x:114:christian
fuse:x:115:christian

```


please, help!!!

even if i try apt-get upgrade the result is again...

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by cmost on 2007-02-10
First, try (in a terminal):
apt-get update

If you're still getting the same error, try (in a terminal):
apt-get clean && apt-get update

Finally, if that didn't help, then use the nuclear option; do the following (in a terminal):
sudo rm /var/lib/apt/lists/* -vf

followed by (in a terminal):
apt-get update

Good luck!

---

### Post by krantix on 2007-02-10
tryed even the nuke... this is what i get...

Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/Release](http://ubuntu.beryl-project.org/dists/edgy/Release)  Unable to find expected entry  main-edgy/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


?!??! thanks for you help! :confused:

---

### Post by llamakc on 2007-02-10
The Release file is there for me. I just checked.

---

### Post by krantix on 2007-02-10
even if i remove beryl the error is just the same...

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by krantix on 2007-02-10
i also tryed

sudo dpkg --forget-old-unavail


dpkg: parse error, in file `/var/lib/dpkg/status' near line 56:
 missing package name


but the file status looks ok... line 56 does not even exist (it ends at 55). I've also copied status-old but without any luck...

---

### Post by llamakc on 2007-02-10
I believe it should end with a newline.

---

### Post by krantix on 2007-02-10
added a line... 

no change... still

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


is there a way to reinstall apt-get and dpkg from scratch?

i had a strange freeze and after that everything goes wrong...

---

### Post by cmost on 2007-02-10
Irritatingly stubborn problem, isn't it?

Try this:
It may be that your "/var/lib/dpkg/status" has been corrupted.  To correct this, try renaming a file called "status-old" (the backup) to status.

Reboot, and try again with:
apt-get update

---

### Post by krantix on 2007-02-10
yes! even more because i've tryed almost everything with dpkg/status...

also renaming the old file does not work....

could it be that the apt configuration got corrupted? is there a way to restore it? 

apt cache dump returns this...

```

christian@christian-laptop:~$ apt-config dump


APT "";
APT::Architecture "i386";
APT::Build-Essential "";
APT::Build-Essential:: "build-essential";
APT::Install-Recommends "0";
APT::Install-Suggests "0";
APT::NeverAutoRemove "";
APT::NeverAutoRemove:: "^linux-image.*";
APT::NeverAutoRemove:: "^linux-restricted-modules.*";
APT::Install-Recommends-Section "metapackages";
APT::Periodic "";
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Archives "";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
APT::Acquire "";
APT::Acquire::Translation "environment";
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::userstatus "status.user";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache::pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::dpkg "/usr/bin/dpkg";
aptitude "";
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$";
Unattended-Upgrade "";
Unattended-Upgrade::Allowed-Origins "";
Unattended-Upgrade::Allowed-Origins:: "Ubuntu edgy-security";
DPkg "";
DPkg::Pre-Install-Pkgs "";
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg::Post-Invoke "";
DPkg::Post-Invoke:: "if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi";

```

---

### Post by ghandi69_ on 2007-02-10
Hey,,

This isn't really exactly the same as the original poster, but it is a problem with apt-get!!

I installed virtual box and it said it depended on newer versions libqt3-mt (needs 3.3.3.7 I have 3.3.3.6) and libss10.9.8 (needs 0.9.9c, I have 0.9.8b2).. but when I apt get these packages, it says I have the newest versions.

Now, in terms of virtual box, I did a force depends version, and it installed and is currently simualting windows vista, and works great.  However, whenever I try to do anything with apt-get anymore.. it says ..

> 
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  virtualbox: Depends: libqt3-mt (>= 3:3.3.7) but 3:3.3.6-3ubuntu3 is installed
              Depends: libssl0.9.8 (>= 0.9.8c-1) but 0.9.8b-2


when I do the -f thing it removes the virtual box package!!  I can't install or do anything with apt-get as long as this issue remains.

---

### Post by krantix on 2007-02-12
i need to reinstall apt-get and dpkg... which is the best way to proceeed?

i always get this error on install/update


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I've tryed to put a fresh new sources.list,

tryed 

apt-get upgrade
apt-get clean 
sudo rm /var/lib/apt/lists/* -vf
sudo dpkg --forget-old-unavail
try renaming  "status-old" (the backup) to status

```
APT "";
APT::Architecture "i386";
APT::Build-Essential "";
APT::Build-Essential:: "build-essential";
APT::Install-Recommends "0";
APT::Install-Suggests "0";
APT::NeverAutoRemove "";
APT::NeverAutoRemove:: "^linux-image.*";
APT::NeverAutoRemove:: "^linux-restricted-modules.*";
APT::Install-Recommends-Section "metapackages";
APT::Periodic "";
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Archives "";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
APT::Acquire "";
APT::Acquire::Translation "environment";
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::userstatus "status.user";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache::pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::dpkg "/usr/bin/dpkg";
aptitude "";
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$";
Unattended-Upgrade "";
Unattended-Upgrade::Allowed-Origins "";
Unattended-Upgrade::Allowed-Origins:: "Ubuntu edgy-security";
DPkg "";
DPkg::Pre-Install-Pkgs "";
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg::Post-Invoke "";
DPkg::Post-Invoke:: "if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi";
```

how can i reinstalla apt? thanks!

---

### Post by renzokuken on 2007-02-12
shouldnt it be

```
sudo apt-get [color=blue]update[/color]
```

instead of 

```
sudo apt-get [color=red]upgrade[/color]
```

---

### Post by krantix on 2007-02-12
both don't work, one is for updating the software apt-get, the other to update the list....

---

### Post by bapoumba on 2007-02-12
[http://ubuntuforums.org/showthread.php?t=332671]("http://ubuntuforums.org/showthread.php?t=332671")
Does that helps ?

Merging this thread with your previous thread.

---

### Post by krantix on 2007-02-12
not really.... :-(

---

### Post by music2myear on 2007-02-12
sry duplicate post, haven't ironed out the firefox plugins yet, heh:(

---

### Post by music2myear on 2007-02-12
I started having this exact same error (As in original post) 4 days ago on a fresh install of Ubuntu 6.10

No customization, no additional packages added. Just first reboot after GUI (live CD) install of ubuntu on laptop that has run exact same thing no problems since november.

> 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


But the solution I found on linuxquestions.org fixed it.
([http://www.linuxquestions.org/questions/showthread.php?t=155478](http://www.linuxquestions.org/questions/showthread.php?t=155478))

Rename the status-old file to status, and I was all set. Will post if this happens again.
([http://www.tuxfiles.org/linuxhelp/fileman.html](http://www.tuxfiles.org/linuxhelp/fileman.html))

What I thought was odd was the way it was corrupt on initial fresh install...

---

### Post by krantix on 2007-02-13
don't know why, but the solution was to "touch" the status file. After that everything started to work again...

---

### Post by Ramses de Norre on 2007-02-13
You copied /etc/group to /var/lib/dpkg/status ?!?
Kind of dangerous operation to perform... However, it seems like creating a new empty status file fixed it.
May I ask what's in the status file now? (A snippet is enough, the file is probably pretty large, 29898 lines here)

---

### Post by mozetti on 2007-02-13
Thanks for following up! I've been having the same problem for the past couple weeks, but didn't have the time to sort it out. I'll try your solution when i get home this evening.

---

### Post by krantix on 2007-02-13
something like this...

Package: xmodmap
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 76
Maintainer: Daniel Stone <daniel.stone@ubuntu.com>
Architecture: i386
Version: 1:1.0.1-0ubuntu1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4-1), libx11-6
Description: X input map modification
 xmodmap is a tool to modify the input maps of X servers (both keyboards
 and mice), to modify key and mouse button events.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'app/xmodmap' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

Package: gstreamer0.8-vorbis
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 144
Maintainer: Maintainers of GStreamer packages <pkg-gstreamer-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: gst-plugins0.8
Version: 0.8.12-4ubuntu1
Depends: libc6 (>= 2.4-1), libglib2.0-0 (>= 2.11.3), libgstreamer0.8-0 (>= 0.8.11), libogg0 (>= 1.1.3), libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libxml2 (>= 2.6.26), zlib1g (>= 1:1.2.1), gstreamer0.8-misc (>= 0.8.12)
Description: Vorbis plugin for GStreamer
 This GStreamer plugin enables the encoding and decoding of Ogg Vorbis
 compressed audio streams.
 .
 [http://www.vorbis.com/](http://www.vorbis.com/)

Package: libbonoboui2-0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 504
Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: libbonoboui
Version: 2.16.0-0ubuntu1
Replaces: libbonoboui2-common (<= 2.4.3-1)
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.12.1), libbonobo2-0 (>= 2.15.0), libc6 (>= 2.4-1), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.3.0), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.0), libgnome2-0 (>= 2.14.1), libgnomecanvas2-0 (>= 2.11.1), libgnomevfs2-0 (>= 2.15.90), libgtk2.0-0 (>= 2.10.0), libice6, liborbit2 (>= 1:2.14.1), libpango1.0-0 (>= 1.14.2), libpopt0 (>= 1.10), libsm6, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.26), libxrandr2, libxrender1, libbonoboui2-common (= 2.16.0-0ubuntu1)
Description: The Bonobo UI library
 This package contains the Bonobo UI library.

---

### Post by Ramses de Norre on 2007-02-13
Seems like it got regenerated, nice :)
Any idea how you managed to copy your group file to /var/lib/dpkg/status ?

---

### Post by krantix on 2007-02-13
sudo sh -c "mv /var/lib/dpkg/status /var/lib/dpkg/status.bak; sudo apt-get update"

did the job! i've received this clue on the irc channel for ubuntu!!!

---

### Post by bapoumba on 2007-02-13
Nice to see you worked it out, and thank you for posting your fix :)

---

