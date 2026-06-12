---
title: "Does Anbox work for anyone?"
date: 2022-04-12
forum: General Help
---

### Post by pc-cobbler on 2022-04-12
I tried Anbox with 20 LTS MATE, but it would always die after showing the start screen. I just built a 22.04 LTS beta MATE system and had the same result. Has anyone been able to use Anbox?

---

### Post by TheFu on 2022-04-12
I haven't tried after failing a few years ago.

Found a tool that connects to android devices over USB and shows the screen on my Linux desktop. Besides the sound coming from the tablet/phone, everything else happens through the computer. Can even create videos while used.  The tool worked, until it was repackaged as a snap, then it never worked again, I'm sad to say.  There are a number of those tools, but my interest waned. I was just using it to have a larger screen for a few games that my old eyes just couldn't see clearly on smaller screens.

---

### Post by pc-cobbler on 2022-04-13
I am responding to private messages here, as I think others may be interested.

I waited 25 minutes before starting anbox, as this system has a slow drive (I did an update in the interim, as this is 22 beta). The popup with the robot appeared for a minute or so and then disappeared. I executed "anbox session-manager" in a terminal, with the following result: "[ 2022-04-13 22:16:16] [session_manager.cpp:149@operator()] Failed to start as either binder or ashmem kernel drivers are not loaded."

I searched for "ashmem" via Synaptic, but the only result was android-androresolvd, which is not installed. Searching for "binder" returns many entries, as one would expect.

@TheFu: Your eyes were ever good enough to play games on a smartphone? I never understood how people used smartphones to see anything other than texts and maybe a weather report.

---

### Post by TheFu on 2022-04-13
I had little trouble reading anything for many decades.  
Smartphones didn't exist. 
Cell phones didn't exist.  
We played Coleco head-to-head red-LED games as a kids. [https://www.handheldmuseum.com/Coleco/H2HFootball.htm](https://www.handheldmuseum.com/Coleco/H2HFootball.htm)
I got a cellular email device in 1999 - a RIM 950 ipgr.  Everything after that has been less great and corrupted the world. The ipgrs were communications devices and information request devices. It was amazing what we could do on those without any advertising or being tracked.  I could find the local UPS store, track packages, get a sbux location, AND email my wife, friends, coworkers all on that amazing little device.

Some games work fine on a 6in screen.  My favorite game is a little busy for that when you reach expert levels.  I'm trying to land about 45 aircraft on 5 different runways concurrently.  That's a bunch of situational awareness to pack into a 6in screen.  But when connected to a 24inch monitor (using about 40% of it), it is possible to see everything, if I wear my reading glasses.  I've only needed reading glasses for about 5 yrs. I wear contact lenses too ... without contacts in, I don't need reading glasses, but I'm likely to trip and fall down the stairs due to poor eyesight for anything over 2ft away.

My choice of career didn't exactly help with eyesight. I was a professional software developer for 15 yrs before moving in to systems and enterprise architecture. That's mostly creating design documents and sitting on conferences 8+ hrs a day - back to back.  Working 20 concurrent projects leads to far too many meetings, with little time left over for actually creating new designs which are used to feed into the next project.  Staring at computer screens all day, especially the old IBM 327x terminals, isn't good for anyone.

---

### Post by deadflowr on 2022-04-14
> I searched for "ashmem" via Synaptic, but the only result was android-androresolvd, which is not installed. Searching for "binder" returns many entries, as one would expect.
ashmem and binder are kernel modules.
try
```
sudo modprobe ashmem_linux
sudo modprobe binder_linux
```
Might also check to see if this causes issues: [https://askubuntu.com/questions/1267823/module-ashmem-doesnt-load-with-secure-boot-on-but-binder-does-load-with-se]("https://askubuntu.com/questions/1267823/module-ashmem-doesnt-load-with-secure-boot-on-but-binder-does-load-with-se")

---

### Post by pc-cobbler on 2022-04-19
@deadflowr

I executed both modprobe lines and rebooted, but it made no difference.

---

### Post by btindie on 2022-04-20
If you reboot, they then won't be loaded. modprobe just loads them into memory temporarily.
Take a look at the install docs [https://docs.anbox.io/userguide/install.html#install-kernel-modules](https://docs.anbox.io/userguide/install.html#install-kernel-modules) it explains how to install the kernel modules!

---

### Post by pc-cobbler on 2022-04-20
@btindie

Um, no.

> 
~$ snap install --devmode --beta anbox
anbox (beta) 4-56c25f1 from Simon Fels (morphis) installed

~$ sudo add-apt-repository ppa:morphis/anbox-support
[sudo] password for userr: 
Repository: 'deb [https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu/](https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu/) jammy main'
More info: [https://launchpad.net/~morphis/+archive/ubuntu/anbox-support](https://launchpad.net/~morphis/+archive/ubuntu/anbox-support)
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/morphis-ubuntu-anbox-support-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/morphis-ubuntu-anbox-support-jammy.list
Adding key to /etc/apt/trusted.gpg.d/morphis-ubuntu-anbox-support.gpg with fingerprint CFD4CCDE77B82D4FA3B113E521C6044A875B67B7
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease [270 kB]
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease               
Ign:3 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable InRelease                     
Hit:4 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable Release                       
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease              
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease            
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages [13.6 MB]
Ign:9 [https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu](https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu) jammy InRelease
Err:10 [https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu](https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu) jammy Release
  404  Not Found [IP: 91.189.95.85 443]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe i386 Packages [7,491 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe Translation-en [5,651 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 c-n-f Metadata [286 kB]
Reading package lists... Done                                                  
E: The repository 'https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease              
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease            
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease               
Ign:5 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable InRelease                     
Hit:6 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable Release                       
Ign:7 [https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu](https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu) jammy InRelease
Err:9 [https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu](https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu) jammy Release
  404  Not Found [IP: 91.189.95.85 443]
Reading package lists... Done                            
E: The repository 'https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

~$ sudo apt install linux-headers-generic anbox-modules-dkms
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package anbox-modules-dkms

~$ sudo modprobe ashmem_linux
~$ sudo modprobe binder_linux

~$ ls -1 /dev/{ashmem,binder}
ls: cannot access '/dev/binder': No such file or directory
/dev/ashmem


---

### Post by grahammechanical on 2022-04-20
It works for me. I followed the instruction in that Anbox document page. The window with the Android icon and the word "starting" appears. That is followed by the Android Application Manager window with a selection of Android apps available.

Regards

---

### Post by pc-cobbler on 2022-04-21
The webpage at [https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu/dists/](https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu/dists/) illustrates the problem. There is no Jammy release, with all content being from 2018.

@grahammechanical   How old is the Ubuntu you are running?

---

### Post by Holger_Gehrke on 2022-04-21
If you had followed the link "Install Kernel Modules" in the anbox documentation page btindie linked to you would have found that starting with Ubuntu 19.04 the modules are part of the standard kernel if you're using a kernel version 5.0 or greater. That's why there are no modules for anything past Ubuntu 18.04 in the PPA. So all you have to do is load these modules with 'modprobe ashmem_linux;modprobe binder' and start anbox. I had it working a few years ago (IIRC it was not a snap back then ...) but found it basically too slow to be usable for any use case except debugging your own apps.

Holger

---

### Post by pc-cobbler on 2022-04-22
With respect to my last comment, I can now safely say that Anbox does not work with Jammy Jellyfish and likely does not work with Focal Fossa.

I took a faster USB flash drive (the other system was built on a USB flash drive) and installed Bionic Beaver. I was able to follow the instructions and get Anbox to install and start.

Now hopefully I can figure out how to obtain APK packages for the apps I want.

---

### Post by luisx10 on 2023-03-29
> **TheFu said:**
> 
Found a tool that connects to android devices over USB and shows the screen on my Linux desktop. Besides the sound coming from the tablet/phone, everything else happens through the computer. Can even create videos while used.
ScrCpy [https://github.com/Genymobile/scrcpy](https://github.com/Genymobile/scrcpy) does that and is easier to install or build, I havent already tried the latest version, wireless connection was amazing for me I'm excited to see what feature they added like audio (I can't use it, old phone) and camera, upgrading right now from 1.22 to 2.0
Anyway back to the OP question, I read in the Anbox repo that Waydroid works without ashmem and there isn't any intent of continue with the development of the first.

---

### Post by silas33 on 2023-04-21
> **pc-cobbler said:**
> I tried Anbox with 20 LTS MATE, but it would always die after showing the start screen. I just built a 22.04 LTS beta MATE system and had the same result. Has anyone been able to use Anbox?

To answer your question, yes, there are many people who have been able to use Anbox successfully on their Linux systems. However, it requires a compatible system configuration and proper installation.


You can try troubleshooting the issue by checking the system requirements for Anbox and ensuring that your system meets them. You can also try reinstalling Anbox or checking for any updates or patches that may have been released to address compatibility issues. Additionally, you can try reaching out to the Anbox community or support team for further assistance.

---

