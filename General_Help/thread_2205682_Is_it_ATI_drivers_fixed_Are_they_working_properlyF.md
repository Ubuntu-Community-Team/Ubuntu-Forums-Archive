---
title: "Is it ATI drivers fixed? Are they working properly?First time user"
date: 2014-02-15
forum: General Help
---

### Post by craige2 on 2014-02-15
Hello all,

I want to install Ubuntu or Kubuntu. Never had them before, I tried the live cd, liked it and want to install either. I educated myself on youtube and forums about them. On December when I was about to install them, I saw a lot of problems with the ATI drivers, so I postponed the installation.

Yesterday and today, I was sniffing around to see the state of ATI drivers. I see they have release new stable and beta drivers.

Stable 13.12
Beta 14.1

Most of the forum posts I see, are referring to _*previous*_ releases of catalyst.

Could you give me an _*update*_ about the state of _*current*_ drivers please? Maybe if you got time to answer the following questions. Would be much appreciated.

1)Which one is the open source and which the prop? the one from Additional Restricted or from amd's site? Which one is preferable?

2)Which to install? 13.12 or 14.1? 

3)Are any of these working at all? Which one is better?

4)Any guides I found online to make them work, are for previous releases. Do the same steps apply to any of these versions?

5)I am between Unity 3d and Kubuntu. Considering my PC, which plays better with catalyst?

6)Would you advice me to install either of them at all(Kubuntu, Ubuntu), considering the state of catalyst? I don't want my PC to get high heated because of the drivers.


buying Geforce card is not an option atm.

I am a typical user, web surfing, youtube, skype, learning c and java at the moment. Maybe on a weekend could spend sometime with games on valve, like football manager or WoW. That would be all.

I do not mind if I have to give up gaming. Just considering the working state of PC under catalyst on linux. 


Spec:-

CrossfireX 2 x Radeon HD 6xxx
AMD Phenom 6 core 1100 TT
16 giga RAM
2 monitors, Samsung (hdmi) and LG (vga)
Gigabyte 990 UD3+ motherboard
Onboard sound card
2 TB hdd
Cooler Master Full Tower case


Sorry if there is a post answering these questions. I surfed a lot and got lost. Also apologise for long post.

Thank you in advance.

Best regards
CR

---

### Post by jp734 on 2014-02-15
Everyone's experience with the AMD video card is different. I, personally, did not have any problem getting the fglrx driver to work with my 2 HD 5xxx cards driving three monitors using **Lubuntu 13.10** with** kernel 3.11.0-15-generic**. No issues with over heating as well. I can't tell you a personal experience with either Ubuntu or Kubuntu as I like my OS simple and that will run on computers with low resource that's why I chose the LXDE version and installed Fluxbox :-)

You just have to take the leap. There will be plenty of help if you encounter any problems.

Good luck to you!

---

### Post by craige2 on 2014-02-15
Hello,

thank you so much for your reply. I followed your advice. I did the installation and I couldn't be more happy than I am. Things turned up way better than I thought and to be honest, feared!

If anyone has any problems and end up here with same questions and PC build, here is what I did:


Brand new install, only OS available, ubuntu 13.10
Fixed my software sources
update, upgrade, update through terminal (installed the kernel and headers etc that apt-get upgrade leave back)
Install the catalyst 14.1 - it is in beta state at the moment, via terminal
Reboot
Done

Only had to fix the scale for my hdmi screen through the catalyst centre.

Everything worked fine. No over heating, fans work as should be.

No laggy. I have no idea how the games will perform, but will take a while to check this out. I dont plan to go on gaming anytime soon.


Again thank you for reply.


_***Conclusion***_, catalyst 14.1 (beta at the moment), on crossfirex 2x Radeon HD 6870, works like charm on fresh installation.



Have fun,
CR

---

