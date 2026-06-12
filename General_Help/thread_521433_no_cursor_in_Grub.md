---
title: "no cursor in Grub"
date: 2007-08-09
forum: General Help
---

### Post by sarahdavies22 on 2007-08-09
I am an absolute beginner here but today finally managed to run an application in a terminal window - a grub editor which I found on this site. I wanted to increase the time on my menu as I have a disability and couldn't use the keyboard quickly enough to run Windows before Unbuntu started. 

I set up the background colour, text colour etc, but foolishly chose Windows as the default OS. 

My new menu now appears on booting up,  but there is no cursor or numbers with which to make a choice, so I can't boot Unbuntu now - disaster. I often get a long run of text, then cursor and a very fast annoying keyboard speed, but can't get anywhere from there. 

If anybody could advise me, I'd be very grateful. 

Thanks
Sarah

---

### Post by apetresc on 2007-08-09
> **sarahdavies22 said:**
> I am an absolute beginner here but today finally managed to run an application in a terminal window - a grub editor which I found on this site. I wanted to increase the time on my menu as I have a disability and couldn't use the keyboard quickly enough to run Windows before Unbuntu started. 

I set up the background colour, text colour etc, but foolishly chose Windows as the default OS. 

My new menu now appears on booting up,  but there is no cursor or numbers with which to make a choice, so I can't boot Unbuntu now - disaster. I often get a long run of text, then cursor and a very fast annoying keyboard speed, but can't get anywhere from there. 

If anybody could advise me, I'd be very grateful. 

Thanks
Sarah
Uh oh :( It seems you've messed up your menu.lst file a bit (it's the configuration file for GRUB). But no worries, this is very fixable! Since you can't boot into Linux anymore, you will have to boot into a LiveCD and modify it from there.

First things first. Boot into a LiveCD, mount the hard drive that has Ubuntu installed on it, and show us the contents of the "/boot/grub/menu/lst" file *of that drive*.

---

