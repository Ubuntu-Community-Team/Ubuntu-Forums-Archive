---
title: "New install - time to get to login screen"
date: 2008-04-09
forum: General Help
---

### Post by cheeseslice on 2008-04-09
Hi,

I was hoping someone could help me.  I've only be using ubuntu for about a week now and have decided to install it on my second laptop.  The first installation was so smooth something had to go wrong for me with this one.

The problem I'm having is that it takes about 4 minutes from turning the laptop on until the login screen appears.  Once I have logged in everything is perfect and runs quickly but I really wanted to use this machine to check emails/internet etc. quickly, so the boot up time matters to me. 

The laptop is a Dell Latitude:
900MHz
384Mb ram
30Gb

I have been reading a bit on the forum but I can't seem to find any solutions.  This post seems to be the closest I can find: [http://ubuntuforums.org/showthread.php?t=370603](http://ubuntuforums.org/showthread.php?t=370603) 

I have run dmseg and looked at the xorg.0.log log, as suggested in this discussion, but I don't really know what to look for.

Any help would be much appreciated.

---

### Post by njparton on 2008-04-09
You may want to try Xubuntu with that amount of RAM.
 
The other thing I would try first is to remove compiz and set metacity as the default window manager first.  That may help and is defnitely worth a try before a re-install.

---

### Post by cheeseslice on 2008-04-09
I was thinking about installing xubuntu.

Would compiz cause the computer to take so long to boot?  Would you mind explaining this to me, just so I can understand what's happening.  

Once I'm actually logged in the machine runs quite quickly, a lot quicker than xp that was on it before.

---

### Post by njparton on 2008-04-09
Compiz is actually fairly buggy and I had long boot and login > desktop times a while back (just after 7.10 release).
 
Someone recommended that I remove compiz and it cured quite a few related problems I was having.
 
If you don't use it then there's no harm in getting rid of it and it's certainly worth a try.

---

### Post by cheeseslice on 2008-04-09
I meant to thank you for the quick reply in my last post.  I got the problem solved after reading this post: [http://ubuntuforums.org/showthread.php?t=580903&highlight=dell+c610](http://ubuntuforums.org/showthread.php?t=580903&highlight=dell+c610)

I just removed "ro quiet splash" and "quiet" from /boot/grub/menu.lst

The boot time went from 5m 36s to 56.9s, quite a difference!

I don't suppose you would mind explaining the difference between compiz, compiz-fusion and beryl to me?  I have been doing a bit of reading on it but most people expect you to know the basics.  As sad as this sounds, I quite like the rotating cube desktop!

I didn't realise how hard it would be to switch to linux, I spent 20 minutes last night reading user documentation just to work out how to run a file that I needed to make in the termnial window.  I'm thiniking I might take notes as I go along of linux equivalents to windows commands, they might come in handy for someone else in the same position.

---

### Post by njparton on 2008-04-09
I'm glad you got it sorted.
 
I'm not an expert in this area and quite a lot of users feel that compiz etc etc is just a gimmick (as do I). I'm therefore not the best person to give you that advice unfortunately.

---

