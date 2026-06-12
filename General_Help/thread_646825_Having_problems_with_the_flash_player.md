---
title: "Having problems with the flash player"
date: 2007-12-21
forum: General Help
---

### Post by Dark.Heat on 2007-12-21
I'm know to Linuz, it's my first OS other than Windows and so far I like it. I just can't figure out how to get the flash going. Every time I go on Youtube it says missing plugin. I've tried installing from clicking the bar, and it says restart Firefox when it was done. I did that, no results. I tried putting in the command in the Terminal - sudo apt-get install sun-java6-plugin - and nothing still. I'm new at this, help please?

---

### Post by banewman on 2007-12-21
You need the shockwave plugin from here -
[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)
:)

---

### Post by Dark.Heat on 2007-12-21
Still nothing unfortunately, here's the message I get

*We are unable to locate a Web player that matches your platform and browser.*

:(

---

### Post by Irony on 2007-12-21
Go here;

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Download option 1 and follow the instructions for option 1.

---

### Post by Dark.Heat on 2007-12-21
Alright, I opened it up in Archive, what do I do now?

---

### Post by Irony on 2007-12-21
Right click on the downloaded file and click extract here.

Then open up the resulting folder and find the installer file and drag it into a terminal and hit enter.

And thats it.

---

### Post by Erdem on 2007-12-21
open console...
```
sudo su
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -xzf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
mv libflashplayer.so /usr/lib/firefox/plugins/
```
that's all...

---

### Post by nebraska66 on 2007-12-21
> **Irony said:**
> Right click on the downloaded file and click extract here.

Then open up the resulting folder and find the installer file and drag it into a terminal and hit enter.

And thats it.

That got it sorted for me.  Man, Youtube was crashing me completely...and I had to pull the plug to get out from under it.

Thanks!

---

