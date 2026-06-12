---
title: "Borked apt-get, maybe found bug, need help fixing system"
date: 2014-05-01
forum: General Help
---

### Post by jamesisin on 2014-05-01
I was running 14.04 as an unpriv'd user and wanted to install VLC.  I hopped into Software Center and was prompted to enter the creds for a priv'd user.  All seemed fine until the process derailed somewhere behind the scenes.

Subsequently I have rebooted and logged in as an admin and tried various methods for getting apt-get back in order (including *sudo apt-get -f install* which fails).

Here is some relative information:

```
The following packages have unmet dependencies:

libmatroska6: Depends: libc6 (>= 2.14) but 2.19-0ubuntu6 is installed
              Depends: libebml4 but it is not installed
              Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is installed
              Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is installed
vlc-nox: Depends: libavcodec-extra-54 (>= 6:9.11) but it is not installed
         Depends: libavformat54 (>= 6:9.1-1) but 6:9.11-2ubuntu2 is installed
         Depends: libavutil52 (>= 6:9.1-1) but 6:9.11-2ubuntu2 is installed
         Depends: libbluray1 (>= 1:0.4.0) but 1:0.5.0-1 is installed
         Depends: libc6 (>= 2.16) but 2.19-0ubuntu6 is installed
         Depends: libdvdnav4 (>= 4.1.4-1219) but 4.2.1-3 is installed
         Depends: libdvdread4 (>= 4.1.3) but 4.2.1-2ubuntu1 is installed
         Depends: libebml4 but it is not installed
         Depends: libfaad2 (>= 2.7) but 2.7-8 is installed
         Depends: libfontconfig1 (>= 2.9.0) but 2.11.0-0ubuntu4 is installed
         Depends: libfreetype6 (>= 2.2.1) but 2.5.2-1ubuntu2 is installed
         Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is installed
         Depends: libgnutls28 (>= 3.2.10-0) but 3.2.11-2ubuntu1 is installed
         Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu3 is installed
         Depends: libncursesw5 (>= 5.6+20070908) but 5.9+20140118-1ubuntu1 is installed
         Depends: libpostproc52 (>= 5:0.git20120217~) but 6:0.git20120821-4 is installed
         Depends: libsmbclient (>= 2:4.0.3+dfsg1) but 2:4.1.6+dfsg-1ubuntu2 is installed
         Depends: libstdc++6 (>= 4.6) but 4.8.2-19ubuntu1 is installed
         Depends: libswscale2 (>= 6:9.1-1) but 6:9.11-2ubuntu2 is installed
         Depends: libudev1 (>= 183) but 204-5ubuntu20 is installed
         Depends: libxml2 (>= 2.7.4) but 2.9.1+dfsg1-3ubuntu4 is installed
         Depends: zlib1g (>= 1:1.2.0.2) but 1:1.2.8.dfsg-1ubuntu1 is installed

```

Here is the output from *-f install*:

```
sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libebml4
The following NEW packages will be installed:
  libebml4
0 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
5 not fully installed or removed.
Need to get 0 B/51.7 kB of archives.
After this operation, 178 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 208770 files and directories currently installed.)
Preparing to unpack .../libebml4_1.3.0-2_amd64.deb ...
Unpacking libebml4:amd64 (1.3.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package libebml3:amd64 1.3.0-0~ppa0
Errors were encountered while processing:
 /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I think I need to purge what was downloaded but I'm at a loss as to how to do that.  But of course that's just my guess.

Who's up for an adventure?

---

### Post by llamabr on 2014-05-01
Sometimes these dependencies weirdnesses work themselves out in a day or two.  In the meantime, have you messed with your sources.list?  Would could take a look at the output of:

```
cat /etc/sources.list
```

---

### Post by deadflowr on 2014-05-01
I noticed this
```
libebml3:amd64 1.3.0-0~ppa0
```
Do you have a ppa installed somewhere?
A relic ppa, perhaps.

---

### Post by jamesisin on 2014-05-01
At this point I have disabled all additional PPA's.  Previously I had disabled some from before the upgrade from 13.10 to 14.04 (as no longer necessary).

There is no file at /etc/sources.list.

---

### Post by deadflowr on 2014-05-01
Like the poster, I, too, missed that
the file is
```
/etc/**apt**/sources.list
```
lol

But, I noticed you have a few packages with upgrades ready.
(36, I think)

Perhaps upgrading those will brings things in order.

---

### Post by jamesisin on 2014-05-02
Damn.  Easy to miss.

Let me know your thoughts.

```
cat /etc/apt/sources.list

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to

# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu saucy partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb http://deb.opera.com/opera/ stable non-free #Opera
# deb-src http://deb.opera.com/opera/ stable non-free #Opera
# deb-src http://extras.ubuntu.com/ubuntu saucy main
deb http://archive.canonical.com/ trusty partner
# deb-src http://archive.canonical.com/ saucy partner
```

---

### Post by jamesisin on 2014-05-02
Oh, I get the same error when I attempt to run the updates:

```
sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libmatroska6 : Depends: libebml4 but it is not installed
 vlc-nox : Depends: libebml4 but it is not installed
           Recommends: libdvdcss2 but it is not installable
E: Unmet dependencies. Try using -f.
```

---

### Post by bapoumba on 2014-05-02
```
ls /etc/apt/sources.list.d
```
Any other third party repo or ppa in here ?

---

### Post by jamesisin on 2014-05-02
Yep.

```
ls /etc/apt/sources.list.d

jacob-media-saucy.list              me-davidsansome-clementine-saucy.list              medibuntu.list
jacob-media-saucy.list.distUpgrade  me-davidsansome-clementine-saucy.list.distUpgrade
jacob-media-saucy.list.save         me-davidsansome-clementine-saucy.list.save
```

---

### Post by bapoumba on 2014-05-02
These are for saucy. Could you please disable them from Software Sources ?

---

### Post by jamesisin on 2014-05-03
They have already been disabled in SS.  I mentioned that above.  The *only* repo checked in SS --> Other Software is Canonical Partners.  Can I safely delete those entries from /etc/apt/sources.list.d?  Or is there some other preferred method?

On a perhaps unrelated note, I have two entries for Canonical Partners (and two for CP Source Code).  This seems to have happened from the upgrade.  Curiously, both of the CP are listed as Trusty while both of the Source Codes entries are listed as Saucy.  I want to remove one of each and make the remaining pair both Trusty, but let me know if that would be a problem.

Thanks for your time and knowledge.

Not sure that it matters but one pair (a repo and a Source Code) list [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) (same as my other 14.04 machine, also upgraded) while the other pair lists [http://archive.canonical.com/](http://archive.canonical.com/) (I think this is the hold-over from 13.10 but am not 100 per cent).

(Incidentally, disabling that last repo made no change in behavior.)

---

### Post by ian-weisser on 2014-05-03
> **jamesisin said:**
> 
Unpacking libebml4:amd64 (1.3.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package libebml3:amd64 1.3.0-0~ppa0


It's not enough to disable the PPA. The conflicting package is *already installed* on your system.

Uninstall the conflicting package (and the PPA application that depends upon it).
Looking through the reverse dependencies, that looks like a PPA version of VLC or some other media player.
```
sudo apt-get autoremove libebml3:amd64        # Remove the conflicting dependency
sudo apt-get update
sudo apt-get upgrade                           # Verify the package manager is working
sudo apt-get install vlc-nox                    # This seems to be what you originally wanted

```

Yeah, PPAs do that.

---

### Post by jamesisin on 2014-05-03
Unfortunately I had already tried variations on that theme:

```
sudo apt-get autoremove libebml3:amd64

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmatroska6 : Depends: libebml4 but it is not going to be installed
 vlc-nox : Depends: libebml4 but it is not going to be installed
           Recommends: libdvdcss2 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by bapoumba on 2014-05-03
I suppose you have all your backups nicely done just in case. Not for the suggestions here, but if they do not work.

Please try :
```
sudo apt-get remove vlc
```

If you want, you may try :
```
sudo apt-get autoremove vlc
```
Which should take care of its deps too. Just found out the other day that autoremove could be use with <package_name>.

---

### Post by Ubi_one_2014 on 2014-05-03
you did already:
apt-get -f install [enter]

??

---

### Post by jamesisin on 2014-05-03
Yep.  Tried all of that.

```
sudo apt-get remove vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmatroska6 : Depends: libebml4 but it is not going to be installed
 vlc-nox : Depends: libebml4 but it is not going to be installed
           Recommends: libdvdcss2 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

sudo apt-get autoremove vlc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmatroska6 : Depends: libebml4 but it is not going to be installed
 vlc-nox : Depends: libebml4 but it is not going to be installed
           Recommends: libdvdcss2 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

sudo apt-get purge vlc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmatroska6 : Depends: libebml4 but it is not going to be installed
 vlc-nox : Depends: libebml4 but it is not going to be installed
           Recommends: libdvdcss2 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

In Synaptic (when did I install that? lucky me) there is an option to Fix Broken Packages.

When Synaptic opens it suggests that since I have broken packages I should use the Broken filter to locate them.  There are two packages listed (which we already know):  **vlc-nox** and **libmatroska6**.

If after all of that I attempt to apply changes ("**libebml4** (version 1.2.0-2 will be installed") I get this:

```

(synaptic:9233): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 208770 files and directories currently installed.)
Preparing to unpack .../libebml4_1.3.0-2_amd64.deb ...
Unpacking libebml4:amd64 (1.3.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package libebml3:amd64 1.3.0-0~ppa0
Errors were encountered while processing:
 /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libmatroska6:amd64:
 libmatroska6:amd64 depends on libebml4; however:
  Package libebml4:amd64 is not installed.

dpkg: error processing package libmatroska6:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libebml4; however:
  Package libebml4:amd64 is not installed.
 vlc-nox depends on libmatroska6; however:
  Package libmatroska6:amd64 is not configured yet.

dpkg: error processing package vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 2.1.2-2build2); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 2.1.2-2build2); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 2.1.2-2build2); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmatroska6:amd64
 vlc-nox
 vlc
 vlc-plugin-notify
 vlc-plugin-pulse


```

---

### Post by Ubi_one_2014 on 2014-05-03
try:

apt-get remove libmatroska6 vlc-nox

---

### Post by jamesisin on 2014-05-03
Ok, looks like I may have fixed it.

I closed and reopened Synaptic and went directly to the Broken filter.  I marked the first package for Complete Removal (the other is a dependency so that's sufficient).  This worked.

Back to the terminal to run *sudo apt-get -f install && sudo apt-get autoremove && sudo apt-get autoclean*.  Now I'm going to reboot but I should be golden.

Thanks to everyone for contributing to this solution.  You can all bask in my newest buzzword: intercontribution.

---

### Post by Ubi_one_2014 on 2014-05-03
lovely

cheers m8

---

### Post by jamesisin on 2014-05-03
Prematurely marked as solved.  Though my system is back in order and I can run my updates and apt-get seems fine, I can reliably break the system by attempting to install VLC through the Software Center.  (I can then reliably fix it by running Complete Removal through Synaptic as per above.)

What's up with Software Center and VLC?

---

### Post by bapoumba on 2014-05-03
Ah cool, glad to see you got it fixed :)
Please mark your thread as solved (under Thread Tools), thanks!

---

### Post by bapoumba on 2014-05-03
> **jamesisin said:**
> Prematurely marked as solved.  Though my system is back in order and I can run my updates and apt-get seems fine, I can reliably break the system by attempting to install VLC through the Software Center.  (I can then reliably fix it by running Complete Removal through Synaptic as per above.)

What's up with Software Center and VLC?

What is the output to
```
sudo apt-get install vlc 
```

---

### Post by ian-weisser on 2014-05-03
> **jamesisin said:**
> 
 vlc-nox : Depends: libebml4 but it is not going to be installed
           Recommends: libdvdcss2 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Ah. The package vlc-nox is marked for installation. Unmark it.
```
sudo dpkg --set-selections
vlc-nox deinstall                    # One package per line, hit ENTER
^D                                      # CTRL+D to end
```

---

### Post by jamesisin on 2014-05-03
I found that vlc-data was still installed and removed that.  No change.  Here is the failure of Software Center to install VLC:

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 208008 files and directories currently installed.)
Preparing to unpack .../libebml4_1.3.0-2_amd64.deb ...
Unpacking libebml4:amd64 (1.3.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package libebml3:amd64 1.3.0-0~ppa0
Selecting previously unselected package libmatroska6:amd64.
Preparing to unpack .../libmatroska6_1.4.1-2_amd64.deb ...
Unpacking libmatroska6:amd64 (1.4.1-2) ...
Selecting previously unselected package vlc-data.
Preparing to unpack .../vlc-data_2.1.2-2build2_all.deb ...
Unpacking vlc-data (2.1.2-2build2) ...
Selecting previously unselected package libvlccore7.
Preparing to unpack .../libvlccore7_2.1.2-2build2_amd64.deb ...
Unpacking libvlccore7 (2.1.2-2build2) ...
Selecting previously unselected package libvlc5.
Preparing to unpack .../libvlc5_2.1.2-2build2_amd64.deb ...
Unpacking libvlc5 (2.1.2-2build2) ...
Selecting previously unselected package vlc-nox.
Preparing to unpack .../vlc-nox_2.1.2-2build2_amd64.deb ...
Unpacking vlc-nox (2.1.2-2build2) ...
Selecting previously unselected package vlc.
Preparing to unpack .../vlc_2.1.2-2build2_amd64.deb ...
Unpacking vlc (2.1.2-2build2) ...
Selecting previously unselected package vlc-plugin-notify.
Preparing to unpack .../vlc-plugin-notify_2.1.2-2build2_amd64.deb ...
Unpacking vlc-plugin-notify (2.1.2-2build2) ...
Selecting previously unselected package vlc-plugin-pulse.
Preparing to unpack .../vlc-plugin-pulse_2.1.2-2build2_amd64.deb ...
Unpacking vlc-plugin-pulse (2.1.2-2build2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of libmatroska6:amd64:
 libmatroska6:amd64 depends on libebml4; however:
  Package libebml4:amd64 is not installed.

dpkg: error processing package libmatroska6:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up vlc-data (2.1.2-2build2) ...
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libebml4; however:
  Package libebml4:amd64 is not installed.
 vlc-nox depends on libmatroska6; however:
  Package libmatroska6:amd64 is not configured yet.

dpkg: error processing package vlc-nox (--configure):
 dependency problems - leaving unconfigured
Setting up libvlccore7 (2.1.2-2build2) ...
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 2.1.2-2build2); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 2.1.2-2build2); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
Setting up libvlc5 (2.1.2-2build2) ...
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 2.1.2-2build2); however:
  Package vlc-nox is not configured yet.

dpkg: error processing package vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.19-0ubuntu6) ...

```

Looks like the problem might be in this archive: **libebml4_1.3.0-2_amd64.deb**.

---

### Post by jamesisin on 2014-05-03
As to *libebml4*, Synaptic believes it is not installed.  If I mark it for installation and apply:

```
E: /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb: trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package **libebml3**:amd64 1.3.0-0~ppa0
```

and

```
(synaptic:11388): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 208008 files and directories currently installed.)
Preparing to unpack .../libebml4_1.3.0-2_amd64.deb ...
Unpacking libebml4:amd64 (1.3.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package **libebml3**:amd64 1.3.0-0~ppa0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```

So I Complete Removed *libebml3*.  This allowed me to install VLC, but of course I am suspicious something else may still be wrong.

On a perhaps related note, VLC fails to open a CD in the tray:

```
Your input can't be opened:
VLC is unable to open the MRL 'cdda:///dev/cdrom1'. Check the log for details.
```

Or (since there does not appear to be a log file...)

```
vlc
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)
[0x756118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x7f58380009b8] main input error: open of `cdda:///dev/cdrom1' failed
```

It shows the CD in the playlist (cdda:///dev/cdrom1) rather than the tracks (which would be normal).

(Rhythmbox is capable of playing that same CD.)

---

### Post by jamesisin on 2014-05-03
Sorry, I did all this other work while you cats were replying.  Let me know if there is more you can offer,

---

### Post by Yellow Pasque on 2014-05-03
The problem was that you didn't run ppa-purge on this ppa before upgrading. [https://launchpad.net/~jacob/+archive/media](https://launchpad.net/~jacob/+archive/media)

---

### Post by jamesisin on 2014-05-03
I've never purged a PPA before moving to the next version of the OS.  What command would that be?  Should the upgrading software have been managing that?

---

### Post by jamesisin on 2014-05-03
I am marking this as solved again since the VLC CD problem is also happening on a fresh installation of Ubuntu 14.04 I have here.  VLC is working for CD's in 13.10.

---

### Post by ian-weisser on 2014-05-03
> **jamesisin said:**
> Should the upgrading software have been managing that?
"upgrading software" generally does not manage itself. There _is_ a lot of information in the deb file explaining to the package manager (dpkg) what the package is, what it does, what version it is, it's minimum requirements, etc.

You have two packages that don't admit to being different versions of the same lib. Instead, they claim to be different libs that provide the same file....That's why the package manager cannot resolve the problem and kicked the error out to the human (you) to fix.

For software in the Ubuntu Repositories, Ubuntu regularly and systematically tests for proper upgrades. If you use Ubuntu Repository packages, this problem won't happen.

But you're upgrading from a PPA version. PPAs are not supported software, and are not in the Ubuntu Repositories. If the PPA owner doesn't test upgrades, nobody else will.

Safe practice before a release-upgrade is to uninstall all non-Ubuntu software. Leaving it on usually does not result in a problem like yours...but occasionally it causes problems.

---

### Post by jamesisin on 2014-05-05
And by that you mean the user must remember any and all software installed (including any dependencies) from a non-Ubuntu source and purge said software prior to running the version upgrade for the OS?

---

### Post by ian-weisser on 2014-05-05
Yes.
You -the system owner or admin- are ultimately responsible for the  stuff you choose to install on your system, including if you choose to  install unsupported stuff that breaks the package manager.

You can install unsupported stuff from PPAs *all you want*. Go ahead. I do it too. But you must keep track of it...because it occasionally causes problems like yours. Not every time. Not most times. But enough.

That's why we recommend using the Ubuntu Repositories when possible. If you fish around these forums, you will find no less than *six* active threads that I'm following where a PPA or other non-Ubuntu software has broken a user's system by breaking package management. None are the fault of the package manager. I know of zero active threads where Ubuntu Repository software has broken a user's system the same way.

---

### Post by jamesisin on 2014-05-06
If that's important and if the system allows the adding of additional repositories, why has no one created a simple method by which one might ask the system "which packages do I have installed from repository X?"?

This would seem obvious if one is expected to remove said packages prior to upgrading the OS.

I mean, the upgrading software (update-manager installs an additional piece of software to manage the version upgrade but I don't recall its name) *does* warn users to *disable* additional repositories; in fact if memory serves it disables them itself; but there is certainly no mention of rooting out any packages which may have been previously installed through said repos.

I should think if this were, as you seem to imply, a best practice there would be some mention of it.  Here are the three top hits from Google for upgrading from 13.10 to 14.04:

[http://www.tecmint.com/upgrade-ubuntu-to-14-04/](http://www.tecmint.com/upgrade-ubuntu-to-14-04/)

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Upgrading_from_Ubuntu_13.10](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Upgrading_from_Ubuntu_13.10)

[https://help.ubuntu.com/community/TrustyUpgrades](https://help.ubuntu.com/community/TrustyUpgrades)

None of them make any mention of removing non-Ubuntu repositories, software, or dependencies.

In my case there were other anomalies in the list of repositories.  I am dubious of the idea that the mere presence of those packages is what broke the package manager.  *Apt* was unable to overwrite a file; regardless of the source of said file, that's a different sort of issue.

Why wasn't *apt* able to overwrite the file?  Why wasn't *apt* able to remove the file?

Finally I have upgraded other machines having those same repositories and not run into this same issue (nor the odd entries in the repo list).

Yes, I am going to remain dubious that your theory is exactly correct (though there are compelling elements to it).  Perhaps though I have misunderstood your case and your forensic analysis is more enticing than my vision of it.

---

### Post by Yellow Pasque on 2014-05-06
> **jamesisin said:**
> If that's important and if the system allows the adding of additional repositories, why has no one created a simple method by which one might ask the system "which packages do I have installed from repository X?"?

You can see that in Synaptic by sorting with the 'Origin' button.

> This would seem obvious if one is expected to remove said packages prior to upgrading the OS.
That's what ppa-purge is for.

> Why wasn't *apt* able to overwrite the file?  Why wasn't *apt* able to remove the file?
Because it's against Debian policy to overwrite files from other packages or just remove individual files. If apt did that, things would get very messy...

I do feel your pain, though. I'm not a big fan of the 6 month upgrade dance or its many anomalies (that's why I switched to Debian sid so I could just roll). I;m of the opinion that Ubuntu should only release LTS versions and just let the non-LTS users roll (especially since they cut down non-LTS support to 9 months). I'm getting off-topic though...

---

### Post by bapoumba on 2014-05-06
> **jamesisin said:**
> 
Why wasn't *apt* able to overwrite the file?  Why wasn't *apt* able to remove the file?

Finally I have upgraded other machines having those same repositories and not run into this same issue (nor the odd entries in the repo list).


apt deals with dependencies. dpkg does what apt instructs it to do, ie install this or remove that. dpkg does not care about dependencies, that is left to the package manager to decide. Packages tell the package manager which versions of which file they depend upon, and the package manager's duty is to keep all dependencies and all versions coherent in a given distribution. If there is a conflict, then they tell the user and the user has to fix it.

Maybe the other machines did not have the same packages installed than the one giving you troubles ?

---

