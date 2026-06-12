---
title: "No menu or panel on older box"
date: 2023-02-16
forum: General Help
---

### Post by StrobeWylan on 2023-02-16
I have an older desktop with Xubuntu 14x on it. My plan was to update the OS through steps to bring it up to the current version. I clicked on the button to update from X14 to X16 and it started to work. I went out of the room for a minute and came back to a blue screen (not the BSOD thankfully). It was a blank standard desktop without the picture I had on it before. Nothing that I did changed anything. There is no panel, menu or anything. After letting it alone for a long time I shut it down by pressing the power button. When I start it up it loads Firefox (it had been set to load on startup). In fact I am using this computer right now. If I minimize Firefox I cannot get it back. I can't get a terminal with any keys such as cntl-alt-t. Right clicking on desktop does nothing. I can use Firefox to access Email like before but cannot open Thunderbird (or anything else for that matter). I use the power button as the only way to shut down. I have things on this computer that I need so I don't want just install the new OS which would erase stuff.

Thank You in advance

---

### Post by monkeybrain20122 on 2023-02-16
Why don't you just back up your data and do a fresh install? If you have important stuffs you should have backed them up anyway.

Xubuntu 14 is a long time ago and "upgrade" is not likely to succeed. Even if it works it would take a long time since the upgrade has to transverse through all the releases since 14 (are they still around?) A fresh install of 22.04 took me ten minutes.

---

### Post by StrobeWylan on 2023-02-16
I have my reasons for not doing what you suggest. Just want to restore the desktop.

---

### Post by ajgreeny on 2023-02-16
I totally agree with monkeybrain20122.
What are your reasons for not doing what we suggest?  There may be ways we can help you if you tell us why you can't or don't want to even try. clean installing and you honestly have little sensible chance of successfully updating any version of 14.xx which lost support nearly 6 years ago, to a currently supported version other than perhaps attempting a "dirty upgrade".

This means using the supported version you choose, 22.04 being my recommendation, as a live system on USB, installing from that using the **Something Else** option at disk preparation stage, but without formatting the partition or partitions of the new install when you do so.

I have no experience of doing this type of install/upgrade personally but in theory it means that all the current configurations you have and the added applications that installed in the 14.xx version should be upgraded to the new versions.  However, the 8 year move from 14 to 22 may just be a jump too far for that system to work so be prepared by first backing up all your personal files before doing anything, which, of course, you already do regularly, don't you!

---

### Post by grahammechanical on 2023-02-16
I am not using Xubuntu so this is just a guess.

It could be that there were significant changes to the user interface between Xubuntu 14.04 and 16.04. I am also thinking that user interaction was required. When the upgrade failed to just a response it timed out.

I suggest that from the Grub menu you selected Advance Options and then select a Linux kernel with recovery mode. At the recovery menu first select Network to establish an internet connection and then select Root shell prompt, Then run

```
apt update
apt upgrade
apt-get install -f
```

The last to command is to fix broken packages. When finished type exit to return to the recovery menu and select Resume. That should load to the desktop. It will be with an open source video driver. A reboot should load with the usual video driver.

Regards

---

### Post by StrobeWylan on 2023-02-16
Thank you all for your responses. I'll try to answer your questions. Yes I have backed up not just data, but everything using, I think it's called grysoft, not sure but can't access it or any other apps because don't have a panel or program starter. there are some apps that I really liked but can't get using the software catalog. There are newer apps but when I try them they don't always work to open the the saved files.  I tried to clone this computer on another box in case all got lost by installing X14 and using the same software to hopefully put everything from this box on to the next one. It didn't work. The apps and data were not installed. And like I said can't access them because the panel is gone or hidden or whatever. It's getting hard to remember what all I tried. I'm doing this with numerous interruptions from my job. I think I have grisoft (? ) on a usb drive, not sure.

---

### Post by StrobeWylan on 2023-02-16
> **grahammechanical said:**
> 

I suggest that from the Grub menu you selected Advance Options and then select a Linux kernel with recovery mode. At the recovery menu first select Network to establish an internet connection and then select Root shell prompt, Then run

```
apt update
apt upgrade
apt-get install -f
```

The last to command is to fix broken packages. When finished type exit to return to the recovery menu and select Resume. That should load to the desktop. It will be with an open source video driver. A reboot should load with the usual video driver.

Regards

Thanks. I think I tried this yesterday but to be sure I'll give it a go. When I get a break later.

---

### Post by StrobeWylan on 2023-02-17
This is what I got

---

### Post by ajgreeny on 2023-02-18
> **grahammechanical said:**
> I am not using Xubuntu so this is just a guess.

It could be that there were significant changes to the user interface between Xubuntu 14.04 and 16.04. I am also thinking that user interaction was required. When the upgrade failed to just a response it timed out.

I suggest that from the Grub menu you selected Advance Options and then select a Linux kernel with recovery mode. At the recovery menu first select Network to establish an internet connection and then select Root shell prompt, Then run

```
apt update
apt upgrade
apt-get install -f
```

The last to command is to fix broken packages. When finished type exit to return to the recovery menu and select Resume. That should load to the desktop. It will be with an open source video driver. A reboot should load with the usual video driver.

Regards
There is no point trying that as the repos for 14.04 and 16.04 are no longer available without editing you sources to point to the EOL repository versions.

However, even if you do that there will still be problems of using the system as no updates will be posted on those repos any more.

In spite of your comments I still believe a new installation of 22.04 will be the best option you have making sure first that you personal files are all backed up.

---

