---
title: "Is it safe to abort the Software Updater?"
date: 2021-03-11
forum: General Help
---

### Post by robert99999 on 2021-03-11
I started running Software Updater about an hour ago. For the past 1/2 hour the progress bar has been doing a left-right-left dance, and the info below the bar says: Updating snaps. It appears to be locked up. If I click the Details dropdown, nothing happens.

Advice?

---

### Post by robert99999 on 2021-03-11
Never mind. I guess I was too impatient. It finished updating, as soon as I posted the above message.

---

### Post by vanadium on 2021-03-13
Still, this is a relevant question. I would consider it unsafe to interrupt an ongoing software update. There is a chance that the your package system breaks. Probably the same applies if you interrupt the graphical updater, unless that one has provisions to safely close update operations when you interrupt it.

---

### Post by grahammechanical on 2021-03-13
Did it truly take more than 30 minutes to update snaps? How many snap apps do you have installed? By the time software Updater has got to the point where it is updating snaps then all the other updates (shall we say, the usual ones?) have been downloaded and applied. If anything is going to break it would be a snap packaged application and not the OS.

The length of time an update takes would depend upon how often the system is updated and the download capacity of the internet connection. By the way, updating through terminal commands avoids snaps being updated. That would speed things up a bit.

Regards

---

### Post by robert99999 on 2021-03-14
Thanks for the info.
In retrospect, I think I was having slow Internet problems when I was doing the update. So, that would probably explain the problem.

I would certainly avoid interrupting an update unless I was absolutely sure that something had gone terribly wrong. I know that some updaters for some systems will buffer the entire download before overwriting any system files. So, I was wondering if this software updater works this way, or has some orderly way to recover in case it does get interrupted.

---

### Post by Impavidus on 2021-03-15
The updaters for Ubuntu normally download everything before they start replacing files.¹ Aborting while still downloading is quite safe. If you abort during installation, there's a possibility that the software that was being upgraded during the interrupt will stop working. If that software is vital to booting or to the package manager, it may be hard to solve. In most other cases, rerunning the package management tools fixes it.

¹: There are some exceptions. In a few packages, the installation scripts will download more files, that couldn't be included in the package for legal reasons. This applies to packages like ttf-mscorefonts-installer and in the past flashplugin-installer.

---

### Post by robert99999 on 2021-03-20
Well, it happened again tonight. The update was only about 60KB, which it downloaded in a few seconds. Then, it ended up again with the message "updating snaps" for nearly an hour. So, I just let it do its thing, and it eventually finished.
What exactly is "snaps" ?

---

### Post by deadflowr on 2021-03-20
> What exactly is "snaps" ?

[https://en.wikipedia.org/wiki/Snap_(package_manager)]("https://en.wikipedia.org/wiki/Snap_(package_manager)")

Also, to see what snaps are installed you can open a terminal and run
```
snap list
```

That's the quickest way to find out what snaps are installed.
Otherwise you can find out by tediously scrolling through the Software Store's list of installed apps section.
All snaps are installed from snapcraft/snap store and would be listed in the Source section of the packages Details section.

---

### Post by robert99999 on 2021-03-20
> **deadflowr said:**
> 
Also, to see what snaps are installed you can open a terminal and run
```
snap list
```


Interesting. When I do that, I get no output. Snaps appears to go into never never land, and nothing happens. I have to get out by doing a ctrl-Z. So, it appears that snaps is the problem, not the updater.

---

