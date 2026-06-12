---
title: "krusader font problem"
date: 2019-05-01
forum: General Help
---

### Post by jgw on 2019-05-01
I thought I would take another look at Krusader.  I used to use it and then stopped (can't remember why).  As far as I can tell this is a KDE program.  I was able to change the display font in its configurator but I can't figure out how to deal with the toobars, dropdowns, etc. font sizes.   I am using a 4k display (3840x2160)  The toolbars and dropdowns are teeny.  To change the display font sizes I had to go up to 45 to get a decent size.  I am finding that there are a lot of programs that seem to use KDE and all those programs have the same problem.  I have read a bunch of stuff on this one and thought I had better get some help.  I am currently using the 18.04 preferenced Gnome.  Apparently one can also run KDE programs in Gnome to but everytime I make a run at a KDE program the font thing seems to stop me cold.  My current problem  is file managers.  I have tried several for gnome and each seems to have problems.  Thunar, for instance does not transfer files well.  I have found the only way to accomplish that is to copy the file and then paste it where I want it.  There is a send to option but is really limited.  I can do this but.....

I used these programs before I had a 4k display with no problem, but, now, not so much.

This system:
Memory:		14.6 GiB
Processor:	        AMD® A8-7650k radeon r7, 10 compute cores 4c+6g × 4 
Graphics:	       AMD® Kaveri
GNOME:		3.28
OS Type:		64.bit		
Disk:		983.4 GB

Thank you................

---

### Post by DuckHook on 2019-05-01
I don't mean this to be in any way dismissive (such is most certainly not my intent), but you have posted a number of times regarding Qt apps. You seem to quite like them. Have you considered simply installing Kubuntu? It's a fine flavour and your KDE apps would all be native to it.

And while I have not personally tried this out, I am given to understand that GTK apps tend to behave better in Kubuntu than Qt apps do in Ubuntu.

---

### Post by jgw on 2019-05-02
Thanks for the reply.  

Yah, I think you are right.  My problem is simple.  In my ignorance I had decided that to try another flavor I would have to do a complete reinstall.  Then  I decided to google "add flavor to ubuntu" and found [https://askubuntu.com/questions/306282/can-i-change-my-ubuntu-desktop-into-a-different-flavour-like-kubuntu](https://askubuntu.com/questions/306282/can-i-change-my-ubuntu-desktop-into-a-different-flavour-like-kubuntu)     Seems I don't have to do a complete reinstall at all!   (sometimes ignorance is not bliss?")   This is a bit embarrassing as I have been at this for enough years to have known this - must be an age thing.  

Anyway, this is going to get interesting.  I really appreciate your thoughts on all of this.  I suspect this is the best answer of all!

Thanks again!

---

### Post by DuckHook on 2019-05-02
A further thought&#8230;

Multi-boot with Kubuntu on one partition and vanilla Ubuntu on another. Share a common data directory with both. Simply symlink needed directories (Docs, Music, Downloads, Video, etc) back to each. No need to choose one over the other.

---

### Post by DuckHook on 2019-05-02
> **jgw said:**
> …Then  I decided to google "add flavor to ubuntu" and found [https://askubuntu.com/questions/306282/can-i-change-my-ubuntu-desktop-into-a-different-flavour-like-kubuntu](https://askubuntu.com/questions/306282/can-i-change-my-ubuntu-desktop-into-a-different-flavour-like-kubuntu)…
I feel for you.

That's what I find so frustrating with AskUbuntu sometimes. They are interested only in answering the technical side of a question and often ignore the larger context. They give technically correct answers that constitute bad practical advice. So what if you end up dragging in hundreds of unwanted dependencies? :roll:

There's a further error in that so-called "solution" that is really pernicious: the installation of a DE is a one-way valve. There's no going back afterwards. It is not as simple as:```
sudo apt purge blah-blah-blah
```…because the DE metapackage is just a wrapper for the hundreds of dependencies that are contained within. Purging the metapackage is just throwing away the box that those hundreds of dependencies came packed in. Those hundreds of packages all get left behind. Coincidentally, another poster just asked a [similar question here]("https://ubuntuforums.org/showthread.php?t=2418110"). You do not get to unscramble that egg so easily.

At this point, you may wish to consider a pure reinstall and go straight to Kubuntu. As mentioned, it's a good DE. But this time, do *all* of your experimentation in VMs. You will be thankful for practising this form of self-discipline on your next version upgrade.

---

