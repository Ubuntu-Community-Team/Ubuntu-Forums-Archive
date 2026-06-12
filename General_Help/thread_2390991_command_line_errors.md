---
title: "command line errors"
date: 2018-05-04
forum: General Help
---

### Post by amterry77 on 2018-05-04
Newbie here looking for some assistance

Having been getting errors trying to run updates, installs or removals of my applications. Does not matter which types of commands i run

```
[-----]:~$ sudo dpkg --configure -a
Setting up ifupdown (0.8.10ubuntu1.3) ...
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service smbd and cups if stopped
insserv:  loop involving service cups at depth 2
insserv:  loop involving service smbd at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ifupdown (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up uuid-runtime (2.27.1-6ubuntu3.4) ...
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service smbd and cups if stopped
insserv:  loop involving service cups at depth 2
insserv:  loop involving service smbd at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package uuid-runtime (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up avahi-daemon (0.6.32~rc+dfsg-1ubuntu2.2) ...
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service smbd and cups if stopped
insserv:  loop involving service cups at depth 2
insserv:  loop involving service smbd at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package avahi-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up plymouth (0.9.2-3ubuntu13.4) ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service smbd and cups if stopped
insserv:  loop involving service cups at depth 2
insserv:  loop involving service smbd at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package plymouth (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up udev (229-4ubuntu21.2) ...
addgroup: The group `input' already exists as a system group. Exiting.
update-initramfs: deferring update (trigger activated)
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service smbd and cups if stopped
insserv:  loop involving service cups at depth 2
insserv:  loop involving service smbd at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up grub-common (2.02~beta2-36ubuntu3.17) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service smbd and cups if stopped
insserv:  loop involving service cups at depth 2
insserv:  loop involving service smbd at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of avahi-utils:
 avahi-utils depends on avahi-daemon; however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package avahi-utils (--configure):
 dependency problems - leaving unconfigured
Setting up apport (2.20.1-0ubuntu2.16) ...
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service smbd and cups if stopped
insserv:  loop involving service cups at depth 2
insserv:  loop involving service smbd at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package apport (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up samba (2:4.3.11+dfsg-0ubuntu0.16.04.13) ...
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service smbd and cups if stopped
insserv:  loop involving service cups at depth 2
insserv:  loop involving service smbd at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of avahi-discover:
 avahi-discover depends on avahi-daemon; however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package avahi-discover (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on udev (>= 143); however:
  Package udev is not configured yet.

dpkg: error processing package pulseaudio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-logo:
 plymouth-theme-ubuntu-logo depends on plymouth (= 0.9.2-3ubuntu13.4); however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-theme-ubuntu-logo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.02~beta2-36ubuntu3.17); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.9.2-3ubuntu13.4); however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-label (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools-core:
 initramfs-tools-core depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package initramfs-tools-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth (= 0.9.2-3ubuntu13.4); however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.02~beta2-36ubuntu3.17); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.02~beta2-36ubuntu3.17); however:
  Package grub-pc-bin is not configured yet.

dpkg: error processing package grub-pc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-36ubuntu3.17); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-x11:
 pulseaudio-module-x11 depends on pulseaudio (= 1:8.0-0ubuntu3.10); however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-module-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-core (= 0.122ubuntu8.11); however:
  Package initramfs-tools-core is not configured yet.

dpkg: error processing package initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of snapd:
 snapd depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package snapd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio (= 1:8.0-0ubuntu3.10); however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-core-launcher:
 ubuntu-core-launcher depends on snapd (= 2.32.3.2); however:
  Package snapd is not configured yet.

dpkg: error processing package ubuntu-core-launcher (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Errors were encountered while processing:
 ifupdown
 uuid-runtime
 avahi-daemon
 plymouth
 udev
 grub-common
 avahi-utils
 apport
 samba
 avahi-discover
 pulseaudio
 plymouth-theme-ubuntu-logo
 grub-pc-bin
 plymouth-label
 initramfs-tools-core
 plymouth-theme-ubuntu-text
 grub-pc
 grub2-common
 pulseaudio-module-x11
 apport-gtk
 initramfs-tools
 snapd
 pulseaudio-module-bluetooth
 ubuntu-core-launcher
```

---

### Post by TheFu on 2018-05-04
Which release?  Some things change over time.  I see the ipupdown package ... that has changed so knowing the release is critical.

Using *dpkg* directly can cause dependency issues.  Stay with apt, apt-get, and aptitude.  Also, stay with packages from Canonical/Ubuntu repositories.  Avoid downloading .deb files.  Those often break dependencies.

Let's start with 1 command at a time.
**sudo apt update**
Please show the command and any **interesting** output from it.  We don't need to see 500 lines of stuff that looks the same. We need to see the command, first few lines that look fine, some lines that work ... and some that fail. We need to see any errors, warnings, suggestions, and the ending.  So ... 20-35 lines.  The output almost always has suggestions, btw.

Then we can move on to the "update" command, if there aren't any issues.

If you want more tips for getting used to Ubuntu/Linux fast, ask.  Windows knowledge sometimes is exactly the opposite of what needs to happen.

---

### Post by amterry77 on 2018-05-20
Thank for responding

here is what I have picked out

```
Ign:1 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial InRelease
Err:2 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial Release
  Please use apt-cdrom to allow APT to recognise this CD-ROM. 'apt-get update' cannot be used to add new CD-ROMs
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]    
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]     
Hit:7 [http://ppa.launchpad.net/gerardpuig/ppa/ubuntu](http://ppa.launchpad.net/gerardpuig/ppa/ubuntu) xenial InRelease          
Ign:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:9 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:10 [http://ppa.launchpad.net/iconnor/zoneminder/ubuntu](http://ppa.launchpad.net/iconnor/zoneminder/ubuntu) xenial InRelease     
Hit:11 [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) xenial InRelease         
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB] 
Hit:13 [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) xenial InRelease        
Get:14 [https://downloads.plex.tv/repo/deb](https://downloads.plex.tv/repo/deb) public InRelease [3,408 B]
Hit:15 [http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu](http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu) xenial InRelease
Hit:16 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) xenial InRelease
Hit:17 [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) xenial InRelease        
Hit:18 [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) xenial InRelease
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [319 kB]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [227 kB]
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [67.8 kB]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [246 kB]
Get:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [68.0 kB]
Get:25 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [107 kB]
Get:26 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [147 kB]
Get:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [331 kB]
Get:28 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,964 B]
Get:29 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:30 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [5,088 B]
Err:14 [https://downloads.plex.tv/repo/deb](https://downloads.plex.tv/repo/deb) public InRelease    
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 97203C7B3ADCA79D
Reading package lists... Done 
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/iconnor-ubuntu-zoneminder-xenial.list:2 and /etc/apt/sources.list.d/iconnor-ubuntu-zoneminder-xenial.list:3
E: The repository 'cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [https://downloads.plex.tv/repo/deb](https://downloads.plex.tv/repo/deb) public InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 97203C7B3ADCA79D
E: The repository 'https://downloads.plex.tv/repo/deb public InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/iconnor-ubuntu-zoneminder-xenial.list:2 and /etc/apt/sources.list.d/iconnor-ubuntu-zoneminder-xenial.list:3
```

---

### Post by TheFu on 2018-05-20
The current 16.04 is 16.04.4.  [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life) shows that 16.04.2 support ended. 
16.04.4 will only be supported a few months after 16.04.5 is released.

It appears that an out-of-date CDROM/DVD is listed as a dependency somewhere.  Please clean that up.
Also, remove the plex PPA and any manually installed .deb files.

Your goal is to get a clean 
```
sudo apt update
```
then AFTER that is done cleanly, run 
```
sudo apt dist-upgrade
```
which will get the system to 16.04.4. A reboot will be required.  Then you can find the correct Plex PPA to add back in, be certain to also install any gpg keys for it.  Installing software without verifying gpg keys is like buying a DVD on the corner, just outside a bazaar.  Never know what you are really getting.

---

### Post by amterry77 on 2018-05-24
I cannot thank you enough, I am still a noob.


Managed to get a clean sudo apt update

When running sudo apt dist-upgrade I get this

```
All packages are up-to-date.
admiral@Lcare-Core:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.13.0-36 linux-headers-4.13.0-36-generic
  linux-image-4.13.0-36-generic linux-image-extra-4.13.0-36-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
26 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up procps (2:3.3.10-4ubuntu2.4) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop between service smbd and cups if stopped
insserv:  loop involving service cups at depth 2
insserv:  loop involving service smbd at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.
```

Then it continues with similar loops for different error which i did not want to copy all

Any suggestions?

A

---

### Post by TheFu on 2018-05-24
Remove all non-core APT sources/PPAs, then do the apt update/upgrade again. Does that fix things? I'd also follow the suggestion to autoremove from the output.

BTW, please wrap text output in "code tags" when posting here.  Makes things easier to read.  Adv Reply (#)

---

### Post by amterry77 on 2018-05-24
Does it make me stupid to admit that I would not be fully confident that I know exactly what 
> Remove all non-core APT sources/PPA
Means

---

### Post by TheFu on 2018-05-24
> **amterry77 said:**
> Does it make me stupid to admit that I would not be fully confident that I know exactly what 

Means

Not at all. Explaining it isn't so easy, so I hoped I wouldn't be asked. ;)

**Overview**
Whenever Ubuntu performs an upgrade from release to release, it removes all the non-Canoncial repos to limit the likely dependency failures.   You'll need to manually do this.

The APT repos and PPAs used are in /etc/apt/ in a few different files.  sources.list is usually the core Canonical repos, but extra  repos/PPAs may have been added.  Comment out anything that doesn't have ubuntu.com in the URL.

In /etc/apt/sources.list.d/ is where most PPAs will be added.  Normally, they are 1 to a file.  I have 12.  They are for different software tools that I decided having the newest from the project team was important enough instead of using whatever version Canonical includes in their repos already.   The files end in **.list** - just rename them to be .list.save.  Then do the apt update/upgrade cycle again.

If this doesn't fix it, I'd backup my precious and wipe.  Being in *APT hell* sucks.

---

### Post by amterry77 on 2018-05-27
Thank you for your patience. Decided to start over as you suggested. You have been most generous.

---

### Post by TheFu on 2018-05-27
> **amterry77 said:**
> Thank you for your patience. Decided to start over as you suggested. You have been most generous.

It is much easier to avoid "APT hell" by properly maintaining a system, 
* daily, incremental, versioned,automatic, backups.
* weekly patching
* using reputably PPAs only
* avoiding installing .deb files directly (avoid dpkg)
* avoiding installing anything from source

We can't always do these things, but should try.

Sorry there wasn't a 2-click answer.

---

