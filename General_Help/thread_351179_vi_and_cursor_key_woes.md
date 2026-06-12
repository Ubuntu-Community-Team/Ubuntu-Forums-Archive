---
title: "vi and cursor key woes"
date: 2007-02-01
forum: General Help
---

### Post by brettg on 2007-02-01
Hi all,

I just bought myself a shiny brand new laptop pre-installed with Ubuntu (ie: no Windows Tax!)

It has Core2Duo processor and I'm using edgy x64.

The only small problem I have is when using vi in bash, when I go into edit mode and attempt to move the cursor around I get A B C or F depending on which direction key I press. 

I've done some googling and found many pages all pointing back to;

[http://randomness.org.uk/wiki/?node=Vi%20On%20Solaris](http://randomness.org.uk/wiki/?node=Vi%20On%20Solaris)

That didn't really look like a solution, a workaround at best, but I tried it out anyway. It didn't help.

I vaguely recall having this problem once before and I'm struggling to recall what it was. 

For some reason I kept thinking of /etc/default/locale but that turned out to be a red herring.

So, does anybody have any ideas on this? It's such a small thing but it's driving me nuts. I want to finish setting up my new toy with MythTV, Beryl and all the other gubbins but I'm being held back by such a trivial yet painfully annoying glitch. 

Help me please Ubuntu Gurus!

Update: I tried vim and it works fine. I guess I can either get used to typing vim or workaround symlinking vi > vim but I'd still like to know what is wrong here.

---

### Post by mvaniersel on 2007-02-01
Hi

I struggled with this too for a while but the solution is simple:

sudo apt-get install vim-full

You and me have been using vim in previous version of ubuntu, but edgy now has old-fashioned vi, to save space. Vi doesn't underderstand the cursor keys.

---

### Post by brettg on 2007-02-01
Wow!

Thanks mate! Tried that and it worked a charm. That explains why my dapper box was working but not edgy.

It is true, the best thing about ubuntu is the forums!

---

