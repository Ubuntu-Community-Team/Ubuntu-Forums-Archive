---
title: "Virtualization"
date: 2007-08-30
forum: General Help
---

### Post by strange_cathect on 2007-08-30
Hello,

I currently boot between XP and Ubuntu.  However, the only reason I have to keep XP is for one crucial program that has no equivalency in Linux.  So I want to try virtualization.

My question:

I want to have my desktop be a clean install of Ubuntu and access the virtual appliance on another computer (my fileserver/music slave) which is located in another room.

Is this possible?  How would I do this?

---

### Post by notwen on 2007-08-30
Define 'virtual appliance'.  Are you saying you want to use an application installed on this computer located in another room?  Your first statement confuses me as I'm not sure if it is related to your question.  

As far as your crucial app that you need WinXP to run, have you ever considered trying to run it in VMware or VirtualBox?  I use VirtualBox for a couple of apps here and there that I cannot find a genuine replacement for here on Linux.

---

### Post by gaussian on 2007-08-30
Two comments:

1. This should be doable at least through VNC or similar remote access program (plain X via SSH would do this too, but could  be slow depending on your network). 

2. This might be something you already know, but I learned the hard way: the Windows XP OEM Reinstall CD that probably came with your computer probably won't work with virtualization. I got around this (on my University owned computer) by getting a site-licensed XP Installation CD from the IT people, but you might have to resort to other means (like buying XP license).

---

### Post by jrusso2 on 2007-08-30
> **strange_cathect said:**
> Hello,

I currently boot between XP and Ubuntu.  However, the only reason I have to keep XP is for one crucial program that has no equivalency in Linux.  So I want to try virtualization.

My question:

I want to have my desktop be a clean install of Ubuntu and access the virtual appliance on another computer (my fileserver/music slave) which is located in another room.

Is this possible?  How would I do this?

I think this is what vmware server is for.

---

