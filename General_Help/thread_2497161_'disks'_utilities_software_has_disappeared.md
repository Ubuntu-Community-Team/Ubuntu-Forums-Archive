---
title: "'disks' utilities software has disappeared"
date: 2024-04-25
forum: General Help
---

### Post by dalpets on 2024-04-25
In my  22.04 installation I used the 'disks' software in utilities to resize my Ubuntu OS partition. The resizing worked but after doing so the software disappeared from 'utilities'. I tried reinstalling it but it still has not come back.
What has happened here & is there means to get it back?


[FONT=Arial][SIZE=6]SOLVED[/SIZE][/FONT]

---

### Post by TheFu on 2024-04-25
a) Please tell us how this was solved.   You created a mystery story, but ripped out the last page where all is revealed!  Don't do that to us! Please.

b) When a thread is solved, use the _Thread Tools_ button to mark it that way, so others are helped and people looking to help don't waste their time.

Looking forward to reading the last page.

BTW, *Gnome Disks* has some oddities and sometimes does undesirable things.  Best to use **gparted ** for partitioning needs if a GUI is desired.

---

### Post by dalpets on 2024-04-25
The problem is that I have been currently multi tasking multiple Linux flavours in an endeavour to establish one that I am happy with. For numerous of those it has not been so, particularly with regard to the gparted issue. So it was with some glee, after hours of trying to make it work with other distros that Ubuntu partitioning worked fine with 'disks', in an instant. From my sometime historical perspective of Ubuntu I had forgotten some of its user characteristics & moreover I didn't find an obvious reference to the 'solved' notation that I was historically & generally used to, & also mainly because I was very much more focused on other issues of importance to me. So it was that the housekeeping issue you raise was overlooked, but rather than just leave it open, out of respect I did it the unconventional way.  

Solvement came about when I realized the dot page method used by Ubuntu on the desktop for installed software & there it was closseted away in dot two.  

Historically, I seem to remember that a few distros, at installation time, would ask more questions regarding partitioning setup that would have the effect of obviating dire straits of rear guard action for required changes. It would haved saved me mightely.

---

### Post by TheFu on 2024-04-25
> **dalpets said:**
> Solvement came about when I realized the dot page method used by Ubuntu on the desktop for installed software & there it was closseted away in dot two.  
You've lost me completely. No idea what a "dot page" is.  Oh well, perhaps it will make sense to someone else.

> **dalpets said:**
> 
Historically, I seem to remember that a few distros, at installation time, would ask more questions regarding partitioning setup that would have the effect of obviating dire straits of rear guard action for required changes. It would haved saved me mightely.

Ubuntu has the "Do Something Else" storage setup for people who don't want 100% defaults with trivial pre-selected choices.  Someone completely new to Linux usually doesn't know anything about partitioning.  They think in terms of "Drives" and "Drive Letters" - which they've been lied to about.  A drive letter is just an NTFS formatted partition for that other OS which we don't speak about.  

Before GPT, it was common for that other OS to use 3 or more partitions on a shipped PC when only 4 were possible, making it more complicated to install side-by-side.  It tool a long time for support utils like grub but Ubuntu is down to needing only 1 dedicated partition.  /boot/ and / and a swapfile are all setup by default on a single Linux ext4 partition.  

Of course, if you prefer a more complex storage setup, that's possible.  I do and bypass as much of the Ubuntu Installers as possible, preferring to setup my storage outside the installer, then just point the installer at my pre-created storage logical volumes.  But you do it your way. Whatever you like.

So, still not pushing the _Thread Tools_ button?  Oh well, I'm out.  I tried.

---

### Post by #&amp;thj^% on 2024-04-25
> **TheFu said:**
> You've lost me completely. No idea what a "dot page" is.  Oh well, perhaps it will make sense to someone else.



+1 I'm as lost as you.
Oh well lost in translation...:confused:

---

### Post by Morbius1 on 2024-04-25
What's the matter with you folks. Isn't his explanation obvious? It's behind the dot two.

---

### Post by #&amp;thj^% on 2024-04-25
> **Morbius1 said:**
> What's the matter with you folks. Isn't his explanation obvious? It's behind the dot two.

Oh yes the old dot two trick....LOL I should of known. ;)

---

### Post by ajgreeny on 2024-04-25
Please, please do tell us how you solved this.
What you have done is simply added the word SOLVED to your post which is no help at all to others and will not be found when searching the forum.
Was "Disks" reinstalled, was it never really removed, did it move to some other section in the menu system

Tell us all the detail then if still appropriate mark this as solved using the Thread Tools menu up,top of all threads.

---

### Post by deadflowr on 2024-04-26
> **ajgreeny said:**
> Please, please do tell us how you solved this.
What you have done is simply added the word SOLVED to your post which is no help at all to others and will not be found when searching the forum.
Was "Disks" reinstalled, was it never really removed, did it move to some other section in the menu system

Tell us all the detail then if still appropriate mark this as solved using the Thread Tools menu up,top of all threads.
post #3
> Solvement came about when I realized the dot page method used by Ubuntu on the desktop for installed software & there it was closseted away in dot two.

Basically they had to learned gnome's funky designs.

---

### Post by ajgreeny on 2024-04-26
Fair enough, but having not even tested or looked at the new versions of Ubuntu it just shows, firstly, that I now know almost nothing about gnome in its most recent versions and secondly that I was correct moving to Xubuntu way back in 2010, I think, when gnome2 turned into gnome3, which just didn't work for me, and now, even more peculiar, gnome46 or whichever version it has now moved to.

I still have no idea what the dot page mentioned is nor do I think I will bother to find out what was meant,

---

