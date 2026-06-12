---
title: "Grub Bootloader (I think)..."
date: 2008-04-29
forum: General Help
---

### Post by bucketmouse3001 on 2008-04-29
I'm not sure if this is the right forum, but here goes anyway. I have a problem, more of an annoyance really, but every time I've ever installed Ubuntu on any of my computers, I get a message just after I select Ubuntu to boot (I have a dual boot with XP) that says, "Starting..." and then tells me it found some BIOS bug (#81, I believe). Nothing is wrong with any of my installations. Everything runs perfectly. I just wish there was some way to get rid of that message popping up every time it boots. Is there a way to disable bug reports being displayed in grub or something? Thanks!

---

### Post by nicholas.Platt on 2008-04-30
I'm a bit of a newbie to the Linux scene, but you can find the Menu for the Grub boot loader in /boot/grub/menu.lst

That's a system file, so to actually make changes to it, you'll have to use the terminal, I believe. Something like this should do the trick:
```

cd /

sudo gedit /boot/grub/Menu.lst

```

Be careful though!
So far the only thing I've actually edited from that file is the timeout and alternate booting options, and only through the use of comments (#).

Good luck. :)

---

### Post by park8b156 on 2008-04-30
Use your windows OS for internet to get to Google search for super grub disk ISO image, burn it and restart just like you would for a live CD and hit enter when you see "Super Grub Loader" follow the prompts.  Remember to select the main hard drive and to select the windows/GNU Linux prompt that should do it. And as always read what the disk brings up on you screen it helps with future probs. DO NOT touch the grub menu unless you know what you are looking to accomplish with it.

---

### Post by bucketmouse3001 on 2008-05-01
I'm not having a problem booting at all, (in reference to your response, park) and I could find no options to do what I'd like in the Grub config. Any other suggestions, guys?

---

