---
title: "ubuntu practical for custom live cd solution?"
date: 2007-01-24
forum: General Help
---

### Post by &amp;)ky#)^ on 2007-01-24
Moderators:  I wasn't entirely sure what part of the forum to post this, so forgive me if this topic belongs somewhere else.  Feel free to move it.

My name is Jay.  I'm a college student and a hobbyist programmer who knows his way around linux.  Of course, Ubuntu is my favorite distro despite its imperfections.

Here's my dilemma.  I'm at a college campus four days a week pretty much all day.  The college I attend unfortunately has wall to wall windows.  Oh, the horror!  Also unfortunately, I've found all existing LiveCD distros inadequate as a permanent solution.  I'd like to take a crack at putting together a custom live cd for my personal use.  It would be geared towards a casual desktop replacement and development environment.  Ubuntu being my desktop system, I naturally wonder if Ubuntu is a viable platform for my endeavor.  I know the installer for Ubuntu is now a live cd.  However, I find it chunky and not as universally compatible as I'd like.  For example, I always end up having to edit xorg.conf before I can even see gdm.   I've noticed a few other live cds based on Ubuntu as well. Anyway, I've become quite fond of apt-get and debian packages, so I'd like to stick with Ubuntu if possible.

Here's some flexible specs of what I'm imagining.

[LIST]
[*]Must fit on a standard 700MB cd-r.
[*]Must use a 2.6 kernel.
[*]Must be fast and small like Damn Small Linux or SLAX.  Perhaps only a slightly larger memory footprint.
[*]x86 Ubuntu base, dapper or edgy.

[*]Fluxbox or Xfce.
[*]Firefox. Perhaps with Flash.
[*]Gaim or equivalent.
[*]Some XMMS-style music player.
[*]Some kind of office software, but probably not OpenOffice.Org.
[*]Maybe Java runtime and compiler, but probably not.
[*]Maybe Mono and C# compiler, but probably not.
[*]Python 2.3 or better with IDLE.
[*]gcc and cpp.
[*]A couple of games like solitaire and zsnes.
[*]The very latest xbox controller kernel module.
[*]Text editor of choice.  Still haven't discovered my personal favorite.
[*]Maybe The Gimp.  Not completely sure.
[*]Maybe some kind of video player.
[*]Ability to read and write vfat, reiserfs, xfs, and maybe ntfs if it's not a giant hassle.
[/LIST]

I think that these are reasonable expectations.  Size shouldn't really be a problem.  Most of these programs are already included in the Ubuntu Live CD installer.  Anyway, if anyone recommends a method of doing this or any links or references that may help, I'd appreciate it very much.  If I succeed, I'll of course make the final product publicly available.

I'd like this to be as easy as installing a basic server installation somewhere and then just adding what I need and then using some script to live cd it.  I know that's naive, though.

Can someone point me in the right direction as to where to start?  Thanks so much.  You rock, Ubuntu community!

EDIT:
I forgot to mention that I could also use a solution for the development process.  I don't want to waste all that media by burning a new copy of my forked distro just to test the latest change I made.  Is the best way to test the distro mid-development by using virtualization software or is there a better way?

---

### Post by aysiu on 2007-01-24
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by &amp;)ky#)^ on 2007-01-24
Cool little script, but it seems to be changing only the look of ubuntu.  I want a bit more control than that.  Any other ideas?

---

### Post by aysiu on 2007-01-24
> **bluej774 said:**
> Cool little script, but it seems to be changing only the look of ubuntu.  I want a bit more control than that.  Any other ideas?
I assure you, it changes more than the look.

You can easily select and deselect packages.

It's a bit more complicated, but you can also change various system files and configurations.

Check out the screenshots of the Reconstructor wizard:
[http://reconstructor.aperantis.com/gallery/](http://reconstructor.aperantis.com/gallery/)

---

### Post by &amp;)ky#)^ on 2007-01-24
Hmm... I guess I underestimated it.  I'll have to check it out.  Are there any tutorials or help guides for the more complex stuff like I'm thinking of?

Also, is there any way to start with the server base and build a live cd from there?  I'd hate to have to start with the live cd install base and have to remove so much stuff and then add my stuff.  I'd rather just start with a minimal install and build up from there.

---

### Post by yotam on 2007-06-23
> **bluej774 said:**
> I always end up having to edit xorg.conf before I can even see gdm.   

Instead of editing the auto-generated xorg.conf, try edit /usr/bin/dexconf.

---

### Post by zach12 on 2007-06-23
puppy linux on a flash card

---

### Post by saj0577 on 2007-08-28
Is their anyway to do this without using that program as what i want to do is something like, extrack all the files from the .iso and edit them and add/delete from them untill i have my perfect live cd. 

I do not what only to add and take packages off the live cd i also want to have a custom .iso i can burn/(and edit) whenever i want which will have everything how i want it. I dont know if it is possible but the perfect solution for me would be if i could copy files from my current set-up on a computer i have and replace a few of the files in the .iso with my own files.

Saj any help would be great

---

