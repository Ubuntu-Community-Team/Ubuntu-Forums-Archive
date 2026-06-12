---
title: "Ubuntu much slower than it should be. Is ATI to blame or something else ?"
date: 2007-05-27
forum: General Help
---

### Post by moljac024 on 2007-05-27
Hello dear fellow ubuntu users, please take some time to answer my post, any help will be appreciated. Thank you.

I got ubuntu 7.04 about a week ago, had some issues at first (first linux distro unless you count my  whole couple of days with debian :) ) but resolved them later, however, i feel that ubuntu is more sluggish than it should be. I do not have a weak computer, my specs are :

Pentium D 2.8 Ghz (dual core)    processor
ASUS P5PL2                                    motherboard
1 GB DDR2 (Apache, i think)        RAM memory
ATI radeon x550                            graphic card

Programs sometimes take a little longer to open, i sometimes get lag when navigating through the gnome menus, my panels disappeared a few times, beryl (0.2.1) was buggy,freezing my system all the time(i gave up on it completely).  I noticed however that those problems were gone when i activate desktop effects (compiz) but then i have some other issues with the screen drawing, it leaves trailes sometimes.

Is this because of ATI's bad support for linux ? Bare in mind, i did not tweak anything related to the ati drivers, i am using the open source ones which came with ubuntu. I read somewhere in the forums that ati has horrible 2d acceleration....is this true ? Are there some lines i could add to my xorg.conf to improve my ati performance ?

Also, i possess a Samsung Syncmaster 720N 17" TFT monitor and when starting ubuntu the monitor displays the message: "Not optimum mode. Recommended mode is 1280x1024" and that message would slowly move from the center of the screen to the bottom right corner and then i would log in....does someone know how to fix this ?

---

### Post by Lucifiel on 2007-05-27
First things first, Beryl and Compiz are both beta. Please note that running them might cause your system to lag as well as encounter other strange errors. 

Secondly, which ATI graphics drivers did you install? Are they the fglrx version? If so, get them off your computer now!!!! They are problematic and often cause various system issues for many .

Edit: I'd disable Compiz and do an 
> 
sudo apt-get remove beryl beryl-manager emerald emerald-themes 

and see what happens with your computer after that in terms of performance.

---

### Post by moljac024 on 2007-05-27
No, i said i didn't install any ati drivers (i am aware that the fglrx version is horrible), i'm using the open source ones that came with ubuntu....

And i know that beryl and compiz are beta.

EDIT: I did get rid of beryl but not compiz (i am not using it, though)

---

### Post by Lucifiel on 2007-05-27
Well, then, try this.
> 
sudo apt-get install htop



Install htop(it is a lot better than top) and run it to see what's causing your pc to lag.

Just type htop in Terminal or you can run it off Applications ====> System Tools.

---

### Post by tgalati4 on 2007-05-27
Ubuntu should fly on your hardware.  If you have SATA drives, then it's possible that you are experiencing slowdowns that others have experienced.  Mark all of the respositories in Synaptic and see if a newer kernel will help.

Try a Dapper Live CD and see if your system is faster (other than the sluggish CD ROM access--which is to be expected).  With 1GB of RAM, you will be running from RAM anyway, once things are loaded from CD.

---

### Post by moljac024 on 2007-05-27
> **Lucifiel said:**
> Well, then, try this.


Install htop(it is a lot better than top) and run it to see what's causing your pc to lag.

Just type htop in Terminal or you can run it off Applications ====> System Tools.

I will thank you....

[QUOTE=tgalati4]Ubuntu should fly on your hardware. If you have SATA drives, then it's possible that you are experiencing slowdowns that others have experienced. Mark all of the respositories in Synaptic and see if a newer kernel will help.[/QUOTE]

I do have a SATA drive, didn't know there was an issue with those.....will look into in, thanks

---

### Post by moljac024 on 2007-05-27
Hmm, i just did some quick testing and noticed that firefox can use up to 90% of the CPU....what gives ??

---

### Post by Lucifiel on 2007-05-27
> **moljac024 said:**
> Hmm, i just did some quick testing and noticed that firefox can use up to 90% of the CPU....what gives ??

The default Firefox browser is junk for many users.

Try running Swiftfox instead.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)

---

### Post by Lucifiel on 2007-05-27
Also, after installing Swiftfox, try installing these few extensions:


Fastefox, Adblock, NoScript and Session Manager.

Edit: Many websites use pretty terrible coding which causes your browser to lag, freeze or even crash. NoScript and AdBlock block most of these nasty pests.

---

### Post by fragos on 2007-05-27
Epiphany is much faster.  Disabling IPv6 also helps and DNS performance of your ISP can also be a factor.  Comcast has very fast DNS and I've heard Earthlink doesn't.

---

### Post by moljac024 on 2007-05-27
I used firefox in windows and it was so much better....why is it lagging so much on linux ? 
I'd really like to keep browsing with it...

---

### Post by Lucifiel on 2007-05-27
> **moljac024 said:**
> I used firefox in windows and it was so much better....why is it lagging so much on linux ? 
I'd really like to keep browsing with it...

Swiftfox and Epiphany are both errr children of Firefox. As in, they're based on Firefox. In fact, Swiftfox is FF optimised for Linux. You can simply copy over your profiles and other settings into your Mozilla directory and Swiftfox will just use them. I'm not sure about Ephiphany, though.

---

### Post by Crafty Kisses on 2007-05-27
The thing is, I'm not able to download any drivers at all for my NVIDIA card, like really, I've tried EVERY way, and all it does, is take me to verbose mode. Then I cannot get back to my desktop. Any Ideas.

---

### Post by moljac024 on 2007-05-28
> **Lucifiel said:**
> Swiftfox and Epiphany are both errr children of Firefox. As in, they're based on Firefox. In fact, Swiftfox is FF optimised for Linux. You can simply copy over your profiles and other settings into your Mozilla directory and Swiftfox will just use them. I'm not sure about Ephiphany, though.

Ok, will try swiftfox, but i still don't understand why does firefox lag my pc so much....and as i've said if i enable 3d acceleration it works fine....so it smells to me like ATI's to blame....

EDIT: I just gave swiftfox a try and it's the same bloody thing! 

The lag persists on flash and java intense sites, why ? When browsing those sites i feel like I own a P2 300MHz......

---

### Post by moljac024 on 2007-05-28
I think i got it....i had java 5 and java 6 both installed.....removing java 5 seemed to speed up things...

EDIT: Still very sluggish desktop experience - using htop i could see that firefox and x use most of the cpu (up to 100%)....please help! This can't be right...

---

### Post by moljac024 on 2007-05-28
Please someone ??

I also noticed that sometimes a process called something like gnome-icon pops up using 100% CPU for a second...

---

### Post by Lucifiel on 2007-05-28
Hmmm... did you install the Add-ons(also known as Extensions) I suggested? If not, I'm afraid there's no way you can solve part of these problems. No-script will prevent Flash, Java and Javascript from loading by default. 

As for the other extensions, try looking up the descriptions yourself. 

I hate to be mean but you've to be willing to consider and implement suggestions given by others. Otherwise, people will just ignore this thread and move on.(This is a hard lesson that I learnt when I first started using Ubuntu.)

---

### Post by moljac024 on 2007-05-28
I have been using those extensions that you listed before (in windows) and had them installed way before you suggested it :)

However, when i open a particular site (which needs to have java enabled and i allow it) it lags while i didn't have those problems in windows (the same site). I am worried, it maybe that one site now but others can follow. I really don't understand why something that worked in windows is causing problems in Ubuntu....

And i did listen to your suggestions, i had the same issues with swiftfox.....

Thanks anyway.

P.S. I don't really want to switch away from firefox, and i won't believe that my 1 gig of DDR2 ram and a dual core 2.8 ghz processor is not enough for it !

---

