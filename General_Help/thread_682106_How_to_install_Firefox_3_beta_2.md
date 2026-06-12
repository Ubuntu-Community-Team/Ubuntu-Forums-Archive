---
title: "How to install Firefox 3 beta 2"
date: 2008-01-29
forum: General Help
---

### Post by geovino on 2008-01-29
How to install Firefox 3 beta2 in Ubuntu 7.10?

it's not in Synaptic and I tried to download from Mozilla and got error messages.

I was able to install from synaptic in PCLOS MiniMe 2008 that I run on another PC and it works great. I thought I would be able to install here in Ubuntu. 

Any clues?

---

### Post by nick_h on 2008-01-29
There is an old guide for a manual install of 2.0 which may be of help - [link](https://help.ubuntu.com/community/FirefoxNewVersion).

---

### Post by bodhi.zazen on 2008-01-29
Here is the best advice on this I know of :

[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by geovino on 2008-01-29
> **bodhi.zazen said:**
> Here is the best advice on this I know of :

[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)

I using Xubuntu now and it won't let me move the tar file to the /opt directory. How do you do that? it's on my desktop right now.

---

### Post by bodhi.zazen on 2008-01-29
sudo mv tar /opt

you may need to

sudo mkdir /opt first

---

### Post by Meyithi on 2008-01-29
Use Swiftfox instead - [http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)

Works great and has repo's - remarkably stable on my box (3.0b3pre)

---

### Post by calabashkid on 2008-01-29
Just installed Ubuntu 7.10 so I am brand new to this OS.  I wanted to update Firefox to the latest version.  I downloaded it, extracted it and followed the instructions for installing\updating apps on Ubuntu but...

I cannot do it using the Add/Remove method.  The option to search for updates in Firefox is greyed out.

How should I proceed.  Thanks.

---

### Post by Het Irv on 2008-01-29
If you just installed and ran all of the updates the Firefox that came pre-installed should be current.  Can you go to Help-About, the most current is 2.0.0.11

btw: my check for updates is greyed out as well.  It may not be avalible unless Firefox detects an update.

---

### Post by sumguy231 on 2008-01-29
> btw: my check for updates is greyed out as well. It may not be avalible unless Firefox detects an update.
It's disabled in the Ubuntu build because you can use the package manager to update it, and unless you're foolishly running as root you wouldn't have permissions to do it anyway.

---

### Post by bodhi.zazen on 2008-01-29
Threads merged, similar question and answer, saves effort for all (I hope)

---

### Post by geovino on 2008-01-30
Thanks for all the advice, but I'll just wait for the final version 3 to come out in Synaptic. I've already tested it out in PCLOS and it works fine.

---

### Post by anthony.canucks on 2008-01-30
I followed the instructions given in the link but now when I try to start firefox it just says "starting firefox web..." for a minute then closes. Firefox doesn't actually open.

Does anybody know a way to fix that?

edit: I've got it working now.

---

### Post by sumguy231 on 2008-01-30
You should run it from the terminal to get useful error output that might tell you what is wrong.

---

