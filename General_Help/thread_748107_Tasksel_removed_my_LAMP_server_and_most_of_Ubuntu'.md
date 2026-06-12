---
title: "Tasksel removed my LAMP server and most of Ubuntu's desktop!"
date: 2008-04-07
forum: General Help
---

### Post by richard.collins on 2008-04-07
In short: In error I ran tasksel option '12: remove all...' and quited! :( Now I want to ensure everything's restored OK!

*While reading about MySQL,* I followed a link to the Ubuntu 7.04 LAMP installation page and saw the link to Tasksel. Without reading *carefully* that tasksel can *uninstall* as well install packages, I ran it from the command line to have a look. For some reason a text version appeared - no nice blue & grey GUI - and not knowing how to exit safely, I entered '12' [return] to choose 'None of the above' *expecting* it to **do nothing and quit**!

'**None** of the above' turned out to mean '**remove** everything listed'! Help! And without warning, off it went. My LAMP server was first to go, followed by most of the Ubuntu desktop before I managed to stop it mid flow - I think using Cntrl-Z. I should have known what I was doing as I've some experience with Unix, but that was a long time ago!

With help, as tasksel failed when I tried to use it to reinstall what it had removed:
```
$ sudo tasksel
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
xserver-xorg install
tasksel: aptitude failed (100)
$
```I ran:
```
$ sudo dpkg --configure -a

```Still tasksel failed with 'tasksel: aptitude failed (100)' so I ran a number of commands:
```
$ sudo apt-get update
$ sudo apt-get install xserver-xorg
Reading package lists... Done
Building dependency tree
Reading state information... Done
xserver-xorg is already the newest version.
The following packages were automatically installed and are no longer required:
libcompizconfig0 libdecoration0 libcairomm-1.0-1 libmcrypt4 libglibmm-2.4-1c2a libt1-5
python-compizconfig libgtkmm-2.4-1c2a libgd2-xpm php5-common libltdl3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$

```which doesn't appear to have done anything, then:
```
$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20080404190104
$
```and
```
$ sudo aptitude install xserver-xorg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initialising package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
$
```'State information' might not have reflected what had been removed as I'd stopped tasksel abruptly, but perhaps 'Writing extended state information' has fixed that. Anyway, with tasksel still failing on 'aptitude' I used the **Synaptic Package Manager** to reinstall my Ubuntu desktop - it was not showing up as 'installed' - and the various parts of my LAMP server. Everything seems to be working fine now and I've managed to restart our server. Amazing considering!

Before I did anything to remedy the situation, I found most of the desktop tools were missing although **Update Manager** was still there and told me my system was up-to-date!? That's nice considering I'd removed most of the desktop and couldn't even browse my directories!  Fortunately, SPM was still operative, and throughout this horrendous experience, Firefox has continued to run, so I've been able to get interactive support *but I've not rebooted*... yet!

I originally installed Ubuntu 7.04 from CD no problem, kept it up-to-date, and my son did all the LAMP installation and configuration. I understand tasksel only removes binaries and not config files, so I can still browse to my server [https://richard/trac](https://richard/trac) and view our CMS development wiki, tickets, etc., although I can't browse the source code in the SVN repository using Trac - it's all there still as Trac offers a download option. Perhaps I've missed a package Trac needs to 'preview html'? I was getting an error restarting the server - remedied by adding some python packages. Trac uses python, and a startup script was failing.

**My questions are:**
Does tasksel remove anything critical that I've missed, so that when I do reboot I won't be able to log in as normal, see the desktop and run applications? If I'm faced with just the command line... :confused:

Should I upgrade to 7.10 ***before*** rebooting, in the hope that anything missing will be installed OK? Or might that make any 'unknowns' worse? I have run the upgrade to the point of it asking whether I want to continue to download and install, and all seems to be OK. The installer reports that it will remove 9 packages, install 122 and update 941 - but what if some are missing while the registry (state information?) 'says' they are installed?

Have I got that right? Is there a file saying what's installed - is that the 'state information' - that might be out of step with what's actually there? I guess tasksel only updates the registry when it's finished doing a remove - and I stopped it mid-way. But 'aptitude install xserver-xorg' seems to have corrected that?

Perhaps I should have posted this in 'Absolute Beginners' but what a naff interface tasksel has! :(

---

### Post by neoflight on 2008-04-28
i went through the same thing yesterday. you cannot boot into the gnome desktop!..
do these...

log in as root (safe mode: usually 2nd menu in the grub) and install ubuntu-desktop.
else try gnome-desktop-environment, gnome-utils, gnome-themes etc..
go step by step by installing missing things...
apt-get install gnome-[hit tab] to get the names of packages 
(if you haven't cleared the cached package lists)
thats all possible if you your internet is working...
if you hit dependency problems then try 
```
dpkg --configure -a
```
and 
```
apt-get install -f
```

i fixed mine without a reinstall...hope this helps...

---

