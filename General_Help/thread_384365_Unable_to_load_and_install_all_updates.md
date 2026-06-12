---
title: "Unable to load and install all updates"
date: 2007-03-14
forum: General Help
---

### Post by Handssolow on 2007-03-14
I'm unable to update update manager.
I've had a problem with Update Manager on one of my PCs virtually since moving to Edgy. The icon appears showing there are updates, I open Update Manager and am only able to load a proportion of the available files to be updated. After it installs the available updates it still shows one or two remaining. I select to install these, a box appears with "reading state information" but then closes leaving the files still to be updated.

I reported this on another post some months ago and filed a bug report. I've been getting round this problem updating using the terminal with-

sudo aptitude update
sudo aptitude dist-upgrade

Today there were 4 files to update but I wasn't able to download the latest Update Manager 0.45.2 so I move to using the terminal but this hasn't worked, giving-


handssolow@handssolow-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Segmentation fault (core dumped)

I tried reinstalling Update Manager 0.45 with Synaptic Package Manager and this didn't enable me to upgrade Update Manager.

Any help and suggestions appreciated?

---

### Post by Handssolow on 2007-03-14
Some progress. Using Edgy, I thought I'd check yet again the sources list

sudo gedit /etc/apt/sources.list

and to my surprise found one old Dapper source which I then removed.

At least I can report that I've been able to install the latest Update Manager 0.45.2 using the terminal commands. Not sure yet though if my Update Manager problem was caused by this old Dapper source. Time will tell when there are some more updates to download.

---

### Post by Kateikyoushi on 2007-03-14
Building tag database... 

This would be next, I will look into it what can be done about it.

---

### Post by Kateikyoushi on 2007-03-14
I see you already figured it out, if you need a sources.list can find one here. [LINK]("http://www.psychocats.net/ubuntu/sources")

---

