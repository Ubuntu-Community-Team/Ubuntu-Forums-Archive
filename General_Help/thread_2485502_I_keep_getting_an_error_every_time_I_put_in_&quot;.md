---
title: "I keep getting an error every time I put in &quot;sudo apt update!&quot;"
date: 2023-03-31
forum: General Help
---

### Post by jayjillaofficial on 2023-03-31
here's what it gives me, after I hit enter:

```
root@community-ThinkPad-T430:/home/community# sudo update
sudo: update: command not found
root@community-ThinkPad-T430:/home/community# sudo apt-get update
Hit:1 [https://dl.winehq.org/wine-builds/debian](https://dl.winehq.org/wine-builds/debian) bullseye InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease
Ign:6 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease
Err:8 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done
E: The repository '[https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
I am using Ubuntu 22.04 LTS with a 1 TB hard drive on a Thinkpad T430 Lenovo, if that matters for extra info.

---

### Post by tea for one on 2023-03-31
> **jayjillaofficial said:**
> E: The repository '[https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy Release' [COLOR="#FF0000"]_does not have a Release file_[/COLOR].
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
Remove the repo above because there is no software package to download for 22.04.
```
root@community-ThinkPad-T430:/home/community# sudo apt-get update
```
Using root in this way should be discouraged.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Holger_Gehrke on 2023-03-31
The PPA you've got in there doesn't have packages for Ubuntu 22.04. The last Ubuntu release for which it offers packages is 20.04. You should disable or remove it.

Holger

---

### Post by jayjillaofficial on 2023-03-31
How do I remove it? I'm very new to this please. && How do I arrange the root path? Thank guys

---

### Post by jayjillaofficial on 2023-03-31
Oh I see lol I have to click on the link first.

---

### Post by tea for one on 2023-03-31
> **jayjillaofficial said:**
> How do I remove it? 
Here is some light bed-time reading:-
[https://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/](https://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/)

---

### Post by jayjillaofficial on 2023-03-31
Thank you! I'll check it out and get back to you.

---

### Post by DuckHook on 2023-03-31
As a self&#8209;described new user, you really should not be adding any PPAs at all to your installs.

The biggest mistake that new users make when coming to Ubuntu is to install all sorts of nonessential customizations by adding PPAs, outside repos and even standalone apps. These will almost invariably lead to trouble. Even when they work, it's a bad habit that just reinforces poor computer hygiene.

The PPA that you have installed is a one&#8209;man show that hasn't been touched by its owner in two&#8209;and&#8209;a&#8209;half years. That's a long time for a developer to have let his PPA slide. How can you be sure that it's not full of bugs or malware?

What is it that you are trying to install? More importantly, why?

---

### Post by MAFoElffen on 2023-03-31
How to remove a PPA, command line
```

sudo add-apt-repository --remove ppa:gezakovacs/ppa

```
That was the PPA for unetbootin... Which even the GitHub for it has also not had a commit in over 2 years either. As DuckHook noted for this PPA.

If, what you are trying to do is have a utility to create Bootable USB's: 
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by jayjillaofficial on 2023-03-31
Yes and I was trying to install wine so I can diagnose my laptop... I screwed up the bios. So now I'm trying to update it and repair or restore the core system to this Thinkpad T430.

---

### Post by jayjillaofficial on 2023-03-31
Yeah I was trying install wine so that I am able to download ISO's and windows compatible files to restore my Lenovo Thinkpad T430. There are some erors showing up as well when starting the system up.
I've been reading and being careful. i've dealt with linux mint and debian systems for more then 2 years teaching my self and read forums. So I try to be careful while in the terminal.

---

### Post by jayjillaofficial on 2023-03-31
Well guy I guess that solved the PPA error thank you. But is this supposed to look like this?


community@community-ThinkPad-T430:~$ sudo bash
[sudo] password for community: 
root@community-ThinkPad-T430:/home/community# sudo apt-get update
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                      
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                         
Hit:3 [https://dl.winehq.org/wine-builds/debian](https://dl.winehq.org/wine-builds/debian) bullseye InRelease    
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB]
Fetched 336 kB in 3s (114 kB/s)    
Reading package lists... Done
root@community-ThinkPad-T430:/home/community#

PS.
What is "sudo apt-get upgrade" supposed to do? and is it okay to run?

Also how do I get rid of the typing curser everywhere I click. I sometime notice a type curser blinking on icons after I click on them... I'm thinking about re installing the OS.

---

### Post by deadflowr on 2023-04-01
> What is "sudo apt-get upgrade" supposed to do? and is it okay to run?
apt-get update is a refresh utility. It checks the repositories you have listed in your source file(s) for any packages which have updated versions.
apt-get upgrade is what actually downloads and installs the updates.
You run both in tandem.

---

### Post by monkeybrain20122 on 2023-04-01
If you are a new user you should get synaptic, which gives you a nice gui to browse, search for, install, remove and upgrade packages (it has a lot more features and options than the software store but only for .deb packages) To use the  sudo apt mumbo jumbo you have to know the exact package name and what they are for in order to install something.

---

### Post by MAFoElffen on 2023-04-01
Curious about this:
```

Hit:3 https://dl.winehq.org/wine-builds/debian bullseye InRelease

```
Debian Bullseye?

Why did you not install wine from the Ubuntu repo's? And if straight from WineHQ, then why not to their Ubuntu focal repo's?

---

### Post by ajgreeny on 2023-04-01
> **jayjillaofficial said:**
> here's what it gives me, after I hit enter:

```
root@community-ThinkPad-T430:/home/community# sudo update
sudo: update: command not found
root@community-ThinkPad-T430:/home/community# sudo apt-get update
Hit:1 [https://dl.winehq.org/wine-builds/debian](https://dl.winehq.org/wine-builds/debian) bullseye InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease
Ign:6 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease
Err:8 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done
E: The repository '[https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
[COLOR="#FF0000"]I am using Ubuntu 22.04 LTS[/COLOR] with a 1 TB hard drive on a Thinkpad T430 Lenovo, if that matters for extra info.

Sorry, but you appear not to be using 22.04, Jammy but 20.04, Focal.

You seem to have a bit a mixture or have made a mess of your sources which really need to be put right before we can tell you exactly how best to proceed from here.

---

### Post by tea for one on 2023-04-01
> **jayjillaofficial said:**
> 
```
community@community-ThinkPad-T430:~$ [COLOR="#FF0000"]sudo bash[/COLOR][COLOR="#0000FF"] < Why?[/COLOR]
[sudo] password for community: 
root@community-ThinkPad-T430:/home/community# sudo apt-get update
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                      
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                         
Hit:3 [https://dl.winehq.org/wine-builds/debian](https://dl.winehq.org/wine-builds/debian) bullseye InRelease    
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB]
Fetched 336 kB in 3s (114 kB/s)    
Reading package lists... Done
root@community-ThinkPad-T430:/home/community#
```
Why have you started this terminal session with sudo bash?
You are running as root and it should be avoided unless you are very comfortable with the potential destructive consequences.

After you log in to Ubuntu, open a terminal and enter:-
```
sudo apt update
```
You will be asked for your password to allow elevated privileges i.e. install software.
> I'm thinking about re installing the OS.
Don't forget to back up your data if you decide to do this.

---

### Post by jayjillaofficial on 2023-04-01
Thanks man for info[


> **deadflowr said:**
> apt-get update is a refresh utility. It checks the repositories you have listed in your source file(s) for any packages which have updated versions.
apt-get upgrade is what actually downloads and installs the updates.
You run both in tandem.

---

### Post by TheFu on 2023-04-03
> **jayjillaofficial said:**
> Thanks man for info[

All the command line tools have manpages, which are installed onto your computer.
For apt, these paragraphs explain:
```
       update (apt-get(8))
           update is used to download package information from all configured
           sources. Other commands operate on this data to e.g. perform
           package upgrades or search in and display details about all
           packages available for installation.

       upgrade (apt-get(8))
           upgrade is used to install available upgrades of all packages
           currently installed on the system from the sources configured via
           sources.list(5). New packages will be installed if required to
           satisfy dependencies, but existing packages will never be removed.
           If an upgrade for a package requires the removal of an installed
           package the upgrade for this package isn't performed.
```

Theere are many more pages of options documented in there. Learning how to read a manpage is very useful.
If you want a GUI for reading manpages, check out **xman**.  Click on some buttons. Look around. There are hundreds (if not more) commands documented.

---

