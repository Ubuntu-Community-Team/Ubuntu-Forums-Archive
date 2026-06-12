---
title: "help with divx"
date: 2008-01-30
forum: General Help
---

### Post by tisa on 2008-01-30
hi all,
i'm new on linux, so i'll try to explain my best the problem. Actually i'm using gutsy, my graphic card is an ati. I don't know why divx doesn't play well on this computer, it's choppy, and the same film on windows goes well. does anybody know where could be the problem?
thx

---

### Post by jleaker01z on 2008-01-30
What drivers are you using for your graphics card?  By far the easiest and best method is a program called 'envy'

---

### Post by tisa on 2008-01-30
actually i'm using the ati restricted drivers. but i don't remember which version, i think I installed them a month ago.

---

### Post by jleaker01z on 2008-01-30
Go to system>administration>restricted drivers manager

Uncheck the box beside your card

Install envy: [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb)

Run envy (will be under applications>system tools

Choose 'install ati driver'

Restart X (ctrl+alt+backspace)

See if that helps

---

### Post by tisa on 2008-01-30
first of all thnx for this program, it's awesome, it does everything in one moment, if i knew it before i wouldn't have had so many headaches with those drivers.
The problem is that even reinstalling the drivers seems that it still doesn't work. i've played it again and it doesn't work. I've observed that if I play it without full screen mode works moreless well, but in full screen mode it's awful. i've tried with so many players and it's all the same. any idea?

---

### Post by jleaker01z on 2008-01-30
System>Administration>Screens and Graphics

Check to see if your monitor (screen) setting is correct.  Beyond that, I dunno...I really thought that the good drivers would help...

---

### Post by confused57 on 2008-01-30
> **tisa said:**
> first of all thnx for this program, it's awesome, it does everything in one moment, if i knew it before i wouldn't have had so many headaches with those drivers.
The problem is that even reinstalling the drivers seems that it still doesn't work. i've played it again and it doesn't work. I've observed that if I play it without full screen mode works moreless well, but in full screen mode it's awful. i've tried with so many players and it's all the same. any idea?
You might need to install proprietary software/codecs:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by tisa on 2008-01-31
Nothing, still with the problem. i've installed the restricted extras and I still have the same problem. When I play it the cpu goes to 100%, it's like it doesn't use the graphic card. any idea?
thx for your time

---

### Post by confused57 on 2008-01-31
> **tisa said:**
> Nothing, still with the problem. i've installed the restricted extras and I still have the same problem. When I play it the cpu goes to 100%, it's like it doesn't use the graphic card. any idea?
thx for your time
I'm not sure what's going on, maybe a graphics card driver issue...have you tried mplayer, that you can install from Synaptic Package Manager?

---

### Post by tisa on 2008-01-31
yes, and everything is the same. i've searched a little throught thtis forum and so many people has the same problem with divx and ati. i'll try if with another graphic card happens the same. thx for all.

---

### Post by confused57 on 2008-01-31
> **tisa said:**
> yes, and everything is the same. i've searched a little throught thtis forum and so many people has the same problem with divx and ati. i'll try if with another graphic card happens the same. thx for all.
Sorry it didn't work...I've always used Nvidia cards & haven't had any problems playing DivX movies.

---

