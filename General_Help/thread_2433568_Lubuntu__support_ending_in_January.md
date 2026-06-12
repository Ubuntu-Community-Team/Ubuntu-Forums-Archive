---
title: "Lubuntu  support ending in January"
date: 2019-12-21
forum: General Help
---

### Post by zalanz on 2019-12-21
I did not realise that lubuntu 19 that I donloaded, was not a LTS.   It was a new install and I do not have any earlier versions on my computer

In January 2020, should I keep using it, I do like it, or is it possible to load an earlier version or do I have to do a new install?

I would like to keep all my files etc though.

Will my version 19, be updated anytime after January?

thanks

---

### Post by mörgæs on 2019-12-21
Please post the output of ```
lsb_release -a
```

---

### Post by zalanz on 2019-12-21
alan@alan-pc:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 19.10
Release:        19.10
Codename:       eoan
alan@alan-pc:~$

---

### Post by mörgæs on 2019-12-21
In Ubuntu short term support means nine months. 

You have 19.10 installed. Nine months added to 19.10 gives 20.07. 

That is, your system is supported through july, at which time you can do a fresh install of 20.04.

People using 19.04 should install 19.10 in january.

---

### Post by zalanz on 2019-12-21
thank you very much

---

### Post by mörgæs on 2019-12-21
You're welcome. Please mark the thread solved.

---

### Post by guiverc on 2019-12-21
You don't need to re-install to *release-upgrade *from your 19.10 release, to Lubuntu 20.04.

You can use the command `do-release-upgrade` and your release will *bump* itself to the next release, there are other commands to for example `[COLOR=#000000][FONT=monospace]do-release-upgrade -d -m desktop -f DistUpgradeViewKDE[/FONT][/COLOR]` will provide a more GUI pretty display instead of the pure text interface with `do-release-upgrade`.

My current box (now on 20.04) was a 17.10 install, and I've *bumped* myself to the next release every six months.
LTS releases can *bump* to the next release, or straight to the next LTS release, *long-term-support* releases come out in April of even years, so none this year.  (*and FYI it's 19.04 that is soon EOL, not 19.10*)

---

### Post by zalanz on 2019-12-22
when will 20.04 be available to upload

---

### Post by CatKiller on 2019-12-22
> **zalanz said:**
> when will 20.04 be available to upload

It will be released in April 2020; the clue's in the name. It's available for testing now, but obviously there will be *a lot* of changes between now and then: the kernel that will be used hasn't been officially released yet, for example.

---

### Post by Bucky Ball on 2019-12-23
Incidentally, Lubuntu 20.04 LTS is a long-term support release so, once you get to 20.04 LTS, you won't need to worry about upgrading once a year in future. You can upgrade to the next LTS release when the time comes, leapfrogging all the interim releases in between. ;)

PS: Not a bad idea to wait until June or July to upgrade to 20.04 LTS. Sometimes a spanking new release has a few lingering bugs and by July, hopefully most of them will be ironed out. Good luck.

---

### Post by zalanz on 2019-12-23
many thanks

---

### Post by guiverc on 2019-12-23
If you want to download the Lubuntu 20.04 daily and have a look, it's available from this site - [http://iso.qa.ubuntu.com/qatracker/milestones/408/builds](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds)  (just follow the link for Lubuntu).  

(I haven't provided the Lubuntu link myself, as it'll take you to the current daily; which may no longer be available in a couple of days as it'll have been replaced with the newer 'daily'  (daily probably ~*means* interval, early in the cycle they are produced weekly, are produced 'daily' most of the time, though on occasion (esp. late in dev. cycle) they produce more than one 'daily' per day).  If you follow the link you'll see "*Link to the Download Instructions*" near the top which will tell you how to download the ISO, which you can write to media & test (just with "Start Lubuntu", or yes install.

PS: if you have bandwidth quota's - learn to use `zsync` as it'll only download the changed parts of the ISO, ie. my first 20.04 download downloaded about ~3% of the file as I just copied & renamed my 19.10 ISO.  Today's started download at 92% of complete (ie. 8% changed & thus downloaded from prior daily I had)

The Lubuntu manual ([https://manual.lubuntu.me/](https://manual.lubuntu.me/)) applies to the current 'stable' release so some things may have change & thus the 'stable' manual won't perfectly apply (none come to mind, but I'll just have forgotten). If you need/rely on 3rd party software (PPA's etc), most of them won't support 20.04 till very close to release.  If you like a stable & consistent environment without change - it's not for you. A couple of days ago the wallpaper in the login screen was changed; I barely notice changes, but some I suspect would find that disconcerting (that example is benign, but some may impact your workflow; differences people see only in the jump from one release (eg. 19.04) to the next (eg. 19.10) occur gradually on development releases).

Yeah I mentioned I'm running it, being a development release there are many upgrades (you can expect multiple per day most days) but problems may occur. Certain support sites don't allow ubuntu+1 (development) support so you should feel pretty competent to solve issues yourself (learn which sites allow ubuntu+1). Problems may be extremely rare, but be aware there are risks to using a development release. Thus the 'Try Lubuntu' (or Start Lubuntu) option from the 'live' media is a great way to have a look without the *risk* of making it your main workstation.  (*Yes beyond install, `do-release-upgrade` will bump you from 19.10 to 20.04 too; but I don't want to encourage it; try running it from a 'live' environment first, see if you actually notice a difference*).

---

### Post by mörgæs on 2019-12-23
> **zalanz said:**
> many thanks

The best 'thanks' you can give back is marking the thread solved.

---

### Post by rsteinmetz70112 on 2019-12-23
> **Bucky Ball said:**
> PS: Not a bad idea to wait until June or July to upgrade to 20.04 LTS. Sometimes a spanking new release has a few lingering bugs and by July, hopefully most of them will be ironed out. Good luck.

You can you set your system to upgrade only to LTS versions, but that won't be offered to you until 20.04.1 which will probably be June or July.

---

