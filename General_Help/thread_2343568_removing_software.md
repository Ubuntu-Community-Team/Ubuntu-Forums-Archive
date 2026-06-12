---
title: "removing software"
date: 2016-11-17
forum: General Help
---

### Post by capharol on 2016-11-17
I have a problem with removing a programm, it doesn't remove it at all, not in the software centre and not in Terminal

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package VirtualBox

this is what i get when i use > sudo apt-get remove VirtualBox


> dpkg: dependency problems prevent removal of virtualbox: virtualbox-qt depends on virtualbox (= 5.0.24-dfsg-0ubuntu1.16.04.1); however:
  Package virtualbox is to be removed.
  Package virtualbox-5.1 which provides virtualbox is not installed.


dpkg: error processing package virtualbox (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 virtualbox
This is what I get when i use the command > sudo dpkg --remove --force-remove-reinstreq

In software centre it's starting but seems to stuck (waited for 2 hrs) :evil:


already trying to uninstall it for 2 days now 
am I doing something wrong?, or is there a known issue about removing software with 16.04?

(sorry when i posted it in the wrong thread)

---

### Post by ian-weisser on 2016-11-17
You asked apt to do something impossible.
Apt warned you that it was impossible, and explained why.
You _forced_ apt to do something impossible anyway.
Apt crashed.

Not 16.04's fault. Not apt's fault.

Kill the Software Center process.
Then open a terminal and run an apt update and apt upgrade.
If there are any error messages, then please show us the entire output of both apt sessions.

---

### Post by capharol on 2016-11-17
> **ian-weisser said:**
> 
Then open a terminal and run an apt update and apt upgrade.
If there are any error messages, then please show us the entire output of both apt sessions.

update:
> Ubuntu:~$ sudo apt updateIgn:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial InRelease                           
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                           
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94,5 kB]
Hit:5 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates InRelease                 
Hit:6 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports InRelease                
Fetched 94,5 kB in 0s (136 kB/s)                                                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.

upgrade:
> Ubuntu:~$ sudo apt upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.


after trying to remove:
> sudo dpkg --remove --force-remove-reinstreq VirtualBox(Reading database ... 209571 files and directories currently installed.)
Removing virtualbox (5.0.24-dfsg-0ubuntu1.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...


isn't in my software centre anymore, although it is still in my dirlist

> Ubuntu:~$ dirBilder	 Documents  Downloads	      genymotion-log.zip		      Music	Public	      Templates  [COLOR=#ff0000]**VirtualBox\ VMs**[/COLOR]
Desktop  Dokumente  examples.desktop  google-chrome-stable_current_amd64.deb  Pictures	Schreibtisch  Videos


---

### Post by DuckHook on 2016-11-17
Do all that ian-weisser asks. Additionally, please tell us:

[LIST=1]
[*]How did you install virtualbox? 5.1 is not the version in the repos. This version must be installed either using .deb or through PPA.
[*]If PPA, did you erroneously disable PPA before trying to remove? If so, you would get the crash that you describe. The PPA must still be active at time of removal for proper uninstall.
[*]Which PPA? Oracle's or someone else's?
[*]If .deb, did you follow instructions from Oracle site or some third party site?
[*]Did you install any further vbox utilities from fourth parties after initial vbox install?
[/LIST]
I'm responding on the road from an android tablet which limits my ability to test or research. But anyone helping will find this additional info useful.

---

### Post by capharol on 2016-11-17
> **DuckHook said:**
> Do all that ian-weisser asks. Additionally, please tell us:

[LIST=1]
[*]How did you install virtualbox? 5.1 is not the version in the repos. This version must be installed either using .deb or through PPA.
[*]If PPA, did you erroneously disable PPA before trying to remove? If so, you would get the crash that you describe. The PPA must still be active at time of removal for proper uninstall.
[*]Which PPA? Oracle's or someone else's?
[*]If .deb, did you follow instructions from Oracle site or some third party site?
[*]Did you install any further vbox utilities from fourth parties after initial vbox install?
[/LIST]
I'm responding on the road from an android tablet which limits my ability to test or research. But anyone helping will find this additional info useful.

sorry I'm  a newbie in the Ubuntu world.... 
1. I used the official VirtualBox-site ([https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)), installed VirtualBox for Linux Xenial AMD64
2. not quite sure what you mean but when you ment other packages .... no i didn't
3 and 4. not sure what you mean..... :(
5. yes I tried to install (on top of) another VirtualBox after I have read that there where need of extra packages (virtualbox -qt, virtualbox-dkms)

---

### Post by ian-weisser on 2016-11-17
To fix your problem, uninstall _all_ of your virtualbox packages from _all_ non-Ubuntu sources.
Locating those packages and remembering those sources is left as an exercise for the student.
Then do another apt update and apt upgrade to ensure the package manager is working properly.
If apt has no errors then install virtualbox from the Ubuntu repositories. Apt will automatically include any dependencies (like dkms). That's why we use it.

Be aware that "sudo dpkg --remove --force-remove-reinstreq" is rather a nuclear solution, and may leave fallout scattered across your system that must be cleaned up manually. Time will tell.

Keep regular backups of your data - you made a couple classic Windows-power-user mistakes, and down that path sometimes lies a thoroughly broken system requiring a reinstall.
The power of Linux must be used wisely. It's also the power to break stuff.

---

### Post by ajgreeny on 2016-11-17
First let's see what virtualbox packages you have installed using dpkg, then we can figure out how to remove them, if that is what you really want.
Run terminal command ```
dpkg -l virtualbox*
``` which will tell us everything needed and we can then move forward from there.

For your information, if you like to use a GUI package manager try synaptic in which you casn saerch by name only for virtualbox and it will show all packages and allow you to install or remove them, and if you wish to move from version 5.0 to 5.1 it will automatically deal with all the dependencies, removing 5.0 before installing 5.1 for example.

PS:
Don't forget Linux is case sensitive; there is no such package as VirtualBox, only virtualbox.

---

### Post by capharol on 2016-11-17
> **ian-weisser said:**
> 
Be aware that "sudo dpkg --remove --force-remove-reinstreq" is rather a nuclear solution, and may leave fallout scattered across your system that must be cleaned up manually. Time will tell.

I have read about that but I thought it was my last way toget it removed :frown: after 2 days struggling to uninstall a programm. 

>  [COLOR=#000000]Keep regular backups of your data - [/COLOR]
will think about it.

> [COLOR=#000000]you made a couple classic Windows-power-user mistakes[/COLOR]
was my thought aswell :lolflag:

> **ajgreeny said:**
> [COLOR=#000000]First let's see what virtualbox packages you have installed using dpkg, then we can figure out how to remove them, if that is what you really want.[/COLOR]

thank you.... I'd run the command and this was the result

```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                               Version                Architecture           Description
+++-==================================-======================-======================-==========================================================================
rc  virtualbox                         5.0.24-dfsg-0ubuntu1.1 amd64                  x86 virtualization solution - base binaries
un  virtualbox-2.0                     <none>                 <none>                 (no description available)
un  virtualbox-2.1                     <none>                 <none>                 (no description available)
un  virtualbox-2.2                     <none>                 <none>                 (no description available)
un  virtualbox-3.0                     <none>                 <none>                 (no description available)
un  virtualbox-3.1                     <none>                 <none>                 (no description available)
un  virtualbox-3.2                     <none>                 <none>                 (no description available)
un  virtualbox-4.0                     <none>                 <none>                 (no description available)
un  virtualbox-4.1                     <none>                 <none>                 (no description available)
un  virtualbox-4.2                     <none>                 <none>                 (no description available)
un  virtualbox-4.3                     <none>                 <none>                 (no description available)
un  virtualbox-5.0                     <none>                 <none>                 (no description available)
rc  virtualbox-5.1                     5.1.8-111374~Ubuntu~xe amd64                  Oracle VM VirtualBox
ii  virtualbox-dkms                    5.0.24-dfsg-0ubuntu1.1 all                    x86 virtualization solution - kernel module sources for dkms
un  virtualbox-guest-additions-iso     <none>                 <none>                 (no description available)
un  virtualbox-guest-modules           <none>                 <none>                 (no description available)
un  virtualbox-modules                 <none>                 <none>                 (no description available)
un  virtualbox-ose                     <none>                 <none>                 (no description available)
rc  virtualbox-qt                      5.0.24-dfsg-0ubuntu1.1 amd64                  x86 virtualization solution - Qt based user interface
un  virtualbox-source                  <none>                 <none>                 (no description available)

```

> [COLOR=#000000]if you like to use a GUI package manager try synaptic[/COLOR]
I will look for it and install it....

sorry again but it's my real 1st time, I'm trying to read about Ubuntu, to learn, but it aint easy if your mind is set on Windows

edit screenshot:
[IMG][[IMG]http://fs5.directupload.net/images/161117/temp/2rb8as5g.png[/IMG]]("http://www.directupload.net/file/d/4542/2rb8as5g_png.htm")[/IMG]

---

### Post by ajgreeny on 2016-11-17
You have only **virtualbox-dkms-5.0.24** installed on your system at present and no virtualbox itself of any version, though you did have VBox-5.1 at one time but have now removed it.

Using synaptic if you like it, for ease, remove completely that **virtualbox-dkms** package then you can install the version of virtualbox that you want to try.
Incidentally I have never had the virtualbox-dkms package installed in my host system and never seen a reason to do so.  I do have dkms installed in the host to enable the various modules needed to be rebuilt when a new kernel version is installed to my host.

I am using 5.1 now with great success, having added the vbox repos to my software sources as shown at the page at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the **"Debian-based Linux distributions"** section.

---

### Post by capharol on 2016-11-18
> **ajgreeny said:**
> You have only **virtualbox-dkms-5.0.24** installed on your system at present and no virtualbox itself of any version, though you did have VBox-5.1 at one time but have now removed it.
i did had virtualbox installed but i deleted it yesterday, but not the -dmks

> I am using 5.1 now with great success, having added the vbox repos to my software sources as shown at the page at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the **"Debian-based Linux distributions"** section.

x386 or AMD64??
I only wanna to install genymotion, but this is a load of hustle for a androidemulator.

---

### Post by ajgreeny on 2016-11-18
> I only wanna to install genymotion, but this is a load of hustle for a androidemulator. 
I have no knowledge of either of those things so can't help with that, but as I said, you do not have virtualbox installed now, other than the remaining configuration for it which you can remove if you wish by using synaptic and choosing "Mark for complete removal".

I am not sure what more I can do for you regarding the virtualbox installation, as your original query seems to be solved.

If I'm wrong, ask a specific question about what exactly you are trying to do and your problems with genymotion.

---

### Post by capharol on 2016-11-18
> **ajgreeny said:**
> I am not sure what more I can do for you regarding the virtualbox installation, as your original query seems to be solved.
yes it is and i thank you for the help so far

> If I'm wrong, ask a specific question about what exactly you are trying to do and your problems with genymotion.
all i wanted was to install a androidemulator under Ubuntu,and was told genymotion was the best option, but in order to get genymotion to run you need VirtualBox, but as you said that is another Topic.

---

### Post by ajgreeny on 2016-11-18
Great! I am very happy you managed to solve that part of your problem, at least.  If you want more help on genymotion you will need to start a new thread.

Please mark this thread as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

