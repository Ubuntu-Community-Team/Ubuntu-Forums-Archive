---
title: "Repository Messed Up?"
date: 2012-11-19
forum: General Help
---

### Post by TheAfroSoldier on 2012-11-19
First off, sorry for any bad grammar/spelling! Second, I've been having trouble with my ubuntu repository lately... It won't let me install or uninstall any program at all... It provides the message.

> Items can not be installed or removed until the package catalog is repaired. Do you want to repair it now?I click yes and it gives me another error.

> **Package operation failed.** The installation or removal of a software package failed.It has the output/details as. 

> installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 243148 files and directories currently installed.) 
Unpacking visualboyadvance (from .../visualboyadvance_1.8.0.dfsg-0.1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/visualboyadvance_1.8.0.dfsg-0.1_i386.deb (--unpack): 
 trying to overwrite '/etc/VisualBoyAdvance.cfg', which is also in package vbam 0.svn451-1 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/visualboyadvance_1.8.0.dfsg-0.1_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of visualboyadvance-gtk: 
 visualboyadvance-gtk depends on visualboyadvance (= 1.8.0.dfsg-0.1); however: 
  Package visualboyadvance is not installed. 
dpkg: error processing visualboyadvance-gtk (--configure): 
 dependency problems - leaving unconfigured Please help, I've searched this form before and tried using them but they didn't help. This all started after trying to install VisualBoy Advance. Also to note, there is a circle in my bar at the top of the screen with a white line going through it. When I click on it, it takes me to the updater which fails and gives me this. 

>  The following packages have unmet dependencies:

visualboyadvance-gtk: Depends: libatkmm-1.6-1 (>= 2.22.0) but 2.22.6-1ubuntu1 is installed
                      Depends: libc6 (>= 2.4) but 2.15-0ubuntu10.3 is installed
                      Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
                      Depends: libglademm-2.4-1c2a (>= 2.6.0) but 2.6.7-2build1 is installed
                      Depends: libglib2.0-0 (>= 2.16.0) but 2.32.3-0ubuntu1 is installed
                      Depends: libglibmm-2.4-1c2a (>= 2.27.3) but 2.32.0-0ubuntu1 is installed
                      Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.10-0ubuntu6 is installed
                      Depends: libgtkmm-2.4-1c2a (>= 1:2.22.0) but 1:2.24.2-1ubuntu1 is installed
                      Depends: libsigc++-2.0-0c2a (>= 2.0.2) but 2.2.10-0ubuntu2 is installed
                      Depends: libstdc++6 (>= 4.5) but 4.6.3-1ubuntu5 is installed
                      Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
                      Depends: visualboyadvance (= 1.8.0.dfsg-0.1) but it is not installed
Again, this is a great forum and it's been a real help since I started using ubuntu. Thank you all for the help ahead of time. <3

---

### Post by Kirk Schnable on 2012-11-20
Broken dependencies like this tend to be a pain. In my experience, these steps should put your dpkg/apt back in working order.

```
sudo apt-get remove visualboyadvance visualboyadvance-gtk --purge 
```

```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

```
sudo apt-get update
```

Once we determine that your package manager is up and running again, we can take a crack at your dependency resolution issue.

Cheers
Kirk

---

### Post by TheAfroSoldier on 2012-11-20
Thanks! Everything seems to be working great now. May I ask you two-three questions though?

1. If I where to ever have this problem again, but with a different software, could I replace the "visualboyadvance" with said software?

2. Where did you get so good at linux code?

3. Where can I get good at this? lol

---

### Post by Kirk Schnable on 2012-11-20
> **TheAfroSoldier said:**
> Thanks! Everything seems to be working great now. May I ask you two-three questions though?

1. If I where to ever have this problem again, but with a different software, could I replace the "visualboyadvance" with said software?
Yeah, basically. You kind of have to play it by ear when apt/dpkg gets messed up. 

> **TheAfroSoldier said:**
> 2. Where did you get so good at linux code?

3. Where can I get good at this? lol
I am a Linux tech for a high school, and I have been using Ubuntu regularly for years. I use it on my personal desktops, laptop, and servers. I also have to frequently fix package issues at my work due to computers being improperly shut down during the updates we do in the background. I've become quite adept at fixing simple apt issues, even to the point where I've written automated scripts that run in the background to preemptively fix a screwed package manager on our machines. 

The best way to become good at it is to keep using it and keep asking questions!

Cheers
Kirk

---

