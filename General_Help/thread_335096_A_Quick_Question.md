---
title: "A Quick Question"
date: 2007-01-09
forum: General Help
---

### Post by Griever on 2007-01-09
I am about to download 6.10, but before I do I want to make sure that my laptop is compatible with it. Sorry if this has been asked before.

My laptop is a [HP  dv2000]("http://h10010.www1.hp.com/wwpc/uk/en/ho/WF06a/21675-38187-38191-38191-38191-12435978.html").

---

### Post by scrooge_74 on 2007-01-09
Probably since it is a HP, HP backs Linux so it will probably work.  You can download the iso for 6.10 and since it is a Live CD you can run it and test to see if anything does not work as suppose before installing.  That is the beauty of Live CDs :D

Also you can check here for more info

[http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/)
[http://www.leenooks.com/](http://www.leenooks.com/)

---

### Post by aysiu on 2007-01-09
You might want to check out this page:
[http://yergler.net/Ubuntu_on_the_HP_DV2000](http://yergler.net/Ubuntu_on_the_HP_DV2000)

---

### Post by Quillz on 2007-01-09
> **scrooge_74 said:**
> Probably since it is a HP, HP backs Linux so it will probably work.  You can download the iso for 6.10 and since it is a Live CD you can run it and test to see if anything does not work as suppose before installing.  That is the beauty of Live CDs :D

Also you can check here for more info

[http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/)
[http://www.leenooks.com/](http://www.leenooks.com/)
A lot of people are having trouble with the 6.10 Live CD. Instead, I would install 6.06 first, and then upgrade to 6.10 from there.

---

### Post by Griever on 2007-01-09
> **Quillz said:**
> A lot of people are having trouble with the 6.10 Live CD. Instead, I would install 6.06 first, and then upgrade to 6.10 from there.

There aren't any download sites that give me decent speed for 6.06.  But at this point, I'm kind of worried about my Wireless, will it still work?  I've read that Ubuntu has a bug when doing wireless stuff.

---

### Post by johnwillis on 2007-01-09
If you are based in the UK and want a pressed copy of 6.06 I have a spare one. I could always send it you through the post.

Just PM me.

- JW

---

### Post by scrooge_74 on 2007-01-09
> **Griever said:**
> There aren't any download sites that give me decent speed for 6.06.  But at this point, I'm kind of worried about my Wireless, will it still work?  I've read that Ubuntu has a bug when doing wireless stuff.

About your speed you can try this

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

About wireless you can check these

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

---

### Post by Quillz on 2007-01-09
> **Griever said:**
> There aren't any download sites that give me decent speed for 6.06.  But at this point, I'm kind of worried about my Wireless, will it still work?  I've read that Ubuntu has a bug when doing wireless stuff.
You can use ShipIt for 6.06. And I've found that all the hardware that worked in 6.06 worked in 6.10, except after the upgrade, my monitor required an ATI driver (very simple to install) so I could run my native resolution of 1280x1024.

---

### Post by greybit on 2007-01-10
I've also got an HP dv2000.  The 6.10 Edgy Live CD worked fine for me and the program Wifi-radar allowed me to connect to my wireless network with no problems.

Edit: Well, I forgot the trouble I went through initially to get the wireless working.  I was reminded when I destroyed my installation and chose to reinstall a couple of days ago.  It is true that Wifi-radar allowed me to connect in the end but before that I did the following:
 
First I installed ndiswrapper which allows linux to use a Windows wifi driver:
 
```
sudo -i
apt-get update
apt-get install ndiswrapper-utils*
```
(or you could use the latest version from the ndiswrapper website)

Then I downloaded from the HP website the Windows XP driver for the wireless card in my laptop.  Since it is of .exe format, I installed cabextract and decompressed the file as follows:

```
apt-get install cabextract
cabextract filename.exe
```

Now there should be a .inf file.  Use ndiswrapper to install it:

```
ndiswrapper -i something.inf
```

Finally, so the old driver isn't loaded upon startup but ndiswrapper and the new driver are loaded, do the following:

```
nano /etc/modprobe.d/blacklist
```
add the line "blacklist bcm43xx" without the quotes, save & exit.

```
nano /etc/modules
```
add the line "ndiswrapper" without the quotes, save & exit.

Hope this helps.

---

