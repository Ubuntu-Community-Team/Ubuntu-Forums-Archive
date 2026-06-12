---
title: "Enabling Desktop Effects (I know, I know)"
date: 2008-05-20
forum: General Help
---

### Post by karasuman on 2008-05-20
First of all, I'm sorry if this is an annoying question.  
(I have a feeling that it is, and that everyone whines about how they can't make it work, but... I'll try not to whine!)  I've tried to sort out as much as I can by reading other posts and googling, but I'm brand-spankin'-new at Linux, and I'm not sure I know what I'm doing.  :)

I've mostly managed to set up my computer (hey, it's online!), but I can't seem to enable desktop effects.  It sounds like this is a pretty common problem.  My computer is a Dell Inspiron 1525 with Intel Graphics Media Accelerator X3100.  (That was the only graphics card they'd let me get!)  I see that that's on the "blacklist" for Compiz, but I'm not quite sure what that means.  I'm running Ubuntu 7.10. 

Does my crappy graphics card mean that I can't enable any desktop effects?  I don't even see an option to install or configure or ANYTHING compiz on my machine.  (Nothing under system > preferences; nothing in the add-remove list.)  Will upgrading to the new version of Ubuntu help at all?  (Should I do that anyway?  Is there a danger of programs, like Maple, not working under a new version?)

I appreciate any help you guys can give me.  I feel like I'm wading through a sea of information without having any real idea of where to start.

---

### Post by steveneddy on 2008-05-20
I see that that's on the "blacklist" for Compiz, but I'm not quite sure what that means. 

**It means that you can't run Compiz because it will probably lock up your machine and make it so unstable that regular reinstalls would become normal.**

Does my crappy graphics card mean that I can't enable any desktop effects?  

**It's not a crappy card, but at this time, you can't run Compiz or "desktop effects" on that PC.**

How about enjoying the stability, dependability and reliability more than the eye candy.

Maybe start to figure out some of the cool music tools for playing and ripping and organizing all of your music collection.

Or go for the gaming angle. There are lots of games that you can play on Linux that don't need a 3D graphics card.

Just have fun.

---

### Post by karasuman on 2008-05-20
I know it's just eye candy.  I happen to like eye candy.  ;)  It's certainly not the end of the world, and NOTHING will make me wish I'd gone with Microsoft again, but if there's a way to fix it...  Alas, I'll have to be low-key for a while yet.

I mostly picked up this laptop to have something to take to school with me when I start commuting to classes next month.  The biggest thing I want to do with it is run Maple.  No offense, but if I want games, I'll use my (Windows XP) desktop and the expensive graphics card my husband installed.  ;)  

So far, I'm amazed at how "user-friendly" the interface is.  I'm not a computer dummy, but this is pretty much my first experience with anything but Windows, and I still had things arranged to my satisfaction, internet connection, Thunderbird, etc. all set up with only a little effort.  I was expecting something a lot more obtuse.  :)

---

### Post by Rovdjur on 2008-05-20
> **karasuman said:**
> So far, I'm amazed at how "user-friendly" the interface is.  I'm not a computer dummy, but this is pretty much my first experience with anything but Windows, and I still had things arranged to my satisfaction, internet connection, Thunderbird, etc. all set up with only a little effort.  I was expecting something a lot more obtuse.  :)

One of the many nice things about Ubuntu :) Easy to use and simple enough to learn. If you want to explore the linux world and try other flavors, you can always try using a less user-friendly version! The first linux I tried was Gentoo (I was persuaded to switch to linux by my friend, and he was a Gentoo-wiz), and it was very hard to deal with. Just installing it took hours and lots and lots of terminal commands. Then once you got it up and running, none of the hardware worked, so you had to spend even more hours just making it so you could have wireless and a decent screen resolution.

Anyway, my point is don't get discouraged because you cannot have desktop effects, because it could be much, much worse, such as having laptop that won't even boot up because you made one tiny error. Enjoy Ubuntu though, it will treat you well :)

---

### Post by Forlong on 2008-05-21
Try: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by karasuman on 2008-05-21
Well, upgrading to Hardy seems to have completely fixed my problem.  

Anyone know why that is?  I'd really like to understand how this stuff works a little better than I currently do.  :)

---

### Post by Forlong on 2008-05-21
> **karasuman said:**
> Well, upgrading to Hardy seems to have completely fixed my problem.  

Anyone know why that is?
Hardy doesn't blacklist any PCI IDs.

---

### Post by hellramza on 2008-05-25
In fact, compiz CAN run on an intel x3100 on ubuntu 7.10. I have a Dell Vostro 1500 (intel x3100 on-board) and i just had to modify a file so that compiz skips the black list, for that i followed a post in this forum (dunno which one, but i had te reinstall ubuntu because i messed up my particions so i'm probably making a quick guide to setting up a vostro 1500). You just have to tell compiz to  skip black list, reboot and voila, you get ALMOST fully working compiz+compiz-fusion (almost because i found 2 o 3 plugins that don't work, yes only 2 o 3 so far, cube and the most comonly used work 100%). Good luck and enjoy the eye-candy =)

---

