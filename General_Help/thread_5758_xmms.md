---
title: "xmms"
date: 2004-11-22
forum: General Help
---

### Post by thoms on 2004-11-22
Just installed Ubuntu yesterday after using Fedora Core 2/Red Hat for a few years. Now sorry if this is a really stupid question but why isn't xmms included with Ubuntu? Are there any plans to include it?

---

### Post by p!=f on 2004-11-22
[QUOTE=thoms]Sorry if this is a really stupid question but why isn't xmms included with Ubuntu? Are there any plans to include it?[/QUOTE]
XMMS is included. 
I'm not sure how's that with **Warty** (current stable) but in **Hoary** (developmnet branch) it's in the main.
If you get a message like "cannot find the package xmms" you probably don't have universe sources turned on. Check your /etc/apt/sources.list and/or documentation section at the Ubuntu Linux website.

---

### Post by thoms on 2004-11-22
aah, well I'm using Warty.

---

### Post by LongTooth on 2004-11-22
XMMS doen not come with Warty. But p!=f is correct about the universe sources. Open up your Synaptic, look in your Repositories list. Tick the boxes that show 'Universe (there are two of them)'. Then do a Search for XMMS. You will get a list. Select (Mark for Installation) Xmms and Apply. It will then be installed. Or if you feel like doing some CLI work, after you turn on the Universe sources in Synaptic, get out of it, open a terminal, key in 'sudo apt-get install xmms'. You will be prompted for your user password. Key it in. It will be installed. Some handy commands for the quick and simple CLI work is: sudo apt-cache search (packagename), sudo apt-get install (packagename), sudo apt-get update, sudo apt-get remove (packagename), apt-get clean.

PS  I'm using Warty and I have XMMS installed and working.

---

### Post by calvinpriest on 2004-11-22
You may also need to do this for xmms to work:
sudo apt-get install libmikmod2

There is a nice faq on multimedia here:
[http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94)

---

### Post by thoms on 2004-11-22
:grin: Thanks alot guys, thats really helpful, I'm liking this community almost as much as I'm liking the download speeds I'm getting with Ubuntu.

---

