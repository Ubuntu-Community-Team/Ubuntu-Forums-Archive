---
title: "[SOLVED] Live CD lockup"
date: 2007-07-05
forum: General Help
---

### Post by ninja_in_pajamas on 2007-07-05
I'm trying to run the Kubuntu Live CD.  I do not want to install it just yet because I wouldl ike ot test drive it a little.  The live cd starts to load.  I get the first splash that has boot options, then it shows a little text.  After that I get the main splash butafter that it becomes a black screen with a little ticker in the top left corner.  I'm using a Dell inspiron E1505 laptop with a gig of ram, 120 gig hard drive, and ati radeon m1400.  I have ran with quiet splash turned off and get no errors of any kind.  I have also tried in safe graphics mode.  Currently I suspect Kubuntus poor ATI driver support since I had a lot of graphics problems on my ubuntu install I have now.

Any known fixes for this?

UPDATE: Okay, the problem is definately the graphics card.  Have two computers that have identical configurations except for the video cards.  One has ATI, the other has Nvidia.  It works on the Nvidia machine but not the ATI machine.

Anyone have any ideas?

---

### Post by forgreatsource on 2007-07-05
what version of kubuntu is it?
in safe graphics mode it should work.

---

### Post by ninja_in_pajamas on 2007-07-06
It's the release that is on the website.  Feisty Fawn.  Tried safe graphics mode and it doesn't work either.  That is another reason why I think it is due to the graphics drivers.  Feisty is notorious for having issues with ATI cards and I have one of the problematic cards, a radeon mobility 1400.  I had a similar problem with the regular ubuntu version of feisty but on it I got an xorg error where on Kubuntu I just get a blank screen at the point where I should see the background and what services are starting up.

UPDATE: Tried with safe mode once more to make sure.  No luck.  Tried again in the normal mode with quiet splash turned off and got no visible errors.  After lockup I tried ctrl-alt-del and it did a normal shutdown with the shutdown splash and everything.  Tried once more but instead of ctrl-alt-del I tried startx.  Got and xorg error.  The picture of the error and what info was shown currently on the screen can be found [here]("http://picasaweb.google.com/tony.dorr/UbuntuKubuntuErrors/photo#5084140313069474530")

---

### Post by john8791 on 2007-07-08
I have the same problem, except with an ATI Radeon X1300 in my E1505.  Tried everything I can think of and still doesn't boot.

---

### Post by john8791 on 2007-07-08
One more thing... It boots fine with the Slax and Fedora live CD's.

---

### Post by ninja_in_pajamas on 2007-07-08
I'm not calling this solved by a longshot because there is still an issue with the Live CD.  But I went ahead and took the plunge and changed Ubuntu over to Kubuntu and I love it.:lolflag:

---

### Post by jynyl on 2007-07-26
There is a post on this thread that may help ...
[http://ubuntuforums.org/showthread.php?p=3082767]("http://ubuntuforums.org/showthread.php?p=3082767")

---

