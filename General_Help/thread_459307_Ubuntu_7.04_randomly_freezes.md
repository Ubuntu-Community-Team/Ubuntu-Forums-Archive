---
title: "Ubuntu 7.04 randomly freezes"
date: 2007-05-30
forum: General Help
---

### Post by DrSkeezix on 2007-05-30
I can run Ubuntu 6.06 non-stop, but as soon as I install 7.04, I get random freezes. Sometimes the mouse works, sometimes not, but nothing else. no HDD running or anything.

can happen after 2 hours or 2 seconds.

And I would like to use 7.04.

---

### Post by rodolfoarce on 2007-05-30
is it a standard ubuntu instalation?? describe the hardware, perhaps has something to do with that

Do you use an optical mouse (has it worked well with other operating systems)??

---

### Post by DrSkeezix on 2007-05-30
umm...  like i said, it works great with ubuntu 6.06.

even installing 7.04 is a pain. sometimes have to try it 2-3 times. different downloads as well. ran a cd check and all was fine.

running in a standard toshiba satellite laptop.

---

### Post by wpshooter on 2007-05-30
DrSkeezix:

I have 2 computers on which I can not get Feisty to install and work on properly.  Both of these computer install and run either Dapper or Edgy fine.

I have 2 other computers that are older than the first 2 on which I can install and run either Dapper, Edgy or Feisty.

I do not believe that Fesity is exactly ready form prime time.  This makes me wonder why they are working on another version (Gutsy) when it appears that Feisty is not yet finished !!!

Good luck.

---

### Post by rodolfoarce on 2007-05-30
Are there any aplcations or programs that you're using at the times of the freezing, it might be linked to some software perhaps

You could try to install from the alternate cd images or perhaps the server install and then completly upgrade the system to the standard ubuntu desktop.

had you tried the kubuntu or xubuntu.. maybe is just gnome

---

### Post by DrSkeezix on 2007-05-30
> **wpshooter said:**
> DrSkeezix:

I have 2 computers on which I can not get Feisty to install and work on properly.  Both of these computer install and run either Dapper or Edgy fine.

I have 2 other computers that are older than the first 2 on which I can install and run either Dapper, Edgy or Feisty.

I do not believe that Fesity is exactly ready form prime time.  This makes me wonder why they are working on another version (Gutsy) when it appears that Feisty is not yet finished !!!

Good luck.

well. at least i'm alone...  i could have sworn i ran fiesty a long time ago with no problems, but it's been to long for this old man...

i'll keep trying things. thanks for the heads up...

---

### Post by DrSkeezix on 2007-05-30
> **rodolfoarce said:**
> Are there any aplcations or programs that you're using at the times of the freezing, it might be linked to some software perhaps

You could try to install from the alternate cd images or perhaps the server install and then completly upgrade the system to the standard ubuntu desktop.

had you tried the kubuntu or xubuntu.. maybe is just gnome

no rhyme or reason. could click on applications and have it do it.

i've downloaded the live cd a few different times.

i'll be trying a few different things. see what happens. wanna get feisty working, darn it!

---

### Post by wpshooter on 2007-05-30
I tried both the DESKTOP and ALTERNATE and would not install and run properly from either.

I also tried installing directly from the burned CD of each version, desktop and alternate and also tried installing Edgy first and then upgrading it to Feisty and in all instances it does NOT work properly.

---

### Post by MichaelSM on 2007-06-01
Yeah. Hello. Problems here too. I don't burn my own discs, I get my CDs from OSDisc. I use a spare box for tests; it's a Pentium 550 with 256 RAM. Nothing much, but it ran either Dapper or Edgy like a treat. 
I got my new discs in the morning mail today and first off was to erase a hd with Edgy on it, and give Feisty a go. 
Anyway, to cut a long story short; of course I went straight to the updates link and there were 46 of 'em, about 71 megs. Alright, time to go down the street and let it all happen. Got back home expecting a near-finished download/install. Hmmm. No such luck. Clock stopped about 10 minutes into download. OK, reboot and try again.  Worse. Oh well, servers must be overloaded .....let's try something else I need. Dave Shuck's Java 6.0 download/install tutorial has always worked. Got the package, followed instructions, ok'd or yessed the terminal. That install froze up halfway; after watching the screen cycle through and dumping Firefox, Terminal, Evolution (which I didn't even have running at the time) I gave it a good 20 minutes to sort itself out, with the busy light on the box flickering happily. Too long. Stop this rubbish. WHAT? No mouse cursor?

I must say that I was underwhelmed. If that box is too slow, fair enough. I'll wipe it and try again in the morning, just in case it was a dodgy install(which has happened before). Perhaps I assumed without checking it out that Feisty would run on a box which easily handled Edgy.
Any ideas?
Cheers, Mike.

---

### Post by cprofitt on 2007-06-01
You guys make it sound like Feisty is worse than Vista. You are making me nervous to try it.

---

### Post by DrMega on 2007-06-01
What graphics card and driver are you using? There is a known issue with Radeon 7000 series graphics hardware that causes just such a random freeze.

The Radeon 7000 chipset also goes by the name of something like Radeon Mobility (when used in laptops) but is the same chipset and subject to the same bug.

I had exactly this problem, and did huge amounts of research before finding a bug report, and ultimately I bought a new graphics card.

To see if it is graphics card related, edit xorg.conf and change the graphics driver to VESA (back it up first). That will give you really crap graphics support with a horrible refresh rate, crap resolution and no acceleration but at least it will help you diagnose the fault, in that if the problem goes away then you know its graphics related.

---

### Post by MichaelSM on 2007-06-01
Hi again. And sorry to give you concerns, PrivateVoid. 
Re. my previous post. Look I dunno why it happens, but it does sometimes. A dodgy install which looks fine at first but can't cut the mustard. 
I just finished a complete wipe and re-install of Feisty, and it's excellent so far. 
I certainly like the codec download facility for Totem. 
The BlueTooth pairing with my Nokia was dead easy, having done it before in Edgy. From Synaptic download Obex, and Gnome BlueTooth. There's a little bit more to do but all easy.
By the way; this afternoon and evening I also had a crack at Gentoo 2007, Mandriva One Spring 2007, and MEPIS 2007. I think I'll just put them back in the box and forget I ever got them.....
Not that matters to anyone on this forum.
Can't wait for Ubuntu Studio. Monday's mail!
Cheers, Mike.

---

