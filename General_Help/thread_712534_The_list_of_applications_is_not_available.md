---
title: "The list of applications is not available"
date: 2008-03-01
forum: General Help
---

### Post by breaking on 2008-03-01
I'm on x86 gutsy, and want to play mp3s but the codecs weren't installed apparently.  So when I open an mp3, it gives me an option to download the Gstreamer plugins, but when I try it just says "The list of applications is not available".  Each time I click refresh and then try to download it again, it does the exact same thing.

It does the same thing for other software packages that download through Add/Remove.

Help! :(

---

### Post by breaking on 2008-03-01
Oops, I just figured out how to solve the problem.  For those of you out there who need to know, here's how:

Applications>Add/Remove>Preferences

Then basically check everything.

---

### Post by bigbudz on 2008-03-25
I'm having the same problem, but when I try to install the codecs for gstreamer by checking it in 
Applications>Add/Remove>Preferences it says the list of applications is not available again.

---

### Post by Zimmer on 2008-03-25
open the synaptic package manager and click on the  'reload' button to refresh your package info...

---

### Post by bigbudz on 2008-03-25
Thanks, I did that and it loaded everything ok. Theres 8 files there for gstreamer0.1, but they all are already installed.

---

### Post by Zimmer on 2008-03-25
> **bigbudz said:**
> Thanks, I did that and it loaded everything ok. Theres 8 files there for gstreamer0.1, but they all are already installed.
If you are still having problems with 'restricted' formats then check out this link 
https://help.ubuntu.com/community/RestrictedFormats

---

### Post by bigbudz on 2008-03-25
I used the sudo apt-get install ubuntu-restricted-extras command in terminal but it cn't find the package. It can read the list, build the tree, and read the info, but it can't find the package. I dont know whats wrong, I'm hooked up to the net for sure.

---

### Post by Zimmer on 2008-03-26
> **bigbudz said:**
> I used the sudo apt-get install ubuntu-restricted-extras command in terminal but it cn't find the package. It can read the list, build the tree, and read the info, but it can't find the package. I dont know whats wrong, I'm hooked up to the net for sure.

Double check you have the correct repositories enabled that have the packages... 

Check the Community maintained (Universe) and Non-free (Multiverse) boxes. and remember to reload to refresh the software lists.

---

### Post by bigbudz on 2008-03-29
You were right on. Didnt have the Universe, Multiuniverse checked. Everythings cool now and Ubuntu is awesome. I don't spose anyone knows how to restart a bittorrent download when you had to stop a big download halfway and shutdown. I heard Deluge is pretty good I might switch to that.

---

