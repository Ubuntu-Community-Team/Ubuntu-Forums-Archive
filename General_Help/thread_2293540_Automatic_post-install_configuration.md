---
title: "Automatic post-install configuration"
date: 2015-09-05
forum: General Help
---

### Post by daniel263 on 2015-09-05
Some people do fresh installs of Ubuntu a lot, either because of change of hardware or for the sake of trying different versions and/or flavours.

But having to install and configure all software again is tedious and a huge headache.

I managed to write a couple of dozens of scripts which install all the software I use, including Skype, Dropbox, Telegram, Emacs and even games like Dwarf Fortress and Minecraft. Very few interaction is needed, rather to accept terms and conditions or to enter password for sudo. Really neat and takes just 25-30 minutes, mostly for downloading.

Definitely I am not alone, so I'd like to ask a couple of questions for those who do the same:

1. How do you deal with sensitive data? All non-sensitive config and dot-files can be stored on github, but what do you do with ssh keys and gpg stuff? I only found a way of copying everything to a flash drive and copying it back after installation
2. [most important] How to automate configuration of KDE (I use Kubuntu)? All those keyboard layouts, global shortcuts, app-specific shortcuts, font sizes. This is SOOOO tedious to do manually after each install. I tried to make the whole ~/.kde and ~/.config folders a git repositories, but they turned out to contain too much stuff, very hard to calculate an exact patch (diff) which is needed.

---

### Post by Bucky Ball on 2015-09-05
*Thread moved to **General Help**.*

Welcome. You posted your thread in a non-support, chat area. Good luck. :)

---

### Post by Habitual on 2015-09-06
> **daniel263 said:**
> 1. How do you deal with sensitive data? All non-sensitive config and dot-files can be stored on github, but what do you do with ssh keys and gpg stuff? I keep mine in a separate /home partition. ;)

---

### Post by ian-weisser on 2015-09-06
> **daniel263 said:**
> 1. How do you deal with sensitive data? All non-sensitive config and dot-files can be stored on github, but what do you do with ssh keys and gpg stuff? I only found a way of copying everything to a flash drive and copying it back after installation

I generally don't put sensitive data on trial systems. I usually don't need it for the trial.
I find the USB-stick method to be quite non-onerous.


> **daniel263 said:**
> 2. [most important] How to automate configuration of KDE (I use Kubuntu)?

I don't. I think one of the joys of a trial is to discover what others set as default.

---

### Post by HermanAB on 2015-09-06
The secret is to make /home a separate partition.  Then, when you re-install, don't format /home and everything will be retained.

---

