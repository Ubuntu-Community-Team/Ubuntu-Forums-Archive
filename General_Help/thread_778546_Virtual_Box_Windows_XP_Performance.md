---
title: "Virtual Box Windows XP Performance"
date: 2008-05-02
forum: General Help
---

### Post by ade234uk on 2008-05-02
I am thinking of installing Ubuntu as my main OS and running XP in Virtual Box.

Just a couple of questions
I have 4GB of ram and an Intel Core 2 Duo processor, will Ubuntu recognise the full 4GB, do I need to download and install the 64 Bit version for this?

As regards running Windows XP in Virtual Box, I do quite a bit of work in PhotoShop, will the performance of this suffer?

I have always had Ubuntu on a seperate box. I just want everything in one place.

---

### Post by posterberg on 2008-05-02
I am quite sure that you won't see all the 4 gig of RAM even with the 64 bit install unless your hardware architecture is 64 bit. This is sadly a fact since it isn't possible to address more memory than exactly 4 gigs on a 32 bit system.

You graphics board are likly to consume 128, 256 or more of this 4 gig address space, soundcard even some etc... Maybe you'll be able to use about 3 gigs of those 4 precious gigs. Sorry, I just experience the same thing just a few weeks ago...

Anyways, Virtualbox does perform really well unless you are going for 3d and directx...

So 2d and no games will work. I can hardly see the difference in the apps I am using. I can not give you any hint on Photoshop, I haven't tried that one...

---

### Post by shad0w_walker on 2008-05-02
You should be able to run the 64bit release and use the full 4Gb, I can (And would) use the 64bit version to get the full 4Gb in user but I choose not to for various reasons which are probably all fixed by now but I'm comfortable with how I've tweaked my install and can't be bothered to move now.

As for performance in virtual box, the easiest way to see would be to give it a try, however from my experience Virtualbox gives extremely good performance for most things. If you are running Photoshop CS2 or earlier then you might be better off using Wine since Google sponsored a fix to get upto CS2 working properly in Wine.

---

