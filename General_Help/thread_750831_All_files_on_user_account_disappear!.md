---
title: "All files on user account disappear!"
date: 2008-04-09
forum: General Help
---

### Post by Thorjelly on 2008-04-09
I am having this bizarre problem with my default account.

When I am browsing my files, while listening to music or something, sometimes -- three times now since I first installed Ubuntu on my laptop a few weeks ago -- all the files will suddenly completely disappear while I am still logged on. The icons will change as I move my mouse over them in Nautilus, and when I try to open them, it will complain that it can not locate the file. If I try to open a directory, it will complain that the directory is not there. I suddenly can't even open Nautilus anymore, or really anything; I can't use the logoff/switch user/reset button, for example. I haven't yet tried to see what I can do in the console while this is happening.

The first time this happened, I turned my computer off, then back on, logged back on to my account, and *everything was gone!* My settings, my files, everything was as if I had just made a new account, and I couldn't locate any of my files anywhere on my disk.

Now when this happens, I log on to another account I created first, and then check to see what the status of the files in my normal user account is from there. My idea was that everything might still be there but only when I log back on does anything get reset. Sure enough, everything is still there. And after I check that, after logging on to another account first, I seem to be able to safely log off and back on to my normal one... I hadn't lost anything yet.

But this is extremely bizarre and I don't want to lose any of my files again. Does *anyone* have any idea what is going on and how I can fix it? I am basically a Linux/Ubuntu newbie so I have no idea what kind of setting files I ought to post or whatever for it to make it easier for you guys to deduce the problem. Although my problem appears to be fairly specific so maybe one of you have heard of it before...

Thanks in advance.

---

### Post by Thorjelly on 2008-04-10
It happened again this morning... and this time, I couldn't boot Ubuntu normally. I had to boot into recovery mode. Though once I did that, I could exit and boot normally perfectly fine, without having to change any settings or anything in recovery mode. -_- This happened once before too, but I can't remember if it before directly followed the problem above. I don't believe it did.

---

### Post by mali2297 on 2008-04-10
When this happens, try starting nautilus from a terminal. Does it show any error messages?

---

### Post by natirips on 2008-04-10
Have you used any commands contaings any of the following (possibly malicious) command(s) "sudo", "rm", "mv", or symbol(s) "*" in the console right before it happened? If so post them here, maybe they caused it...

The problem might as well possibly be in your hardware (hard disk in this case - i.e. bad sectors; or eventually your hard disk's cable).

---

### Post by Thorjelly on 2008-04-10
> **mali2297 said:**
> When this happens, try starting nautilus from a terminal. Does it show any error messages?
No. It fails to do anything. And by that I mean, it won't go back to a prompt, it will sit there waiting doing absolutely nothing for as long as I keep the console open. I had forgotten to check and see if I could see my files in the console, though.. I should do that next time.

> **natirips said:**
> Have you used any commands contaings any of the following (possibly malicious) command(s) "sudo", "rm", "mv", or symbol(s) "*" in the console right before it happened? If so post them here, maybe they caused it...
No, although the very first time that this happened it happened after I ran a makefile I had gotten off of an icon theme on gnome-look.org, which I had assumed would simply copy all the files to my .icon folder for me:

```
DEBIANDIR = build-debian
BUILDDIR = build
ICONDIR = $(DEBIANDIR)/usr/share/icons/GartoonRedux
CONTROLDIR = $(DEBIANDIR)/DEBIAN
DOCDIR = $(DEBIANDIR)/usr/share/doc/gnome-icon-theme-gartoon-redux
INFODIR = info

all: render deb-package
render:
	mkdir -p $(BUILDDIR)/scalable
	cp -r src/* $(BUILDDIR)/scalable
	bash -c 'cd $(BUILDDIR); ./render.pl && ./make-index.pl && ./make-links.pl'
	
clean: deb-clean
	find $(BUILDDIR)/ -mindepth 1 -maxdepth 1 -type d -print | xargs rm -r
	find . -mindepth 1 -type l -delete
	
deb-clean:
	rm -rf $(DEBIANDIR)
	
packages: source-package dist-package

source-package:
	tar -cvf ../gartoon-redux-source.tar ../GartoonRedux/
	gzip ../gartoon-redux-source.tar
	
dist-package:
	tar -cvf gartoon-redux.tar $(BUILDDIR)/ --exclude=0ALIAS --exclude=0CONTEXT --exclude=*.pl --exclude=Makefile
	gzip gartoon-redux.tar
	
deb-package:
	mkdir -p $(ICONDIR) $(DOCDIR) $(CONTROLDIR)
	cp -t $(ICONDIR) -r build/* gtkrc
	find $(ICONDIR) -name '*.pl' -delete
	find $(ICONDIR) -name '0ALIAS' -delete
	find $(ICONDIR) -name '0CONTEXT' -delete
	cp -t $(CONTROLDIR) $(INFODIR)/control $(INFODIR)/postinst
	cp -t $(DOCDIR) $(INFODIR)/changelog.Debian $(INFODIR)/copyright $(INFODIR)/changelog $(INFODIR)/AUTHORS $(INFODIR)/README
	gzip --best $(DOCDIR)/changelog.Debian $(DOCDIR)/changelog
	fakeroot dpkg-deb --build $(DEBIANDIR)
	mv build-debian.deb gartoon-redux.deb
	
.PHONY: all render clean packages dist-package source-package
```

Interestingly I've also noticed now that this only seems to happen while I am playing something in Totem Movie Player... although that could easily be a coincidence. Oddly, despite all of my files suddenly "disappearing", at least off of Nautilus, the music would still stream perfectly fine off of my HD..

> **natirips said:**
> The problem might as well possibly be in your hardware (hard disk in this case - i.e. bad sectors; or eventually your hard disk's cable).
I doubt it, since the problem is isolated to things that have to do with my user account. I can run any application in this state, or navigate to any file which is not in my user directory. I've also scanned my HD a few times since this started occurring without any problems.

---

### Post by cmay on 2008-04-10
hi 
where exactly did you get this makefile ?
i can see all of the commands posted in the warning do use these commands in this file.
but to be honest i can not read what the script actually does.
if you didnt have anything really important on this harddisk i would consider to reinstall.
but as i am a newbie myselve i would wait and see if there comes any better answers to this post.
one thing i can say is that i have about six month ago tried to have my hardisk wiped for half of the program using a install script from out of the distrobutions package repos
i will nerver again install anything from sources other than ubuntu or debian myselve.
hope this can help somehow even i do know it did not actually help solve anything.

---

### Post by natirips on 2008-04-10
Properly made makefile sould not alter your system unless it is ment to do so (like acctually compiling/installing something :) ). 

BTW, if you manage to pinpoint the cause of problem you might consider reporting a bug.

---

### Post by mali2297 on 2008-04-10
Before doing anything drastic as reinstalling ubuntu, you could try removing all your hidden files and directories in your home folder (the ones that start with a dot). The fact that you could work from another account indicates that the error might be in one of those files.

---

### Post by Thorjelly on 2008-04-10
> **natirips said:**
> Properly made makefile sould not alter your system unless it is ment to do so (like acctually compiling/installing something :) ). 

BTW, if you manage to pinpoint the cause of problem you might consider reporting a bug.

Well, I didn't give it root permissions. So it shouldn't have messed up my system in any way. I don't know what it could have done to my account, though.

> **mali2297 said:**
> Before doing anything drastic as reinstalling ubuntu, you could try removing all your hidden files and directories in your home folder (the ones that start with a dot). The fact that you could work from another account indicates that the error might be in one of those files.

I have not been using my other accounts long enough to be sure if this problem does not persist on other accounts. What I have done, for now, is transfer all of my files (besides any hidden files, which I did not copy) to a new account, there for safe keeping, and if the problem can not be resolved I will simply use that as my main account. Right now I suspect that this problem occurs only when I am streaming data off of the hard drive, because it appears to be happening when I listen to music; I have been listening to music more frequently lately, because I have been transferring select music files from my desktop to my laptop, and the problem has also been more persistent lately. The problem doesn't appear to persist merely due to harddrive use, though, since copying many files to my laptop does not appear to incite it.

I will try to gather more information and, if I resolve it or I have enough information to find a general cause, will see about reporting a bug. Right now I suspect that this is an account isolated issue, that by some bizarre combination of ignorance and poor luck I've messed up my current user account in some inexplicable way (although I couldn't tell you how), and I can easily enough fix the problem by simply creating another account. Which is really just a mild inconvenience.

EDIT: Okay, I have done what you suggested too, though, deleting my hidden folders from home, with the exception of a few like .purple, since I want to keep my Pidgin logs, and such

---

### Post by Thorjelly on 2008-04-10
Okay. Well, everything else, applications and console, can get to files perfectly fine. It just seems to be Nautilus that doesn't appear working inexplicably. The logoff/reset/etc button doesn't work either, as I have mentioned -- but it will pop up several minutes later from pressing it. CTRL-ALT-DEL shortcut also does absolutely nothing in this state. Deleting those temp files didn't help. This appears to be some bizarre sort of Gnome bug I guess. I will try using another account for a while and see if the bug still persists, and if it does, I guess I will try switching to KDE and see if that has any problems...

EDIT: Oh. I think, in regards to the logout/reset/etc thing, Now I believe that it does not show up or do anything when I press CTRL-ALT-DEL for as long as Nautilus is trying to open. Nautilus will just do nothing for several minutes before giving up, apparently, and only then will the menu pop up -- and it will work fine until I try to open up Nautilus again. I tried opening Nautilus with the console again learning this to let it just sit there for several minutes til the logout screen is allowed to pop up, but it still just sits there, no error messages or anything

---

