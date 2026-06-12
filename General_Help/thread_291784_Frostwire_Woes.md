---
title: "Frostwire Woes"
date: 2006-11-02
forum: General Help
---

### Post by Craftycorner on 2006-11-02
I tried to install The Frostwire deb package.  It proved impossible for my friend and I to install, would someone look into that deb package and add it to the updates?  You have my thanks...

Crafty

---

### Post by taurus on 2006-11-02
Here is the link.  

[http://www.frostwire.com/](http://www.frostwire.com/)

Click on the Ubuntu/Debian to download it and once it's done downloading to your machine, open a terminal, Applications -> Accessories -> Terminal, and type

```

cd ~/Desktop
sudo dpkg -i FrostWire-4.10.9-2.i586.deb

```
Then, it should be in your Applications -> Internet.  However, before you run it, you have to have a copy of java on your machine first...  Use Automatix to install both java and frostwire if installing it by hand is a little too hard for you.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Craftycorner on 2006-11-03
The prob is I had Java in my machine, and the bugger still wouldn't co-operate.  The friend said it was something to do with the way the deb was packaged.  I of course didn't know beans about what he was talking about...

---

### Post by NeoLithium on 2006-11-03
Frostwire is also available when you install automatix 2; [http://www.getautomatix.com](http://www.getautomatix.com)

Easiest way I find to install some of the little things for less headaches right after a fresh install of Ubuntu.

---

