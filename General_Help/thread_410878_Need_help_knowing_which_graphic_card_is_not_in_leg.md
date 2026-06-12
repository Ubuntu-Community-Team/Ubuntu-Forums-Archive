---
title: "Need help knowing which graphic card is not in legacy"
date: 2007-04-16
forum: General Help
---

### Post by Masterj15 on 2007-04-16
I have either 4 graphic cards or 3 two graphic cards and this other card. (Guessing a video adpter, I'm not sure.)

They are: 
Nvida  Riva Tnt2/tnt2 pro
Nvidia Riva 128ZX
Unknown cirrus logic cl-G0d5446-hc-a
Creative Ct7120
 
Nvidia Riva Tnt2/tnt2pro: It is wierd because the card says something about dimond viper and i have never seen the words tnt2/tnt2 pro before on the graphic card.

Nvidia Riva 128ZX: I tried putting it in my computer but it would not come on. My computer would make this weird sound and would not turn on the screen. I would be upset if this is a legacy ddriver card beacuse I paid this guy 190$ for this card and he said that it is new.

unknown cirrus logic cl-god5446-hc-a: This does not do good with ubuntu.

Creative ct7120: This i paid 250$ and never got it to work. Even when I had windows. 


I want to know if any of this are not legacy beacuse I have been trying to install beryl and the mesa does not support GLX_Pixmap_ Texture (Or something like) in a legacy card.

Thanks in advance for helping me out.:D

---

### Post by dpar on 2007-04-16
This page may help.....[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia?highlight=%28nvidia%29%7C%28legacy%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia?highlight=%28nvidia%29%7C%28legacy%29)

---

### Post by Masterj15 on 2007-04-19
That helped me to a certain degree but my main goal is to get beryl to work and they say I need a normal graphic card to work. I starting to think nothing works at all and it is just not possible for me to get beryl to work.:confused:

---

### Post by dpar on 2007-04-19
I'm using an FX5200 and Beryl runs fine on it. Those seem like pretty high prices for old cards. My card is pretty old too, but it only costs $52 new at ncix.com

---

### Post by Smuve on 2007-04-19
Peep this: [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html")

If you want something non-legacy, then it looks like you're going to have to go with a 5000 series or higher.  The riva's are definitely legacy cards.

---

### Post by Masterj15 on 2007-04-20
that is the weird thing. My nvidia riva zx128 is not up their any catgory. When I did find it for linux it said that it is used by the normal "nv" instead of changing the xorg.cinfig file to the uasull nvidia.

---

### Post by Smuve on 2007-04-20
Yea, I don't know how to describe it properly, but nv is kind of like a default or fallback driver for nvidia cards.  When I first install Ubuntu, my GeForce 6800 uses nv.  Then I have to install the real nvidia drivers.  nv works enough to get your GUI up and running, but it doesn't do any of the fun stuff needed to run beryl.

---

### Post by spankymasterc on 2007-04-20
dayum man u got ripped off those are old cards and are not worth what you paid for them... u could buy for the money you waster a new nvida 8800 series fuhh.... sorry for the non answer

i just bought a e-Geforce 7600 gt 256 gddr3 pci-e card for about 125 and its a pretty damn good card for its price.....

its Evga and its sli ready....

---

### Post by Masterj15 on 2007-04-23
Wow, I guess i'm going to have to buy any gefore or ati radoone or something like that. I just have one problem though. When I tried to put the nvidia128zx in their is force my bois. What do I do. I use to use nvidia riva tnt2/tnt2 pro but when I put that in that does not work also. Is it the bios? I don't think so beacuse I use a pci card that was like 20 years old and that worked. I might just have to buy a whole new computer. The problem is i'm a kid and don't a pay check at the end of two weeks like yiou guys. lol

---

### Post by lakersforce on 2007-04-23
Both your nvidia cards are supported by the legacy drivers.

---

### Post by Masterj15 on 2007-04-24
Thanks for telling me. I'm suck of a having a legacy card. I just want  Radons and geforces like other people.:(

---

### Post by jespdj on 2007-04-24
> **Masterj15 said:**
> ... The problem is i'm a kid and don't a pay check at the end of two weeks like yiou guys. lol
A good, normal ATI Radeon or nVidia GeForce video card (not the top-of-the-line 3D performance monsters) costs maybe $70 or so. Is that a problem? In your opening post you mentioned you paid $190 and $250 for some strange old video cards.

> **Masterj15 said:**
> Thanks for telling me. I'm suck of a having a legacy card. I just want  Radons and geforces like other people.:(
If you can afford to spend $190 + $250 for some strange old video cards then there is no reason why you are stuck with a legacy card. :confused:

> Nvidia Riva Tnt2/tnt2pro: It is wierd because the card says something about dimond viper...
"Diamond viper"? That reminds me of my video card that I had in my very first PC, a 386SX, 20 MHz (0.02 GHz!), with 2 MB (0.02 GB!) RAM and 40 MB (0.04 GB!) harddisk. That video card had 64 KB (not MB!) video memory. In other words, super-old and antique compared to today's computers. Cirrus Logic is another brand name from that era. I bought that PC in 1991.

---

### Post by lakersforce on 2007-04-24
> **Masterj15 said:**
> Thanks for telling me. I'm suck of a having a legacy card. I just want  Radons and geforces like other people.:(

nvidia cards up to (but not including) Geforce5 series (I believe it is officially called Geforce FX) are only supported in the legacy drivers.

You can get a Geforce 6200 for around 30$ these days. With this card you can pretty much get state-of-the art graphics for gaming.

---

### Post by Masterj15 on 2007-04-24
I'm just going to buy a radone or a gefore like everbody else.:)

---

### Post by Smuve on 2007-04-25
Nvidia will make your life easier with linux.

---

### Post by Masterj15 on 2007-04-26
Quote:
Originally Posted by Masterj15  
Thanks for telling me. I'm suck of a having a legacy card. I just want Radons and geforces like other people. 

If you can afford to spend $190 + $250 for some strange old video cards then there is no reason why you are stuck with a legacy card. 

At the time I had a job so it did not matter to me ebout money. It was when I moved to another state then that was the problrm but I have the money now and I'm going to but a geforce 6200 for gaming. Epscialy halo 2. LOL:)

---

