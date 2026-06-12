---
title: "Running Ubuntu But Now Lubuntu Seems to be Causing Mischief"
date: 2015-11-16
forum: General Help
---

### Post by Plumtreed on 2015-11-16
I am running Ubuntu 14.04 and decided to try Lubuntu on an 'older' Laptop. To this end I downloaded the Lubuntu ISO on my main and faster desktop and intended to make a dvd in order to install to the laptop. However, since downloading Lubuntu and trying it out on Virtualbox on my Ubuntu machine, Lubuntu has intruded into the startup and shut down process of Ubuntu.......instead of a Ubuntu background I get a blue Lubuntu background and Lubuntu logo.

Anybody know why I got stuck with this messy business?

---

### Post by sudodus on 2015-11-16
I have never heard before, that testing Lubuntu or any other Ubuntu flavour in Virtualbox has messed with the host operating system.

-o-

Your problems looks like you have installed the Lubuntu desktop into your Ubuntu system with the following command

```
sudo apt-get install lubuntu-desktop
```

or a similar action via some graphical user interface.

I'm sorry, but once you have mixed up the desktop environments, it is very difficult to return to a clean one. You can try, but there is a great risk that the system will be damaged. On the other hand, it is possible to live with a mixed up desktop environment, several people do that on purpose. I do it because I want the light lubuntu desktop (LXLE) to play high definition video, and I want the other desktop environment for other purposes.

But it might be cleaner to only install the desktop environment, so for example

```
sudo apt-get install lxde
```

or maybe (to mess with the desktop environment, but not install doublets of application programs)

```
sudo apt-get install lubuntu-core
```

and instead of

```
sudo apt-get install xubuntu-desktop
```

you could install

```
sudo apt-get install xfce4
```

-o-

In computers, that are getting older, I have found it useful to install ***Xubuntu*** and into that install Lubuntu Core

```
sudo apt-get install lubuntu-core
```

---

### Post by Sweet_Baby_Jamie on 2015-11-16
>  In computers that are getting older, I have found it useful to install ***Xubuntu*** and into that install Lubuntu Core. 

Fascinating!  Would you then select an LXDE session at login when booting up Xubuntu?

---

### Post by Plumtreed on 2015-11-16
Didn't do any of the things you mention....just wanted to try Lubuntu...kindasorry I bothered now but I guess I can live with what I have. That is not the point tho, when things like this happen in Ubuntu it is very disappointing!

---

### Post by sudodus on 2015-11-16
> **Sweet_Baby_Jamie said:**
> Fascinating!  Would you then select an LXDE session at login when booting up Xubuntu?

Yes :-)

---

### Post by sudodus on 2015-11-16
> **Plumtreed said:**
> Didn't do any of the things you mention....just wanted to try Lubuntu...kindasorry I bothered now but I guess I can live with what I have. That is not the point tho, when things like this happen in Ubuntu it is very disappointing!

I'm sorry, but I have no other explanation. I hope that someone with more experience of VirtualBox reads this and can help you better.

---

### Post by ajgreeny on 2015-11-16
I use VBox a lot.
I have six OSs available which I can run in that, and like sudodus, I have never heard of something like this happening; in fact I think it is impossible that installing something in VBox could ever affect the host machine, as the guest is completely separate from host.

@ Plumtreed
You may be able to remove some of the packages that were added and are now related to this by using command
```
grep -iw install /var/log/dpkg.log.1 /var/log/dpkg.log
``` This will list all newly installed packages, and by looking at the date and time of any lubuntu named packages, and relating that to the point when this problem started, you may be able to figure out what has happened and remove some of them.

I suggest you install synaptic package manager to do this, if you don't already use it, as it is much better than the software-centre and gives you a lot more information when installing anything in your system.

Are you 100% sure you downloaded the iso file of Lubuntu, and did not download and install the lubuntu.desktop package at some time?  I can see no other way for your current installed OS to have suddenly changed to using lubuntu artwork etc etc.

---

### Post by Plumtreed on 2015-11-16
I have a few things set up in vbox but primarily for testing.....I don't use it in any other way. I have never had any 'crossover' problems before.
I will follow your suggestion AJGreeny as a matter of interest but can assure you that the problem I have explained is a fact........other than running Lubuntu on Vbox I burnt a DVD and have the Lubuntu ISO in my Download file.

---

### Post by vasa1 on 2015-11-16
> **Plumtreed said:**
> Didn't do any of the things you mention....just wanted to try Lubuntu...kindasorry I bothered now but I guess I can live with what I have. That is not the point tho, when things like this happen in Ubuntu it is very disappointing!Well, I sympathize with you. What you have seen isn't uncommon. The latest desktop environment can alter the grub, login and possibly the logout screens. Many of us here now don't recommend mixing desktop environments for various reasons, not just the one you've described.

---

### Post by ajgreeny on 2015-11-16
> **vasa1 said:**
> Well, I sympathize with you. What you have seen isn't uncommon. The latest desktop environment can alter the grub, login and possibly the logout screens. Many of us here now don't recommend mixing desktop environments for various reasons, not just the one you've described.
Including me!
But the OP insists that he has not, and did not, mix DEs on his computer, so we are still left trying to figure out where those lubuntu packages came from that appear to have taken over the artwork on the system.

With a bit of luck we may get some clues from my suggested command to grep the dpkg.log files

---

### Post by vasa1 on 2015-11-16
> **ajgreeny said:**
> Including me!
But the OP insists that he has not, and did not, mix DEs on his computer, so we are still left trying to figure out where those lubuntu packages came from that appear to have taken over the artwork on the system.

With a bit of luck we may get some clues from my suggested command to grep the dpkg.log filesYes, there is some ambiguity about what exactly OP did.

---

### Post by SantaFe on 2015-11-16
Might be the Plymouth theme's been changed.  Might try what's shown here: [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html) and look for the Ubuntu Plymouth splash screen entry & pick it & reboot.

---

### Post by Plumtreed on 2015-11-16
Following up on AJGreeny's suggestion....indicates a lot of extras were installed to existing including things more associated with Lubuntu, such as, Abiword?, Lubuntu Core and others.

Looking back into memory, I was experiencing problems related to warnings cropping up saying there were problems, not specific, and they should 'be reported'! Also some warnings about 'update info being outdated' and suggestions how to sort them. A recommendation appeared suggesting a solution might be to run....sudo apt-get install -f.

Whatever happened results in a Hybrid ubuntu/lubuntu system which, while looking strange, seems to work satisfactorily.

---

### Post by Vladlenin5000 on 2015-11-16
> **Plumtreed said:**
> indicates a lot of extras were installed to existing including things more associated with Lubuntu, such as, Abiword?, Lubuntu Core and others.

So the original contention still stands: This couldn't have happened in Virtualbox.

Somehow you managed to install something on top of your Ubuntu. Surely I'm not the only one curious about what you did exactly. Can you please describe what you did?
Meanwhile, please do NOT blame Virtualbox.

---

### Post by Plumtreed on 2015-11-16
No, It difficult to think that Virtualbox could have had anything to do with it!

From memory, I downloaded Lubuntu, ran it in VBox and then used K3B to burn a DVD for install on the other machine. 

Not necessarily related to lubuntu, because it had happened previously, my 'desktop' suggested there was a problem and even suggested running 'sudo apt-get install -f, which I did.

....I don't recall doing anything more adventurous than that.

---

### Post by vasa1 on 2015-11-16
> **Vladlenin5000 said:**
> ...
Meanwhile, please do NOT blame Virtualbox.
The title seems to imply that Lubuntu is at fault :)
Given the lack of clarity, I suggest that OP use the Report button to ask that this thread be closed. OP could start a new thread in which specific information is provided to help others understand what exactly is being done.

---

### Post by Plumtreed on 2015-11-16
> **vasa1 said:**
> The title seems to imply that Lubuntu is at fault :)
Given the lack of clarity, I suggest that OP use the Report button to ask that this thread be closed. OP could start a new thread in which specific information is provided to help others understand what exactly is being done.

Not much interested in closing this thread........and there is little more I can add....I have indicated a problem that developed. Lubuntu has clearly become superimposed on my Ubuntu software. Mainly manifested by the lubuntu logo and blue screen showing on start up and shut down whereas normally one would get the Ubuntu Logo and maroon colour.

Ambiguous it is not! The situation is abundantly clear..............I did nothing but follow a process that I have been doing for years with many and varied other operating systems! This time when I tried Lubuntu it somehow intruded into my Ubuntu OS.

---

### Post by Vladlenin5000 on 2015-11-17
> **Plumtreed said:**
> I did nothing but follow a process that I have been doing for years with many and varied other operating systems!

Is the process something along this lines?
Create a new VM (defining the OS type, drive, etc.), add the Lubuntu ISO as a virtual CD drive, then start the VM and install as usual?

---

### Post by Plumtreed on 2015-11-17
> **Vladlenin5000 said:**
> Is the process something along this lines?
Create a new VM (defining the OS type, drive, etc.), add the Lubuntu ISO as a virtual CD drive, then start the VM and install as usual?

I downloaded Lubuntu 14.04, did a md5sum check and then created a session on VirtualBox named Lubuntu. I set type to Linux and version to Other Linux (32bit).
I probably set the Memory size @ 512MB and Hard Drive to only a bit less than 8GB.
Storage to  IDE  PIIX4 and selected the VDI file.............I didn't do an install just ran live.

It works and runs as it should so I decided to burn DVD and install it on a different machine as planned. Did that and it all went as it should.

Next time I booted the original machine the Lubuntu logo appeared and so on.

---

### Post by Vladlenin5000 on 2015-11-18
> *Once you eliminate the impossible, whatever remains, no matter how improbable, must be the truth.*

Arthur Conan Doyle

Considering:
1. Doing as you did couldn't possibly have installed Lubuntu specific packages in the host system;
2. You're sure you didn't do it yourself...

Then _someone else_ did. The dates/timestamps in the log should give you a clue.

---

### Post by Plumtreed on 2015-11-18
I appreciate your interest but because everything seems to be running smoothly i will just use my 'new' Ubuntu/Lubuntu as it is. I will probably reinstall at the next LTS release to make my OS pure Ubuntu. I have been updating Ubuntu since 7.10 so it may be time to refresh things.

I can assure you that I did nothing intentionally to provoke the outcome I have described. Thanks and I hope we meet again!

---

### Post by ajgreeny on 2015-11-18
> **Plumtreed said:**
> I appreciate your interest but because everything seems to be running smoothly i will just use my 'new' Ubuntu/Lubuntu as it is. I will probably reinstall at the next LTS release to make my OS pure Ubuntu. I have been updating Ubuntu since 7.10 so it may be time to refresh things.

I can assure you that I did nothing intentionally to provoke the outcome I have described. Thanks and I hope we meet again!
Fair enough, but to satisfy your curiosity, and mine, can you run command ```
sudo apt-get -s remove lubuntu*
``` which will not do anything at all but just simulate removal of any package named lubuntu-*something* and list what would have been removed without the -s (simulate) switch option.

I really am curious as to what went on here.

---

### Post by Plumtreed on 2015-11-18
This doesn't seem to be much help..........but I still see Lubuntu at boot up and shut down.

E: Unable to locate package lubuntuAddons

---

### Post by Plumtreed on 2015-11-18
Attached is a 'photo' of what appears

 [ATTACH=CONFIG]265669[/ATTACH]

on what is a basic Ubuntu Install

[ATTACH=CONFIG]265670[/ATTACH]

---

### Post by Bucky Ball on 2015-11-19
> **Plumtreed said:**
> I appreciate your interest but because everything seems to be running smoothly i will just use my 'new' Ubuntu/Lubuntu as it is. I will probably reinstall at the next LTS release to make my OS pure Ubuntu. I have been updating Ubuntu since 7.10 so it may be time to refresh things.

In that case, could you please mark this thread as solved to help others. See first link in my signature. This will not close the thread to further discussion but will save others some time and effort. Thanks and good luck. :)

PS: Please run the command ajgreeny has asked you to and post the output here between code tags (last link in my signature). Thanks.

---

### Post by Plumtreed on 2015-11-19
> **Plumtreed said:**
> This doesn't seem to be much help..........but I still see Lubuntu at boot up and shut down.

E: Unable to locate package lubuntuAddons

The result is posted here

This is hardly 'Solved' and I will mark it as solved once AJGreeny has exhausted his interest in locating the problem;)

---

### Post by vasa1 on 2015-11-19
At this point my only interest in this thread is in seeing how the "Lubuntu Seems to be Causing Mischief" in the title is justified. If it can't be shown that "Lubuntu Seems to be Causing Mischief", I suggest that the title of this thread should be edited accordingly.

From [Ubuntu Forums Rules]("http://ubuntuforums.org/misc.php?do=showrules") > Attacks and **derogatory terms** of any kind are not welcome. This includes references to **any operating systems** or the companies that produce them.

---

### Post by Bucky Ball on 2015-11-19
As you stated

> **Plumtreed said:**
> I appreciate your interest but because everything seems to be running smoothly i will just use my 'new' Ubuntu/Lubuntu as it is.

... it looked like you were satisfied with the situation and had reached a satisfactory resolution (unfortunately we only have a 'solved' option).

Marking it as solved doesn't preclude ajgreeny or anyone else from continuing to post on the thread and exploring what they wish with you, but it does help others looking for a fix and saves potential helpers time as you seem to have reached a satisfactory resolution.

Either way, no big deal, up to you. Good luck.

---

### Post by ajgreeny on 2015-11-19
> **Plumtreed said:**
> The result is posted here

This is hardly 'Solved' and I will mark it as solved once AJGreeny has exhausted his interest in locating the problem;)
Unfortunately the result is not yet posted, so I can't tell you anything more.

It is just my curiosity, as I said, and if you are happy to continue using your system as it is, that is OK.  That command will just show you any packages with "lubuntu" in their name that have been installed in the past, and whilst it may still not solve the mystery of who installed them, it will at least prove that some were installed at some point.

---

### Post by Plumtreed on 2015-11-19
When I entered the code this is what was returned.................E: Unable to locate package lubuntuAddons..............which adds nothing to the discussion or seems to suggest that none were installed.

I'm going to pull my head in because my observations, which evidence some mild defect in Ubuntu/Lubuntu, have been met with some consternation and derision. I'm not interested in that sort of stuff.

---

### Post by ajgreeny on 2015-11-19
> **Plumtreed said:**
> When I entered the code this is what was returned.................E: Unable to locate package lubuntuAddons..............which adds nothing to the discussion or seems to suggest that none were installed.

I'm going to pull my head in because my observations, which evidence some mild defect in Ubuntu/Lubuntu, have been met with some consternation and derision. I'm not interested in that sort of stuff.
That's because there is no such package as lubuntuAddons, and I'm not sure where you got that *lubuntuAddons* package suggestion from as I suggested you run command ```
sudo apt-get -s remove lubuntu*
```
Incidentally I do not think that anyone is meeting your comments with derision; we are simply trying to figure out what has happened here, but so far have been unable to see where it was that those lubuntu packages were installed, as they must have been at some time, or they would not be there.

However, if your machine is still running everything as you want except for the splash screen, and you are happy to leave it as is, no-one is forcing you to do anything else;  I, for one, just do not like a situation such as this that is left hanging with no answer when I know there must be an answer available if we could only get the information needed.

---

### Post by Plumtreed on 2015-11-19
When I run the command you suggested that was the response

plumtreed@plumtreed-lennie-M58:~$ sudo apt-get -s remove lubuntu*
[sudo] password for plumtreed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lubuntuAddons
plumtreed@plumtreed-lennie-M58:~$

I am happy to explore the problem as long as you feed me the questions.......I found I now have Lubuntu Software Centre installed as well as Ubuntu Software Centre......I have not installed Lubuntu Software Centre.

---

### Post by Plumtreed on 2015-11-20
I renamed files/folders starting with Lubuntu and re-ran the code suggested

```
plumtreed@plumtreed-lennie-M58:~$ sudo apt-get -s remove lubuntu* 
[sudo] password for plumtreed: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Note, selecting 'lubuntu-software-center' for regex 'lubuntu*' 
Note, selecting 'lubuntu-restricted-extras' for regex 'lubuntu*' 
Note, selecting 'ubiquity-slideshow-lubuntu' for regex 'lubuntu*' 
Note, selecting 'lubuntu-nexus7-default-session' for regex 'lubuntu*' 
Note, selecting 'lubuntu-nexus7-extra-files' for regex 'lubuntu*' 
Note, selecting 'lubuntu-extra-sessions' for regex 'lubuntu*' 
Note, selecting 'blubuntu-theme' for regex 'lubuntu*' 
Note, selecting 'lubuntu-default-settings' for regex 'lubuntu*' 
Note, selecting 'plymouth-theme-lubuntu-logo' for regex 'lubuntu*' 
Note, selecting 'blubuntu-wallpapers' for regex 'lubuntu*' 
Note, selecting 'lubuntu-desktop' for regex 'lubuntu*' 
Note, selecting 'blubuntu-session-splashes' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork-14-04' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork' for regex 'lubuntu*' 
Note, selecting 'ldm-lubuntu-theme' for regex 'lubuntu*' 
Note, selecting 'lubuntu-plymouth-theme' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork-13-04' for regex 'lubuntu*' 
Note, selecting 'blubuntu-look' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork-13-10' for regex 'lubuntu*' 
Note, selecting 'lubuntu-default-session' for regex 'lubuntu*' 
Note, selecting 'lubuntu-live-settings' for regex 'lubuntu*' 
Note, selecting 'lubuntu-icon-theme' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork-12-04' for regex 'lubuntu*' 
Note, selecting 'lubuntu-core' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork-12-10' for regex 'lubuntu*' 
Note, selecting 'plymouth-theme-lubuntu-text' for regex 'lubuntu*' 
Note, selecting 'lubuntu-restricted-addons' for regex 'lubuntu*' 
Note, selecting 'qlubuntu-default-session' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork-11-04' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork-11-10' for regex 'lubuntu*' 
Note, selecting 'lubuntu-lxpanel-icons' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork-10-04' for regex 'lubuntu*' 
Note, selecting 'lubuntu-artwork-10-10' for regex 'lubuntu*' 
Package 'lubuntu-plymouth-theme' is not installed, so not removed 
Package 'blubuntu-look' is not installed, so not removed 
Package 'blubuntu-session-splashes' is not installed, so not removed 
Package 'blubuntu-theme' is not installed, so not removed 
Package 'blubuntu-wallpapers' is not installed, so not removed 
Package 'ldm-lubuntu-theme' is not installed, so not removed 
Package 'lubuntu-artwork-10-04' is not installed, so not removed 
Package 'lubuntu-artwork-10-10' is not installed, so not removed 
Package 'lubuntu-artwork-11-04' is not installed, so not removed 
Package 'lubuntu-artwork-11-10' is not installed, so not removed 
Package 'lubuntu-artwork-12-04' is not installed, so not removed 
Package 'lubuntu-artwork-12-10' is not installed, so not removed 
Package 'lubuntu-artwork-13-04' is not installed, so not removed 
Package 'lubuntu-artwork-13-10' is not installed, so not removed 
Package 'lubuntu-extra-sessions' is not installed, so not removed 
Package 'lubuntu-live-settings' is not installed, so not removed 
Package 'lubuntu-nexus7-default-session' is not installed, so not removed 
Package 'lubuntu-nexus7-extra-files' is not installed, so not removed 
Package 'qlubuntu-default-session' is not installed, so not removed 
Package 'lubuntu-restricted-addons' is not installed, so not removed 
Package 'ubiquity-slideshow-lubuntu' is not installed, so not removed 
Package 'lubuntu-restricted-extras' is not installed, so not removed 
The following package was automatically installed and is no longer required: 
  python-pysqlite2 
Use 'apt-get autoremove' to remove it. 
The following packages will be REMOVED: 
  lubuntu-artwork lubuntu-artwork-14-04 lubuntu-core lubuntu-default-session 
  lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme 
  lubuntu-lxpanel-icons lubuntu-software-center plymouth-theme-lubuntu-logo 
  plymouth-theme-lubuntu-text 
0 to upgrade, 0 to newly install, 11 to remove and 25 not to upgrade. 
Remv lubuntu-desktop [0.55] 
Remv lubuntu-default-session [0.39] 
Remv lubuntu-core [0.55] 
Remv lubuntu-default-settings [0.39] 
Remv lubuntu-artwork [0.45] 
Remv lubuntu-artwork-14-04 [0.45] 
Remv lubuntu-icon-theme [0.45] 
Remv lubuntu-lxpanel-icons [0.45] 
Remv lubuntu-software-center [0.0.8-0ubuntu1] 
Remv plymouth-theme-lubuntu-logo [0.45] 
Remv plymouth-theme-lubuntu-text [0.45] 
plumtreed@plumtreed-lennie-M58:~$ 
```

At least we have a result. Does this help at all?

---

### Post by ajgreeny on 2015-11-20
Yes it does, as it shows you have several lubuntu packages installed that are not normally part of the default ubuntu, Xubuntu or Kubuntu installation, as shown in the bottom part of your output:-
```
The following packages will be REMOVED: 
  lubuntu-artwork lubuntu-artwork-14-04 lubuntu-core lubuntu-default-session 
  lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme 
  lubuntu-lxpanel-icons lubuntu-software-center plymouth-theme-lubuntu-logo 
  plymouth-theme-lubuntu-text 
```
Now we either try to figure out where they all came from, remove them by omitting the **-s** option in the command, or leave things as they are and wait until you clean install 16.04, as you say you might do.

---

### Post by Plumtreed on 2015-11-20
I removed the files as suggested and this cleared the splash screen problem and I will do a fresh install when 16.04 is available...........I can't see much point in searching for the cause of the initial problem.

Ubuntu is running well on my Desktop and I will get around to removing some of the extra apps that appeared......and, Lubuntu is running well and smoothly on the Laptop.

Thanks for your help and patience.

---

### Post by ajgreeny on 2015-11-20
You're welcome.

I am very happy that we managed to find the packages that were causing the problem and remove them.

---

