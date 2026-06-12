---
title: "Uninstall Firefox"
date: 2007-01-22
forum: General Help
---

### Post by kazbear on 2007-01-22
I want to remove Firefox.  I have used add/remove, Synaptic Package manager, and apt-get.  But its still installed.  How can I get rid of it?

---

### Post by bodhi.zazen on 2007-01-23
How did you install it ? Did you download it and install it outside of apt-get/aptitude/synaptic ?

---

### Post by aysiu on 2007-01-23
From [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion): > Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the gecko rendering engine. How low on disk space are you that you have to remove Firefox?

---

### Post by kazbear on 2007-01-24
I wish I had seen that uninstall firefox warning before.  Didnt know.  Its been so long, I cant remember how I installed Firefox.  Perhaps it was already there, I probably tried to install upgrades to it in anyway I could.  Through the terminal, Ad/Remove, downloaded package...Not sure now.

But like the post above warns, I have lost Add/Remove, and I guess all the others.  But FIrefox is still installed.  I'm using it now,

I suspect that because of the many ways I tried to install it, and upgrades to it, that some plug ins are confused (Like flash).  So, I wanted to remove it all and start fresh.

Now I have more issues to deal with,

Any suggestions...

*Edit* I was able to reinstall the packages using the package manager, which re-installed Firefox as  well.  I don't think I will attempt to remove it again, but I would like to get the latest version of flash to work...

---

### Post by xSauronx on 2007-01-24
> **kazbear said:**
> I wish I had seen that uninstall firefox warning before.  Didnt know.  Its been so long, I cant remember how I installed Firefox.  Perhaps it was already there, I probably tried to install upgrades to it in anyway I could.  Through the terminal, Ad/Remove, downloaded package...Not sure now.

But like the post above warns, I have lost Add/Remove, and I guess all the others.  But FIrefox is still installed.  I'm using it now,

I suspect that because of the many ways I tried to install it, and upgrades to it, that some plug ins are confused (Like flash).  So, I wanted to remove it all and start fresh.

Now I have more issues to deal with,

Any suggestions...

*Edit* I was able to reinstall the packages using the package manager, which re-installed Firefox as  well.  I don't think I will attempt to remove it again, but I would like to get the latest version of flash to work...
go here and follow the directions, i had to do the same thing with Xubuntu on 6.10 because apt/synaptic didnt do the trick
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")

---

### Post by ~LoKe on 2007-01-24
So FireFox has turned into the IE of Ubuntu?

---

### Post by eXisor on 2007-01-30
So what do i do If my firefox, latest version in edgy and all, is broken? (It doesn't restore sessions, with or without tabmix+, and it loses the address bar content after I load from a bookmark - just empty space in the address bar for every page).

If I can't uninstall firefox to get a clean config, what do I do? BTW, I've tried removing my user mozilla folder and reinstalling, but the problem remains.

---

### Post by glabouni on 2007-01-30
> **~LoKe said:**
> So FireFox has turned into the IE of Ubuntu?

I feel that way. or the other way around Ubuntu has turned into the windows of IE for firefox.

Sometimes I wish the ubuntu philosophy was actually applied to ubuntu. so far apart from being available free of charge, IMHO the rest of the philosophy is more a work in progress.

firefox is a perfect example of this. I can't remove it without breaking my system, it is way behind opera in term of usability and accessibility, (it is not even free software debian people forked it into [iceweasel]("http://en.wikipedia.org/wiki/IceWeasel") for this reason.)
at first I just wanted to get back to firefox 1.5 as several extension I uses daily (and are the reason for me to use firefox) are not 2.x compatible and 2.x adds nothing of interest to me but annoyances. 

but firefox is only an isolated case, I've encountered the same problem on several occasion, while trying to remove the english only dictionnary for example. 
hopefully, ubuntu dev are aware of these problems and will do something about them.

> Ubuntu Philosophy: 
- software should be available free of charge
- software tools should be usable by people in their local language and despite any disabilities
- people should have the freedom to customise and alter their software in whatever way they see fit.
[http://www.ubuntu.com/Welcome](http://www.ubuntu.com/Welcome)

>  At the core of the Ubuntu Philosophy of Software Freedom are these core philosophical ideals: 
- Every computer user should have the freedom to run, copy, distribute, study, share, change and improve their software for any purpose, without paying licensing fees. 
- Every computer user should be able to use their software in the language of their choice. 
- Every computer user should be given every opportunity to use software, even if they work under a disability. 
Our philosophy is reflected in the software we produce and include in our distribution.
[http://www.ubuntu.com/ubuntu/philosophy](http://www.ubuntu.com/ubuntu/philosophy)

If I want to remove firefox, I *have to* remove ubuntu, so be it. (hopefully this might be fixed in an upcoming ubuntu release)
I recently found ubuntu 6.12 professional which I have to test; as it may suits my needs and taste.
> Ubuntu 6.12 Professional brings new standard into the World of Ubuntu - it is a small CD created for users, who want to install a basic Ubuntu system on their computers (courtesy of ubuntu.pl)

as a matter of facts, it would be nice to have the ability to choose what software I want to have installed during installation, not afterwards. 
It would be nice *not* to have installation procedure end with software I don't wan't and I can't remove installed, and available in repository software I *do* wan't, not installed.

---

### Post by dmizer on 2007-01-30
removing the ubuntu-desktop is merely removing the meta package.  last i checked, it was perfectly safe to uinstall firefox.

edit:
per this post -> [http://www.ubuntuforums.org/showpost.php?p=2051700&postcount=3](http://www.ubuntuforums.org/showpost.php?p=2051700&postcount=3) i stand corrected.  no longer safe to remove firefox.

---

### Post by dmizer on 2007-01-30
> **eXisor said:**
> So what do i do If my firefox, latest version in edgy and all, is broken? (It doesn't restore sessions, with or without tabmix+, and it loses the address bar content after I load from a bookmark - just empty space in the address bar for every page).

If I can't uninstall firefox to get a clean config, what do I do? BTW, I've tried removing my user mozilla folder and reinstalling, but the problem remains.

go to synaptic package manager and find firefox, right click on it and select the option labeled "reinstall".

---

### Post by eXisor on 2007-01-30
dmizer: Two posts in a row without bothering to read the original posts. Bad day?

As I said, did that and removed the user settings folder too, no joy.

glabouni:

You've picked out the pertinent points indeed. Seems the devs don't check their decisions against the published philosophy.

This really sucks. 

And I'm open to correction, but I don't think the devs removed the dependency on the gecko engine for feisty either. Personally I can live without the dependent packages, but there doesn't seem to be a way to get rid of them all without breaking ubuntu.

You'da thunk they'd have learnt from m$.

If a dev could chime in with a way of getting rid of firefox and all dependent packages without killing ubuntu, I'd be happy to hear it.

---

### Post by dmizer on 2007-01-31
> **eXisor said:**
> dmizer: Two posts in a row without bothering to read the original posts. Bad day?

As I said, did that and removed the user settings folder too, no joy.

yeah ... and what's really sad is that you said it IN the quote that i quoted you on. 8-[ 

this is the way things came out after an install, or after an update?  could it be that the install cd was a bad burn or download for the image was off?

---

### Post by eXisor on 2007-01-31
dmizer:

My firefox broke (I think) when I installed swiftfox. They seem to share a lot of folder/data, notably the bookmarks, plugins, configs, etc. I noticed it shortly thereafter, anyway. 
Uninstalling swiftfox didn't resolve the problem. Something is borked in one of the firefox files (not user based) and apart from an uninstall I can't think of another way of solving it.

Oh yes, and swiftfox had the same problem. Whatever the cause is, it's shared by firefox/swiftfox.

---

