---
title: "help flash video"
date: 2007-12-08
forum: General Help
---

### Post by n0greenfx on 2007-12-08
hey i am running ubuntu gutsy gibbon i have an amd athlon 3200 xp+ processor and about 700m of ram and a geforce 2 400\400mx graphics card. i have compiz and everything runs smoothly since i installed the legacy driver for it.when i go to site  like youtube (the only one that will actually somewhat work) THe video is all choppy and it slows my system down extremely also the youtube player does not look right i am not able to seek or pause or up the volume. Any i deas this is only day 2 with linux and or ubuntu so im very new. lol

---

### Post by n0greenfx on 2007-12-08
heres wat i tryed i uninstalled gnash that did not seem to work and install adobe flash and it says i dont have the newest player installed idk wats the hell is wrong

---

### Post by Swmmrman on 2007-12-08
Ok i had a similar thing with gnash.  Borken and chopy.  However when i install flash.  It says its still not installed,,  only possible dif is a am running 64 bit.  However the machine 5 feet from me is 32 and does the same

---

### Post by lswest on 2007-12-08
what you have to do is uninstall gnash, and then go to [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux") and download the tar.gz and extract it to wherever you want.  then in the terminal do
```
cd install_flash_player_9_linux
```
then, when in the folder run
```
sudo sh flashplayer-installer
```

if that doesn't work, try just double-clicking on the file and choosing "run in terminal".  it will need root privileges though, so you'd have to run it from your root account.
then at the prompt answer the questions and keep in mind the path to the firefox "install" is /usr/lib/firefox/

hope it helps.  If you have any issues feel free to PM me, and ill post answers here, or reply back.

---

### Post by n0greenfx on 2007-12-08
i installed flash then go to utube and i get this everytime

---

### Post by Swmmrman on 2007-12-08
Us 64 bit guys are loved.
```
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

```

---

### Post by daradib on 2007-12-08
There is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This caused Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by n0greenfx on 2007-12-09
that did it ******* awsome thank u so much iv been on this for days

---

### Post by Mrs Twaddle on 2007-12-09
thanks..
videos on youtube now play fine for me... :D 
but i still can't play flash games..

---

### Post by daradib on 2007-12-09
Your welcome. I don't know, however, what the problem with flash games is. I have heard of bugs with Flash 9 regarding games, but not playing at all seems strange. It could be a bug, but maybe someone else can answer that better than I can.

And BTW, you are sure these are flash games and not Shockwave games (which unfortunately to the best of my knowledge don't play on Linux at all unless you use WINE on Windows Shockwave and Windows Firefox). Speaking of which, you might want to take a look at the [Shockwave Player and Plugin for Linux petition]("http://www.petitiononline.com/linuxswp/petition.html") and the [64 bit Linux Flash/Shockwave players petition]("http://www.petitiononline.com/lin64swf/petition.html").

---

### Post by Mrs Twaddle on 2007-12-09
I'll sign the petition, :D they are definately flash games though. I host them on one of my sites.
It seems to bet just some of the flash games that won't run at all. Mainly things like Space Invaders.
Card games, and games where the click of a mouse triggers a reaction are fine. Ones that run on their own as well as when you click don't seem to work very well, if at all.

---

### Post by daradib on 2007-12-09
> **Mrs Twaddle said:**
> I'll sign the petition, :D they are definately flash games though. I host them on one of my sites.
It seems to bet just some of the flash games that won't run at all. Mainly things like Space Invaders.
Card games, and games where the click of a mouse triggers a reaction are fine. Ones that run on their own as well as when you click don't seem to work very well, if at all.

Could you give me a URL of a game that won't play. I want to test it on my computer.

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by Mrs Twaddle on 2007-12-11
> **daradib said:**
> Could you give me a URL of a game that won't play. I want to test it on my computer.

they are on my site, currently guests can't play.
I can pm you a user and pass for access though if necessary?

i've managed to get some other games working by having a second page open on another site/page and occasionally browsing it when the flash freezes. That seems to get it started again. Doesn't with all games as you can't play if there is constant action..

---

### Post by sweeper on 2007-12-11
[B][I][COLOR="Magenta"]  	
daradib!!

Thank you![/COLOR][/I][/B]

---

### Post by Divisionbyzer0 on 2007-12-18
> **daradib said:**
> There is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This caused Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)


Awesome, dude.  Works like a charm on the first try.  I'm glad I don't use 64 bit anymore.  Was nothing but a pain.

---

### Post by daradib on 2007-12-18
> **Divisionbyzer0 said:**
> Awesome, dude.  Works like a charm on the first try.  I'm glad I don't use 64 bit anymore.  Was nothing but a pain.

I have expanded on that and explained everything [here]("http://ubuntuforums.org/showthread.php?t=636397").

---

### Post by richard.deverell on 2008-04-09
thanks for the help with the flash mate. I was brand new ubuntu user with not much idea about linux os and was stumped. I read through a few different googled forum answers but the only one I could understand and use was yours. The fix worked straight away and I sopped cursing ubuntu and am now pretty impressed. Good on yer mate anyway. Cheers

---

### Post by daradib on 2008-04-09
And cheers to you. 

It's good to hear that the fix helped another person.

---

### Post by richard.deverell on 2008-04-19
sorru daradib. [I] fixed problem now with official fix[/I

---

