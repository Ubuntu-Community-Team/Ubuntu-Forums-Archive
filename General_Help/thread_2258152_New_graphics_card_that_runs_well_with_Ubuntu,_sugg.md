---
title: "New graphics card that runs well with Ubuntu, suggestions?"
date: 2014-12-25
forum: General Help
---

### Post by petermartin2 on 2014-12-25
I have been trying to find out why my Ubuntu installation crashes and from what I can gather it probably has to do with my Radeon videocard. I have been trying to fix it with different updates and reinstall etc but it keeps crashing every few hours, particularly when I'm working in browsers. So now I am thinking of a GeForce and would like to know if anyone has had experiences with GeForce and Ubuntu. 

Or if there is some videocard that works really well with ubuntu that I should get. The most important thing is really that it works well with Ubuntu because it's my first operating system

---

### Post by flaymond on 2014-12-25
Try Lubuntu or Xubuntu, it fit well on my PC.

---

### Post by buzzingrobot on 2014-12-25
If your system has onboard Intel video in addition to the Radeon, switch to it in the BIOS and see if you like it. Intel video is well supported in Linux, the drivers are open-sourced and provided in a default install. Not the best for serious gaming, video editing and the like, but just fine for all the rest.

---

### Post by coffeecat on 2014-12-25
Just referring to a card as “radeon” or “geforce” doesn’t really help. There are many different radeon and geforce cards released over the many previous years and to be able to decide whether your card may be responsible for the system crashes you need to tell us which one it is, and which driver you are using. Similarly, to be able to decide whether there is a better card suitable for your needs, we need to know the specifications of the machine you are using and what you use it for.

For example, I use a Radeon HD 6450 card with the default open source driver in Ubuntu on my main machine, and this combination serves my particular needs more than adequately. It gives me glitch free high definition video viewing from Netflix, or from saved video files played in vlc or smplayer, but it wouldn’t be much good for gaming, which doesn’t interest me anyway. A gamer would choose a more powerful card and would use the proprietary driver. Whether they would choose a later model AMD Radeon or a Nvidia Geforce I have not the experience to tell. 

So – which radeon card are you using? Which driver?
Specifications of your machine?
Do you game or not? 

The other thing to remember is that system crashing may have causes other than the video card.

---

### Post by petermartin2 on 2014-12-25
> **coffeecat said:**
> Just referring to a card as “radeon” or “geforce” doesn’t really help. There are many different radeon and geforce cards released over the many previous years and to be able to decide whether your card may be responsible for the system crashes you need to tell us which one it is, and which driver you are using. Similarly, to be able to decide whether there is a better card suitable for your needs, we need to know the specifications of the machine you are using and what you use it for.

For example, I use a Radeon HD 6450 card with the default open source driver in Ubuntu on my main machine, and this combination serves my particular needs more than adequately. It gives me glitch free high definition video viewing from Netflix, or from saved video files played in vlc or smplayer, but it wouldn’t be much good for gaming, which doesn’t interest me anyway. A gamer would choose a more powerful card and would use the proprietary driver. Whether they would choose a later model AMD Radeon or a Nvidia Geforce I have not the experience to tell. 

So – which radeon card are you using? Which driver?
Specifications of your machine?
Do you game or not? 

The other thing to remember is that system crashing may have causes other than the video card.
Hello I am right now trying to find [COLOR=#000000]onboard Intel video in the bios but haven't been able to locate it yet. Seeing as it is in bios I guess it will be used in my windows boot as well if I don't change it every time I boot in the different OS?

I do game in my windows boot occasionally, this is the only time I boot in windows maybe 5h a week or something all other things I want to do in ubuntu only. I've had a number of problems with my 1 gb radeon HD7770 card with ubuntu. I can't get compiz to work for example and have found a lot of threads and fixes for this but nothing has worked for me. Also there are threads and fixes about crashes when using browsers but it's still crashing every few hours.

Basically what I want to do is be able to game on the windows boot and do everything else in ubuntu, that includes looking at video in good quality and maybe some editing and of course avoid crashes. Considering how much problems there seem to be with my card I would rather just have a card that works better in general with ubuntu?[/COLOR]

---

### Post by petermartin2 on 2014-12-25
> **InterProg said:**
> Try Lubuntu or Xubuntu, it fit well on my PC.
Thanks, I've been looking at xubuntu actually as a last resort if I can't get ubuntu stable. I'm getting used to fiddling with ubuntu but I guess xubuntu would be much the same

---

### Post by petermartin2 on 2014-12-26
I'm still interested in which cards that work well with Ubuntu. I'm still experiencing huge problems with [COLOR=#000000]radeon HD7770. There's a big library of posts in a number of different ubuntu forums about this card. Last night I reinstalled the OS for the fourth and fifth time trying to battle the problems. The last time it bugged out and crashed at the login screen every time I restarted. Now I've managed to remove the login.[/COLOR] The default software for the card acts as follows:

a) if installed with swap the crashes freezes the whole system every few hours
b) if installed without swap the system wide crashes dissapears but is replaced by apps crashing constantly 

No matter if with or without swap a lot of compiz functions are not working properly. For example I can not use desktop cube. [COLOR=#000000]The drivers from AMD leaves the screen totally black at startup the pack from software center is extremely buggy and[/COLOR] has so low rating that it's not a recommended install. If anyone is not experiences these errors could you please tell me which card you are using? I just want a card that is running smoothly with Ubuntu 14.04, 14.10.

---

### Post by petermartin2 on 2014-12-26
I'm looking at NVidia for example their driver packs in software center all have average to high rating, are they any good?

---

### Post by buzzingrobot on 2014-12-26
I imagine it's going to be close to impossible to find a universal fits-everyone graphics card recommendation.  Far too many variables: Different hardware, different versions of Ubuntu, different software mixes and demands, etc. Lack of source for the proprietary Nvidia/AMD drivers mean kernel updates can throw a working  driver on a given system for a loop, and the fix has to come from Nvidia/AMD after the fact. Vendors may make subtle changes to their cards that bear the same model name and number of the Nvidia or AMD reference model.

Recommendations and advice given online often leave a lot unsaid.  People use different installation methods, jump from one method to another without cleaning out the detritus from the previous attempt.

I don't game and I don't make any heavy video demands on my system, so for a long time I've routinely used Intel video without a problem. If I did use Nvidia/AMD, I'd first opt for the open source drivers.  If I did need to use the proprietary drivers, I'd only install/remove them via the Additional Drivers feature in Ubuntu.

---

### Post by petermartin2 on 2014-12-26
> **buzzingrobot said:**
> I imagine it&#39;s going to be close to impossible to find a universal fits-everyone graphics card recommendation. Far too many variables: Different hardware, different versions of Ubuntu, different software mixes and demands, etc. Lack of source for the proprietary Nvidia/AMD drivers mean kernel updates can throw a working driver on a given system for a loop, and the fix has to come from Nvidia/AMD after the fact. Vendors may make subtle changes to their cards that bear the same model name and number of the Nvidia or AMD reference model. Recommendations and advice given online often leave a lot unsaid. People use different installation methods, jump from one method to another without cleaning out the detritus from the previous attempt. I don&#39;t game and I don&#39;t make any heavy video demands on my system, so for a long time I&#39;ve **routinely used Intel video without a problem**. If I did use Nvidia/AMD, I&#39;d first opt for the open source drivers. If I did need to use the proprietary drivers, I&#39;d only I 
  	I have checked up on my CPU and it does have integrated graphics and I would very much like to try it. Unfortunately my motherboard dosen&#39;t support bios it only has the UEIF thing and I have looked through it but can not find any option to chose to run graphics from intel CPU could you tell me how I could do this? What should I look for?

---

### Post by buzzingrobot on 2014-12-26
> **petermartin2 said:**
> I have checked up on my CPU and it does have integrated graphics and I would very much like to try it. Unfortunately my motherboard dosen't support bios it only has the UEIF thing and I have looked through it but can not find any option to chose to run graphics from intel CPU could you tell me how I could do this? What should I look for?

It's usually in BIOS/UEFI settings under 'Video' or something similar. It may not specifically say "Intel", or it may call it "internal" or something similar, but will call it something that distinguishes it from the separate Radeon card, which may be called "discrete" or something like that. 

If you're working with a desktop, the output for onboard Intel is typically different than the discrete card. For example, the Intel may use a DisplayPort connection while a discrete card may use DVI or HDMI, or vice versa.  Before you switch, you'll need the right cable, of course. Don't forget to switch the monitor from whatever port the Radeon uses to the port the Intel uses, otherwise nothing will display, including BIOs/UEFI settings.(I usually connect the cable first, then switch switch video settings in BIOS.  When the machine reboots, the monitor is black and complains it doesn't have a video connection.  I switch the monitor video settings to the right port and all is well.)

---

### Post by petermartin2 on 2014-12-29
I'm running Ubuntu on intelgraphics until I get a new video card

---

