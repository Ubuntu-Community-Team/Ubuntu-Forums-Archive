---
title: "Xgl works in Kororra and SLED but not in Ubuntu"
date: 2006-08-16
forum: General Help
---

### Post by djsamsel on 2006-08-16
i love ubuntu and want to stick with it. however, on my laptop Xgl will not work in Ubuntu and yet it runs perfectly in kororaa and sled. it's a dell d820 with nvidia nvs 120. any suggestions will be appreciated. in xgl i get artifacts on icons or menu's that i click and there are no window bars. the cube works fine. i've followed the install in wiki and used automatix bleeder. both give the same results. help me keep my ubuntu.

---

### Post by yeehawjared on 2006-08-25
I have the EXACT same problem as you.  I have a dell inspiron 9300 laptop and am still having problems with my XGL setup.  I used automatixbleeder which worked OK, then followed another guide.  XGL runs fine but has lots of jaggies and stuff.  I also can't move any windows.  The expose f12 thing works flawlessly... but once again the icons all go jaggy and i can't move any windows around.

Did you figure out what's going on?  I have a nvidia Go 6800  Thanks,

---

### Post by David Corrales on 2006-08-26
I have an Inspiron 9300 with the Ati x300 and it's useless :( lots of glitches and horrible performance.

---

### Post by Metroid48 on 2006-08-26
Try this site:

[http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/](http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/)

It worked well for me. Only one thing, if you have an Intel or NVidia card, where it says xv:pbuffer, replace it with xv:vbo.

---

### Post by djsamsel on 2006-08-26
i have given up on ubuntu and just stuck with sled for the last few weeks. i love the community around ubuntu, but i was spending a ton of time trying to to make it work. if one of you get's it working, please post that you did and how you did. i'd love to return, but don't have the time to figure it out (i spent at least 8 hours on irc working on this and got nowhere)

---

### Post by Metroid48 on 2006-08-26
What's your graphic card?

The guide works flawlessly for me (except you HAVE to put xv:vbo).

I'm running an Inspiron 6000 with an Intel Mobile graphic chipset. I've heard it works just fine with Nvidia, I have no clue about ATI though.

---

### Post by djsamsel on 2006-08-26
nvidia nvs120

---

### Post by yeehawjared on 2006-08-27
yeah I've been putting in 2+ hours for the last week trying to get XGL to work flawlessly.  It sucks that I'm so close.  I've tried just about everything.  I think I may re-install and start from scratch... or move to SLED10 :(  

If I give up now all that time wasted will have been in vain #-o

---

### Post by djsamsel on 2006-08-27
gotta tell ya. sled is pretty slick. adding quinns repo's is a snap, and at least for me, on both my laptop and my desktop, xgl just worked out of the box. in fact, everything worked oob. good luck. like i've posted, i love the ubuntu community, but a free distro was costing me a ton of time.](*,)

---

### Post by yeehawjared on 2006-08-28
I'm going to try SLED tonight... too bad SLED10 is $50 a year :(

---

### Post by djsamsel on 2006-08-28
opensuse is 99% of what sled is. once 10.2 is released it will be as good or better. good luck. hopefully they will get ubuntu straightened out soon. you really can't find a better forum or group of people willing to help.

---

### Post by skymt on 2006-08-28
Really? You're switching to a paid distro (with an annual fee, at that) for the *eye candy??*

](*,) 

Please get over it. It's a beta for a reason. Wait for AIGLX+Metacity in Edgy (or Edgy+1).

Sorry for the tone, but I'm really sick of XGl. It's great, really. I'm going to use it *once it's usable*. As long as it takes a crummy collection of hacks to even get it to run (witness the fact that most HOWTOs use a shell script that uses the killall command), I'll stick with normal Xorg.

---

### Post by yeehawjared on 2006-08-28
FINALLY got it to work.
[http://doc.gwos.org/index.php/XGL_Compiz%2832bit%29Nvidia](http://doc.gwos.org/index.php/XGL_Compiz%2832bit%29Nvidia)

followed that guide, changed my xorg.conf to 24 bit and bingo.
I have an Nvidia Geforce Go 6800.

and yeah, i'd never pay 50 a year for a linux distro when there's ubuntu and countless others.

---

### Post by djsamsel on 2006-08-29
skymt, yeehaw, i totally understand your position. like i said, i really love the community and i think ubuntu is a great product. i'm not trying to tell you to leave for sled, but for others who are having problems with ubuntu i suggest rather than leaving linux, they give another distro a try. i have a desktop with an asus mb and amd x2 processor that wont even let me boot or install ubuntu. i've posted all over the place looking for help, but nothing has worked. for consistency, i want both computers to use the same distro. sled and opensuse run very smoothly on both. i got to the point that the amount of time i was spending to configure and get ubuntu working was worth more that $50 a year, even if i only made minimum wage. so, i opted for sled. i continue to read the forums and look for answers and hope to eventually come back to ubuntu, until then sled "just works" for me.

---

### Post by yeehawjared on 2006-08-29
sucks that your mobo isn't supported / doesn't work out of the box... have you tried xubuntu?  has better legacy support, but that motherboard is new.  wish i could help man :(

---

### Post by skymt on 2006-08-29
Okay, I didn't read properly. If you were switching exclusively for eye candy, that would be pretty stupid.

Well, good luck with that. Give Edgy a shot when it comes out, maybe it'll work out better for you.

---

### Post by David Corrales on 2006-09-02
> **djsamsel said:**
> skymt, yeehaw, i totally understand your position. like i said, i really love the community and i think ubuntu is a great product. i'm not trying to tell you to leave for sled, but for others who are having problems with ubuntu i suggest rather than leaving linux, they give another distro a try. i have a desktop with an asus mb and amd x2 processor that wont even let me boot or install ubuntu. i've posted all over the place looking for help, but nothing has worked. for consistency, i want both computers to use the same distro. sled and opensuse run very smoothly on both. i got to the point that the amount of time i was spending to configure and get ubuntu working was worth more that $50 a year, even if i only made minimum wage. so, i opted for sled. i continue to read the forums and look for answers and hope to eventually come back to ubuntu, until then sled "just works" for me.

Hooray for choices :D Good luck with SLED man, it's a slick distro. The only thing I don't like is Yast and rpm's lol. But it's very polished and worth the $50.

---

