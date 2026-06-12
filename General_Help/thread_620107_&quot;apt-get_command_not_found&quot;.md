---
title: "&quot;apt-get: command not found&quot;"
date: 2007-11-22
forum: General Help
---

### Post by LIJI on 2007-11-22
Hello,
I'm a dual-boot user with Ubuntu and Windows XP.
Lately, my Windows XP OS "broke", and I used Ubuntu with the NTFS driver and the Windows XP boot CD to fix it.
However, After inserting the XP Boot CD, Booting to Linux results in a fschk Error 4 and a "apt-get: command not found" error that asks me to do apt-get apt (Which obviously doesn't work), although Ubuntu worked fine minutes before I did.

Meanwhile I can't boot to Ubuntu and reformatting will be to much afford as it took me ages installing all these drivers.

Can anyone tell me how to solve this problem?

Thanking in Advance,
LIJI

---

### Post by kshane on 2007-11-22
> **LIJI said:**
> Hello,
I'm a dual-boot user with Ubuntu and Windows XP.
Lately, my Windows XP OS "broke", and I used Ubuntu with the NTFS driver and the Windows XP boot CD to fix it.
However, After inserting the XP Boot CD, Booting to Linux results in a fschk Error 4 and a "apt-get: command not found" error that asks me to do apt-get apt (Which obviously doesn't work), although Ubuntu worked fine minutes before I did.

Meanwhile I can't boot to Ubuntu and reformatting will be to much afford as it took me ages installing all these drivers.

Can anyone tell me how to solve this problem?

Thanking in Advance,
LIJI

I would suggest you first get Ubuntu booting again.  The easiest way to do this is to use **Super Grub** to fix your boot troubles.  

Once that is done, I would suggest using "Aptitude" for your installations and, perhaps, to re-install apt-get....

Kevin

---

### Post by shavenlunatic on 2007-11-22
> **LIJI said:**
> Hello,
 asks me to do apt-get apt

shouldn't it be "apt-get install apt" ?

just a thought (it's usually best to ignore my thoughts though)

---

### Post by kshane on 2007-11-22
> **shavenlunatic said:**
> shouldn't it be "apt-get install apt" ?

just a thought (it's usually best to ignore my thoughts though)

:)

aptitude is very similar to apt-get, so, no, it should be aptitude install apt-get, I believe.

But, I would probably use Synaptic, instead, now that I think about it...

Kevin

---

### Post by shavenlunatic on 2007-11-22
> **kshane said:**
> :)

aptitude is very similar to apt-get, so, no, it should be aptitude install apt-get, I believe.

But, I would probably use Synaptic, instead, now that I think about it...

Kevin

no, i know the differnces (or lack of them) between apt and aptitude.. I was just replying to his initial comment and wondered if the apt-get (or even aptitude.. ) command was being used correctly as he stated is said "apt-get apt" rather than "apt-get install apt" or "aptitude install apt"

anyway.. you make sense... . use synaptic if it works :)

---

### Post by LIJI on 2007-11-22
I'm not a too advanced Linux user, and I generally suck at command line modes of all types too. ;)

Which commands should I user to reinstall Apt from Synaptic?

---

### Post by shavenlunatic on 2007-11-22
just go into synaptic.. search for apt.. right click on the relevant package and mark for re-installation (or remove and reinstall.. whichever.. I'm on an XP machine at work right now so I can't check)

---

### Post by LIJI on 2007-11-22
It's not that easy, I'm stuck at commandline. ;)

---

### Post by shavenlunatic on 2007-11-22
right.. type either

```
sudo aptitude remove apt
sudo aptitude install apt

```

should get u there (i reckon if apt is ****** then apt won't re-install apt.. dunno though.. try replacing the word aptitude with apt-get if the first thing doesn't work

---

### Post by kshane on 2007-11-22
> **shavenlunatic said:**
> no, i know the differnces (or lack of them) between apt and aptitude.. I was just replying to his initial comment and wondered if the apt-get (or even aptitude.. ) command was being used correctly as he stated is said "apt-get apt" rather than "apt-get install apt" or "aptitude install apt"

anyway.. you make sense... . use synaptic if it works :)

Ahhh!  <seeping through the density>  Sorry...

---

### Post by kshane on 2007-11-22
> **LIJI said:**
> It's not that easy, I'm stuck at commandline. ;)

Since you don't like command line, try just using Synaptic--->    System>>Administration>>Synaptic Package Manager.  That way you'll have a GUI to work with.  Once there, use SEARCH and look for apt...  Install the relevant package and see if it works then.  You might also consider doing an uninstall , then re-install if there are still problems, using Synaptic.

Kevin

---

### Post by Tyke91 on 2007-11-22
synaptic is just a front end for apt... so why would you use it to install its self? :)

anyway... good luck with this :)

---

### Post by LIJI on 2007-11-22
I've managed to fix the problem.
After using the reboot command a few times it asks you to log in. After you do apt-get install apt works and solves the problem.

---

