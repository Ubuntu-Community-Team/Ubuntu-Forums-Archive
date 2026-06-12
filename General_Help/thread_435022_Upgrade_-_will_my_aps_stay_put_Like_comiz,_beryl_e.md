---
title: "Upgrade - will my aps stay put? Like comiz, beryl etc"
date: 2007-05-06
forum: General Help
---

### Post by olavjunior on 2007-05-06
I'm thinking about upgrading from edgy to feisty. But I do have second thoughts, cause I've gone a long way to get my edgy setup exactly the way I want. To get the compiz to work correctly was a pain in the a., but now I'm really satisfied with things. 

So if I upgrade, will I loose all my aps and settings?? I have my home on a seperate partition. So since I've never done this before, Iæm wondering how it will turn out. Because of school and exams, I don't have time to play around with config and spending hours and hours with error searching. 

The reasons I mainly want Feisty, is that my microphone worked from the live cd (hp dv 2130), I can easily use security on my wireless network (never got to work in edgy). 

I've also had some issues dual-booting with xp. My xp is really ******, and I stay out of it as much as I possible can. But I share the home-dir betweeen the two oses, and sometime I belive xp locks some of the files in home, causing my ubuntu to not beeing able to boot (soft cpu lockup detected on sda7 -my home). I'm not sure that it's the xp doing this though.. But yesterday I couldn't get to my home eighter from xp, nor boot ubuntu, so the situation is kind of unsustainable. 

So what's your thoughts on this? I read alot of people having truble with the upgrade. Will I be spared since I have home on a seperate partition? And is there any way of totally backing up my edgy on a external drive, so that if it all goes down the drain, I could just restore edgy from backup?

---

### Post by Theimon on 2007-05-06
There are different ways of upgrading, I prefer to do a fresh install. Just make sure you're not formatting your /home partition and you should keep settings and stuff. Maybe take some .conf files from /etc as well, but that's not really necessary.

---

### Post by strabes on 2007-05-06
All your apps will retain their settings and things. Your preferences will be saved. Beryl will most likely be broken though.

---

### Post by olavjunior on 2007-05-07
:sad: Alright... just upgraded.. hmmmmm
My xorg.conf was broken, something about my version in xorg not the same as something else. So I started the live-cd and copied the xorg.conf generated from that one. But of course compis doesn't work. Are my nvidia drivers gone? Any way of checking this?  Propably, since my old xorg.conf didn\t work... Thinkin about just doing a fresh install since my xorg is broken anyway... 

But my mic works for the first time! Nice

EDIT I fixed the xorg.conf to use the nvidia driver instead of the nv. But then it didnt find my monitor. So I guess Ive lost my nvidia drivers:(
AND nvidia doesn\t show up in the restricted drivers !
EIDT 2: I tried envy, installed manually. But it didn't work. Had to change the sorg.conf driver back to nv (from nvidia). I got this to work under edgy, but now I don't get to use the nvida :( 

Any ideas?? Please help! I don't think this will be any different if I do a clean install, so I'd rather mess around now and find the right solution..

EDIT: the error I get is:
    ERROR: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but this X module has the version 1.0-9631...
(I got this the first time I started feisty as well as now after installing nvidia with envy ( I removed the old nvidia first) and then also when I tried to use nvidia through restricted drivers)

I'm starting to think I'll never get the nvidia drivers to work again. Cause my card (radeon geforce go7200) isn't suported. But I got it to work under edgy by some luck (I don't know what I did, it just suddently worked. Forced the install or something)

:sad:

---

### Post by olavjunior on 2007-05-08
I installed Feisty from scratch! Now my desctop-effekts work fine :) 
BUT my apps aren't there any more :-k 
I'm using my old home (altered the fstab), so that isn't the reason they're gone)

Is it really the case that I should keep my programs? Or is it just the settings I get to keep? 
(installed Opera again, and the settings were kept. That's nice, so reinstalling apps isn't really a big problem)

---

### Post by H.E. Pennypacker on 2007-05-10
My advice: do not upgrade if you have everything working for you now.  There are too many people complaining that an upgrade ruined something (sound, Internet, hibernation, suspend, etc.).  Again, you should not upgrade if you are happy with your current system.

A fresh install will remove all applications.  You will have to install them again.  The settings for some of the applications will still be there, because their settings are located on the /home partition (you still have the home partition).

You will need to re-install Beryl.  Make sure you go to [www.beryl-project.com](www.beryl-project.com), and follow their guide.  If you have any problems, please seee their messageboard.

---

### Post by strabes on 2007-05-10
If you're going to do a fresh install, make sure you don't format your home partition.

---

### Post by olavjunior on 2007-05-11
I'm very happy with upgrading to Feisty. Getting to clean some old mess up. Not going to install kde apps this time. And now my microphone works perfectly, I can easily use secured wireless networks, I got Beryl to work (not only Compiz). So as you see mr H.E. Pennypacker, for some it's nice to update the system :) I feel sorry for those guys getting into troubble thoug..

---

