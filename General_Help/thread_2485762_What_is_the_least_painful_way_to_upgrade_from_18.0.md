---
title: "What is the least painful way to upgrade from 18.04 to 22.04?"
date: 2023-04-08
forum: General Help
---

### Post by stevermann on 2023-04-08
The last time I did a 
[COLOR=#1F2937][FONT=&amp]sudo apt full-upgrade
[/FONT][/COLOR]I recall that the process took most of the day.  Is this still the recommended process to upgrade from 18.04 to 22.04?

---

### Post by Quarkrad on 2023-04-08
I think you will find the majority of advice will be backup, backup, backup* - and then do a fresh install.

* not just your user data (photos, documents, music, etc) but things like browser bookmarks and saved passwords.  Lots of other things to backup depending how you use your pc.

---

### Post by #&amp;thj^% on 2023-04-08
Your going from 18.04 to 22.04, while missing 20.04, it's going to take some time. (A ton of changes have happened since then)
this appears to be a good how to: [https://blog.eldernode.com/upgrade-ubuntu-18-04-to-22-04/](https://blog.eldernode.com/upgrade-ubuntu-18-04-to-22-04/)

---

### Post by monkeybrain20122 on 2023-04-08
The least painful way, as always, is to back up your data and do a clean install. I never trust "upgrade" unless you have a pristine system (minimal customization, no ppa or third party apps and drivers, in other words, no reason to "upgrade" instead of fresh install)  and go from one version to the next without any gap in between (from 18.04 to 22.04 there is a huge gap)

You can make it easier next time if you make a separate /home partition, that way a fresh install won't affect your user specific configurations (like your browser's bookmarks and sessions etc)

---

### Post by stevermann on 2023-04-08
> **monkeybrain20122 said:**
> The least painful way, as always, is to back up your data and do a clean install. 

This would be my preferred upgrade path except one of the Ubuntu PCs is running MediaWiki. MediaWiki is a program that uses mysql extensively.  The last time I migrated MediaWiki to a newer PC, it took me days to get it working again.  I do daily mySql backups, so saving the data is not a problem. I have spent the past week trying to install MediaWiki to another computer but days of frustration to get PHP and the required extensions to work made me think again, why not just do an in-place upgrade?

Then I remember how frustrating the in-place upgrade was. Back then I swore, never again. Just reinstall everything.

So, the axiom "If it ain't broke, don't fix it" is screaming loudly in my head.

---

### Post by ne29914 on 2023-04-08
I'd never try an update like that.
But an option could be trying 18.04 - 20.04 - 22.04
My last 20.04 - 22.04 took about an hour on an old laptop. But make 100% certain that you're fully updated/upgraded/autoremoved before each update.

---

### Post by MAFoElffen on 2023-04-08
> **stevermann said:**
> The last time I did a 
[COLOR=#ff0000]sudo apt full-upgrade[/COLOR][COLOR=#1F2937][FONT=&amp]
[/FONT][/COLOR]I recall that the process took most of the day.  Is this still the recommended process to upgrade from 18.04 to 22.04?
I can't be the only one here who noticed that this (in Post #1) is wrong, right?
```

sudo apt full-upgrade

```
...does not upgrade the release. That will update the current release and if needed, remove packages to make that work.

To do a release upgrade to a newer release would be 
```

sudo do-release-upgrade

```
I'm sure that is what you meant, right?

---

### Post by stevermann on 2023-04-08
> **MAFoElffen said:**
> 
I'm sure that is what you meant, right?

No WONDER it took me most of a day...  (lol)

Actually, I did it from the GUI.

---

### Post by TheFu on 2023-04-08
> **ne29914 said:**
> I'd never try an update like that.
But an option could be trying 18.04 - 20.04 - 22.04
My last 20.04 - 22.04 took about an hour on an old laptop. But make 100% certain that you're fully updated/upgraded/autoremoved before each update.

+1.  Never do upgrade the same system more than once.  The second upgrade needs to be a full-install. There are just too many bloat issues that will come up in the new OS, even if it works. Lots of cruft will be left behind from the prior installs, causing confusion for you, helpers, and a few different subsystems.

BTW, I run **apt full-upgrade** weekly, so I suspect you are confused about that option.
From the apt manpage:
```
       full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove currently
           installed packages if this is needed to upgrade the system as a whole.

```
full-upgrade is the same as dist-upgrade, BTW.  Neither will migrate an OS to a new release unless you do some other work first.

The best solution is not the "least painful" in this situation.  Do you want little pain for 2 days, but lots of little issues for the next 2 yrs?  Or do you want a little hassle for the next 2 hours, and very few issues for the next 2 yrs?
That's the choice to be made.

---

### Post by guiverc on 2023-04-08
I recently (~9 days I think) finally got around to performing a *release-upgrade* of a *xenial* desktop system (16.04) and got it to at least 20.04 (*ie. two upgrades; 16.04->18.04, reboot, check then 18.04->20.04*).  That was *slow* and took more than a day (*as I forgot it was running, the screen blanked & I went to bed etc... forgetting it mostly made it longer*), but regardless it took *many many hours.*

The reason I did that upgrade however, was partially because I wanted to look one last time at the change of desktop (Ubuntu 16.04 used Unity 7 & 18.04 uses GNOME), and wanted to have a quick play & try and mentally contrast the differences one more time.. The GNOME UI change  kept my interest less than 10 seconds, and wasn't worth it.

My planned upgrade path was what I think of as an '*Upgrade via re-install*', ie. non-destructive upgrade of the newer release; thus I'd have jumped straight to 22.04 (*I keep that box on LTS*) and be done in ~30 minutes including have it download & re-install the packages I'd added automatically.  The only thing I'd not decided with this approach was what ISO I use (I didn't want GNOME thus I'd not have used Ubuntu Desktop; didn't want LXQt thus not Lubuntu; I was leaning towards Xfce/Xubuntu, etc). My system is a multi-desktop install, so I was going to get multiple desktops anyway regardless of media; but how the packages are marked as installed will vary depending on media I use (*thus the decision*). I'd not made that decision in nearly 3 years..

Thus I decided I wanted to look at the UI change from 16.04 to 18.04; and so went the *release-upgrade* route.

For me, I've still got one more *release-upgrade* before I reach 22.04; and again I'm really wanting to just '*upgrade via re-install*' as its just so much faster!  but I've still got to decide what ISO & how I want packages marked in the metadata...

Beyond my OCD... My backup strategy on *release-upgrade* problems of desktop systems is always the *unclean* or *repair* type installation, and find it **so useful**  I'm often using it instead as its so fast, and avoids the disk space issues I seem to always have (*with my bloating my boxes with multiple desktops probably!*).  Maybe consider it  (*I use it in fact more often than the release-upgrade on desktops*).

**Notes**

- it's great for **desktop** installs; not server applications/installs
- if using ***flavor* media** it's easier (as 'universe' is enabled automatically for *flavors*, for some releases you need to manually activate *'universe' *before install so it'll find the packages 'universe' packages as they need to be downloaded & installed; if you forget to enable 'universe' they'll get skipped & you receive a *generic* error that some packages couldn't be found).  I take note of what packages I had installed before using it; so if I forgot to *enable* universe & it was required (*which varies on release/ISO*) I just re-add my *missed* packages.
- its **triggered** by re-use of directories WITHOUT FORMAT for `ubiquity` and `calamares` installers on Ubuntu ISOs; even works with the new *ubuntu-desktop-installer* (23.04) now too though my testing hasn't been extensive.
- **no user file is touched, no user config changed**
- **global changes** (in system directories) are however lost; an issue mostly for server installs, but some desktop users may make such changes (they're not default; most desktop changes are user specific though)

FYI:  The lack of format causes the installation to do the following

[LIST]
[*]take note of your *manually* *installed* packages 
[*]erase system directories 
[*]install the new system 
[*]if internet is available install the extra packages noted earlier 
[*]ask to reboot (*and won&#8217;t touch any user files*) 
[/LIST]

As this install type was intended to **REPAIR **installs it's great... I'm just using it to install a newer release :)

**Do note: ** I do an audit of the software I use first; esp. where 3rd party packages are used. How it goes with 3rd party packages depends on how they are created/packaged; if done carefully you'll not have problems, however many 3rd party packages don't consider the *release-upgrade* aiming only to get you the *newest* packages for the initial install release & thus those packages will have problems; my audit before doing the install is looking for these type issues. FYI: All QA is done by Ubuntu is without 3rd party packages.

---

### Post by #&amp;thj^% on 2023-04-09
> **guiverc said:**
> My system is a multi-desktop install, so I was going to get multiple desktops anyway regardless of media; but how the packages are marked as installed will vary depending on media I use (*thus the decision*). I'd not made that decision in nearly 3 years..
+1 same as me
> **guiverc said:**
> 

- it's great for **desktop** installs; not server applications/installs
- if using ***flavor* media** it's easier (as 'universe' is enabled automatically for *flavors*, for some releases you need to manually activate *'universe' *before install so it'll find the packages 'universe' packages as they need to be downloaded & installed; if you forget to enable 'universe' they'll get skipped & you receive a *generic* error that some packages couldn't be found).  I take note of what packages I had installed before using it; so if I forgot to *enable* universe & it was required (*which varies on release/ISO*) I just re-add my *missed* packages.
- its **triggered** by re-use of directories WITHOUT FORMAT for `ubiquity` and `calamares` installers on Ubuntu ISOs; even works with the new *ubuntu-desktop-installer* (23.04) now too though my testing hasn't been extensive.
Great Minds think alike, I'm not sure I remember how to do a clean install...:lolflag:

> **guiverc said:**
> 
As this install type was intended to **REPAIR **installs it's great... I'm just using it to install a newer release :)

**Do note: ** I do an audit of the software I use first; esp. where 3rd party packages are used. How it goes with 3rd party packages depends on how they are created/packaged; if done carefully you'll not have problems, however many 3rd party packages don't consider the *release-upgrade* aiming only to get you the *newest* packages for the initial install release & thus those packages will have problems; my audit before doing the install is looking for these type issues. FYI: All QA is done by Ubuntu is without 3rd party packages.
+1
I do so much with my systems on a testing basis, that I've just learned to up a release, and when needed to back-down to previous release.
Take the above sentence with a big dose of salt, down grading is not fun always, and will put your Linux foo to a new level. :!:(Not recomended)

---

