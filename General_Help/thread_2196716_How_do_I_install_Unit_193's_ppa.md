---
title: "How do I install Unit 193's ppa?"
date: 2013-12-31
forum: General Help
---

### Post by vasa1 on 2013-12-31
My experience with ppas is quite limited. I've done things like:```
USING [ARIA2C](https://launchpad.net/~t-tujikawa/+archive/ppa)  
sudo add-apt-repository ppa:t-tujikawa/ppa  
sudo apt-get update  
sudo apt-get install aria2  

```
Now I want to install Xombrero 1.6.3 for Saucy and I found that [Unit 193 has a ppa]("https://launchpad.net/~unit193/+archive/test") but the installation instructions are different. They involve editing sources.list and a "key" and a "fingerprint".

If I do go ahead and edit */etc/apt/sources.list* to add **deb [http://ppa.launchpad.net/unit193/test/ubuntu](http://ppa.launchpad.net/unit193/test/ubuntu) saucy main**, at what stage are the "key" and "fingerprint" required?

What else do I need to do?

---

### Post by carl4926 on 2013-12-31
From what I see it looks the same
```
[COLOR=#000000][FONT=monospace]sudo add-apt-repository [/FONT][/COLOR]**ppa:unit193/test**
```
enter to accept
```
sudo apt-get update
```

---

### Post by vasa1 on 2013-12-31
Actually, it was quite simple. I right-clicked on sources.list in Thunar and got an option to open it with "Software and Sources". I was then prompted to update and now have Xombrero 1.6.3.

---

### Post by vasa1 on 2013-12-31
> **carl4926 said:**
> From what I see it looks the same
```
[COLOR=#000000][FONT=monospace]sudo add-apt-repository [/FONT][/COLOR]**ppa:unit193/test**
```
enter to accept
```
sudo apt-get update
```
Thanks, Carl!

Got it going! The Chromium pepper flash should be good news for Chromium users. I think I remember you posting about how another distro (SuSE?) had it available.

---

### Post by carl4926 on 2013-12-31
Yes it's in the Packman repo which supplies multimedia for openSUSE
Install is easy with no addition configuration

Funny thing though. On my eeepc, Pepper flash doesn't play youtube video properly. So I just use the standard, now ageing flash-plugin.
It's the same for Chrome and Chromium BTW and on all distros (openSUSE, Ubuntu, Mint)

---

