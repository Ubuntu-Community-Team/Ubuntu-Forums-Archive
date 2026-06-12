---
title: "List of questions"
date: 2007-12-30
forum: General Help
---

### Post by NadeMaster on 2007-12-30
I have a list of questions because i may make liunux my gaming part of my computer because i have definately been having some issues with my windows internet.  So here are my questions.

1) What is a good firewall for liunux ( i use zonealarm on windows so something similar would be nice)
2) What is a good anti-virus protector for linux and or spyware.
3) Would i be better off taking some of my protection programs and run them through wine.

K thanks for now.  I may add more later.

---

### Post by jken146 on 2007-12-30
1) Ubuntu already has a firewall (iptables) installed.  All ports are closed.  You don't need to do anything.

2) You don't need anti virus software for Linux.  You won't get any spyware either.

3) Running windows security programs in wine would be a total waste of time.


Welcome to Linux!  Hope you enjoy it.  Post back if you have more questions.

---

### Post by meindian523 on 2007-12-30
1]Linux has an inbuilt firewall called IPtables.You might want to install Firestarter,a graphical frontend to configure the Iptables firewall.
```

sudo apt-get install firestarter
```

2]Linux in general doesn't require a AV,if you don't run as root and use software from trusted sources only,though if you want you can use ClamAV(Google it)

3]It's you who has to make a choice,look through the above solutions and decide yourself.

edit: :o oops,didn't mean to step over your toes,jken.

Also,I'm not sure,but would a Windows security program be able to secure Linux against viruses(though it wouldn't require it) running in wine?Would it even recognize the filesystem?

---

### Post by bran on 2007-12-30
1. go with hardware or do not bother.

2. Why?

3. really do not bother

---

### Post by jken146 on 2007-12-30
ClamAV has no always-on protection, and it can only scan for windows viruses, as far as I know.  You only really need this if you run a mail server.  Otherwise you're just slowing your comp down unnecessarily.

---

### Post by meindian523 on 2007-12-30
> **bran said:**
> 1. go with hardware or do not bother.

+1.

---

### Post by jken146 on 2007-12-30
A windows security program running in wine (if you could get it to work) would likely just think it's in windows and not do anything outside of ~/.wine.  It wouldn't have permissions to do anything outside of your home directory anyway (unless you ran it as root, but that would be -- ironically -- a massive security blunder).

---

### Post by meindian523 on 2007-12-30
I thought so too,but just a theoretical question,would a Windows security program recognize filesystems like ext2/3, reiserfs,etc?

---

### Post by NadeMaster on 2007-12-30
K thanks for all of the posts soo quickly.  So u guys r saying if i wanted to run a game like battlefield 2 i would have to run wine and it wouldnt be too quick.  or is there some other way to install bf2

EDIT: I heard something called cedega.  Ever hear of it?

---

### Post by meindian523 on 2007-12-30
Cedega is a commercial program(paid-for) which enables Windows apps to run in Linux.

You can try to look for a native installation of BF2 or if that isn't available,you can find tutorials to do it in wine,but in general,games perform worse off than under their native platform,usually Windows.

---

### Post by NadeMaster on 2007-12-30
ya i know that.  Also i will need a driver for my graphics card.  Do u know of a place where i can get a nvdia evga forceware for the series 6,  my exact card is the 6600

---

### Post by meindian523 on 2007-12-30
The easiest way is to go to System>>Administration>>restricted Drivers Manager.Check the enable box,reboot and you are done.

In the case that's not available,try [Envy]("http://albertomilone.com/nvidia_scripts1.html")

---

