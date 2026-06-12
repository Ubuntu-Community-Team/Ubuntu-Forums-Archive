---
title: "How long before a stable release of Beryl"
date: 2007-02-07
forum: General Help
---

### Post by tacm on 2007-02-07
I am very interested in learning about this, but everthing i have read has basicly said NOOBS beware.  I have been useing 6.06 for a couple weeks it is the first time I have used Linux, I learn a little more every day, but for once Im not jumping in with both feet.  The warnings have worked.  Sould I wait for a better relese?  Sould I wait until my Linux skills improve?  Any advice would be great.

---

### Post by wh0rd on 2007-02-07
Tomorrow!

:P, j/k... 

why don'tcha post it on the beryl forums: [http://forum.beryl-project.org/](http://forum.beryl-project.org/)

---

### Post by r4ik on 2007-02-07
Skills improve by practice.
As long as you're important data is safe.

Good luck !

---

### Post by thelocust on 2007-02-07
[B]sorry bad post.
[/B]

---

### Post by Naegling23 on 2007-02-07
I would recommend running beryl on edgy, all the install needs is to add a repository.  There are a couple of tweaks on top of it, but its very easy.  I installed compiz as a noob on dapper, and I have to say that beryl on edgy is very easy.

If you want to wait, when feisty comes out, there should be compiz or beryl support built into it, so you wont need to install anything really.

---

### Post by reclusivemonkey on 2007-02-07
> **tacm said:**
>  Any advice would be great.

A lot depends on your graphics card. What do you have?

---

### Post by tacm on 2007-02-07
> **reclusivemonkey said:**
> A lot depends on your graphics card. What do you have?

ATI Radeon XPRESS 200M 5955 (PCIE)

---

### Post by john.nicholls on 2007-02-08
If you have enough hard disk space, I'd suggest setting up another partition and installing Edgy plus Beryl on it. Then you can play around with it and leave your working system untouched. This is what I'm using at the moment.

John

---

### Post by reclusivemonkey on 2007-02-08
> **tacm said:**
> ATI Radeon XPRESS 200M 5955 (PCIE)

From what I understand, ATI cards can be tricky to set up with Beryl, and you don't get the same performance as with a NVIDIA card. I would hold off for a while, although YMMV. Have a look on the forums for ATI+Beryl.

---

### Post by xxrealmsxx on 2007-02-09
> **tacm said:**
> ATI Radeon XPRESS 200M 5955 (PCIE)

[http://www.ubuntuforums.org/showthread.php?t=321766&highlight=beryl+200m](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=beryl+200m)

and

[http://www.ubuntuforums.org/showthread.php?t=341149&highlight=beryl+200m](http://www.ubuntuforums.org/showthread.php?t=341149&highlight=beryl+200m)

got it working for me on an hp pavillion zv6000 w/ the 200m 128mb video card.

However, this latest update killed my beryl and it won't work.

I am sure the next update will fix it though so i'm just going to wait.

---

### Post by aldenhg on 2007-02-09
My experience with Beryl + ATI has been pretty painless on Edgy. I ran a script I found somewhere (I'll attach it at the end) and then set up my session to load beryl-manager at startup (System -> Sessions -> Startup Programs -> Add -> type in beryl-manager). Now if I want Beryl I just open a terminal and run beryl. I haven't had any problems, except that since you need the open source drivers to run AIGLX and they don't support GL_ARB_fragment you can't use Blur or Water. C'est la vie. BTW, this is on a Radeon 9800 Pro.
I really can't remember where I found this script, so I'm assuming it's all GPL'd and all that. I'm not in any way trying to take credit for it and if anyone knows who the original author is please enlighten me and the rest of us. Also, I think that this script is best run on a spankin' new installation, so use at your own risk and your mileage may vary. There are better guides here in the forums and in the Wiki, so if this seems at all daunting to you check the other sources out first. I'm by no means an expert.

---

