---
title: "Firefox - Snap or .deb update?"
date: 2022-08-31
forum: General Help
---

### Post by echotech2 on 2022-08-31
Is there way to tell if this Firefox (or any other program ) update is a Snap or .deb?

Changes for firefox versions:
Installed version: 104.0+build2-0ubuntu0.22.04.1~mt1
Available version: 104.0.1+build1-0ubuntu0.22.04.1~mt1

 I've added the Mozillateam PPA and that other change to remove the snap as described in a couple of posts and I think I got it right.

---

### Post by &amp;KyT$0P# on 2022-08-31
If you don't have snapd installed, you can use [FONT=Courier New]-s[/FONT] switch of [FONT=Courier New]apt[/FONT] or [FONT=Courier New]apt-get[/FONT] to only simulate the update, and see if it wants to pull in snapd.

If you do have snapd installed, you could [FONT=Courier New]apt-get download firefox[/FONT] and manually inspect the contents of the package.

---

### Post by grahammechanical on 2022-08-31
Open Firefox. Click on the hamburger icon - three horizonal lines and then select Settings. Scroll down until you come the the section called Firefox Updates. There you will see what version of Firefox you are using and whether it is a ded or snap version.

Regards

---

### Post by echotech2 on 2022-09-01
The only things under Firefox Updates is:
  (Hand copied, won't let me copy & paste)
 
Version 104.0 (64 bit)
Mozilla Firefox for Ubuntu
canonical - 1.0

-no mention of .deb or snap
  
 I was mostly just worrying if the above (post 1)Firefox update was going to try to install the snap version.  22.04 installed the Snap version and things did not go well, no bookmarks, passwords, etc.  Maybe this weekend I'll follow a post I saw and remove snapd and companions.  I haven't yet because there's lots of things in "snap list" that I don't know what they are and maybe they are important..

---

### Post by mIk3_08 on 2022-09-01
> **echotech2 said:**
> The only things under Firefox Updates is:
  (Hand copied, won't let me copy & paste)
 
Version 104.0 (64 bit)
Mozilla Firefox for Ubuntu
canonical - 1.0

-no mention of .deb or snap
  
 I was mostly just worrying if the above (post 1)Firefox update was going to try to install the snap version.  22.04 installed the Snap version and things did not go well, no bookmarks, passwords, etc.  Maybe this weekend I'll follow a post I saw and remove snapd and companions.  I haven't yet because there's lots of things in "snap list" that I don't know what they are and maybe they are important..
Just type the command below and I think if the results do have a "/snap"  location address that app probably from snap and if the address location  result doesn't have any "/snap"
location address results that is not  from snap. And on how to open terminal just press ctrl and alt + t in  your desktop or just find it in your Ubuntu installed applications.  Regards and cheers
```
type firefox
```

---

### Post by VMC on 2022-09-01
```
$ type firefox
firefox is /usr/local/bin/firefox
```
I'm on "**firefox-*.tar.bz2" **install

---

