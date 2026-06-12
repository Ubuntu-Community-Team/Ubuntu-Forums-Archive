---
title: "SystemRescueCD"
date: 2007-05-21
forum: General Help
---

### Post by merlinus on 2007-05-21
No matter what parameters I enter on the boot line, when everything loads and I reach a system prompt, startx results in a bunch of colored lines on a half-screen purple background and nothing else.

Ctrl-Alt-F2 gets back to the CLI, but this basically makes the disk unusable for anything except a very few things.

Any ideas or suggestions?

Many thanks!

-merlin

---

### Post by MoLE on 2007-05-29
Hi Merlin,

My first suggestion would be to check the integrity of the CD.  What hardware are you trying to run it on?  You may be able to specify a different video driver for X that may work.  Also there are forums for systemrescue CD found [here]("http://www.sysresccd.org/forums/index.php?sid=f99aeab3291bc208e32cf178ee5f8ea1").
They may be in a better position to help you than the ubuntu community.

---

### Post by merlinus on 2007-05-29
Hi, and thanks for your response.

I tried every one of the boot suggestions, to no avail.  And posting on the systemrescuecd forum did not bring any responses.

Even the forcevesa argument on bootup did not work, and that is the driver ubuntu is using for my installation.

-merlin

---

### Post by liberalist on 2007-05-29
I had a similar problem with Feisty Fawn, because I have an ATI Radeon video card. The solution might be to install Feisty Fawn from an Alternate Install CD.

if that doesn't help, I would advise you to install Ubuntu 6.06 LTS (Dapper Drake, which worked fine on my computer). Again an alternate install CD or the DVD option. Burning the CD on 4x speed might make a better disc (I read this somewhere in Ubuntu's documentation). Again, check the disc for integrity. 

Good luck and I hope you haven't lost any important documents and other files. Let us know if you have any other questions or problems.

---

### Post by merlinus on 2007-05-29
Thanks for your response, but I was only referring to the SystemRescueCD from [http://www.sysresccd.org/](http://www.sysresccd.org/)

I had -- and -- have no problems with Feisty, other than having to manually edit some files due to the recent kernel upgrade.

All the best....

-merlin

---

