---
title: "can't install 7.04"
date: 2007-10-20
forum: General Help
---

### Post by fredfelter on 2007-10-20
I'm trying to install Feisty on an IBM T23 with Dapper already on it. When I put in the installation CD and boot from the first install option I end up with a blank screen after seeing a lot of scrolling (ie no desktop). If I try from the second option, the safe graphics mode I get a low resolution screen that doesn't show Next and Back at the bottom of the display so I can't progress with the installation. In other words either approach is a dead end for me.
   Help please and thanks.

---

### Post by Frugoo Scape on 2007-10-21
try the text based installer

---

### Post by ruibernardo on 2007-10-21
> **fredfelter said:**
> I'm trying to install Feisty on an IBM T23 with Dapper already on it.

Don't, you can't upgrade directly to Feisty. If you use a Feisty CD (alternate or desktop) you should/will do an new install. You have to upgrade to Edgy and then to Feisty (and then to Gutsy) to upgrade from Dapper.

> **fredfelter said:**
> When I put in the installation CD and boot from the first install option I end up with a blank screen after seeing a lot of scrolling (ie no desktop). If I try from the second option, the safe graphics mode I get a low resolution screen that doesn't show Next and Back at the bottom of the display so I can't progress with the installation. In other words either approach is a dead end for me.
   Help please and thanks.

If you are getting a "screen" you are using a Desktop CD. The desktop CD isn't for (and can't do) an upgrade and like I said, you should use an Alternate CD to do an upgrade, because the desktop CD only makes new installs - only the alternate CD can upgrade (just by putting it in the drive with Dapper running, an Edgy alternate CD in this case, and then an Feisty Alternate CD after).

More info about this in [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) and **[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes).**

Hope this helps you to do a safe upgrade.

---

### Post by fredfelter on 2007-10-21
Thanks for the replies. 
I am a rank beginner to Linux and I do NOT want to upgrade. I'm changing from Dapper to Feisty because I couldn't make the sound work on my laptop under 6.06; after hours of tinkering and googling. I had no worthwhile data to retain on the Dapper version so I thought by throwing the Feisty CD in it would do a clean install which is what I really want.

Questions:
So I shouldn't use the Feisty install CD? You mean there is a different version of Feisty for laptops than desktops? Why?
I can't see what Frugoo Scape has to do with a Linux installation? Looks like some gaming app.

Again, the problem is that the install mode takes me to a blank screen. I had a similar problem installing Dapper but I was able to overcome it by doing a safe mode install and then reconfiguring xorg. In this case I can't use the safe mode because the screens don't show the Next and Back buttons at the bottom of the screen (the low res. graphics extend past the computer screen).

Thanks.

---

### Post by logos34 on 2007-10-21
> **fredfelter said:**
> So I shouldn't use the Feisty install CD? You mean there is a different version of Feisty for laptops than desktops? Why?

no, the Alternate cd is simply a text-mode version (for all computers).  On t[he main page]("http://www.ubuntu.com/getubuntu/download") just below the green 'start download' arrow there's a box you check if you want the alternate cd.
> 
I can't see what Frugoo Scape has to do with a Linux installation? Looks like some gaming app.

That's simply a link in his signature.

> Again, the problem is that the install mode takes me to a blank screen. I had a similar problem installing Dapper but I was able to overcome it by doing a safe mode install and then reconfiguring xorg. In this case I can't use the safe mode because the screens don't show the Next and Back buttons at the bottom of the screen (the low res. graphics extend past the computer screen).

Actually, there's a workaround if you want to try it.  When you get to the desktop right-click on it and change the bottom panel to the left side, and the top panel to the right side.  That should clear just enough room at the bottom to see the forward buttons.

---

### Post by fredfelter on 2007-10-21
Thanks for the workaround Logos34; that was what I needed to be able to see the entire screen.

Now I'm trying to set up some sound as that will be a basic need. Being a Linux newbie I first need to test it, then if someone could refer me to the most basic method to get audio settings up and runnning with Thinkpad 23 with Sound Fusion CS46 card, Cirris Logic CS chip and Feisty. I was hoping it would work "out of the box" as I never could get it working in Dapper.

Thanks in advance.

---

### Post by logos34 on 2007-10-22
try this troubleshooting howto:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

