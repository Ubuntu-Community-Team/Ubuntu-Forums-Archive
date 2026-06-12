---
title: "Firefox blocks some pages"
date: 2023-06-18
forum: General Help
---

### Post by gipsyshadow on 2023-06-18
I use "Firefox 113.0.2 (64 bit) for ubuntu canonical - 1.0" on Ubuntu 18.04.3LTS 64bit and from yesterday I get this error: "**Your tab just crashed**". This doesn't happen with every page, eg. this happens every time I search anything with [google images]("https://www.google.com/imghp"): I get my result and after 3-4 seconds my page turns into that error.
This doesn't happen with FF 79.0 (64bit) on Windows 10 so I'm quite sure this doesn't deal with any temporary google issue.

These are my attempts to solve the problem but without success:
- starting FF in recovery mode;
- changing the key "browser.tabs.remote.autostart" from true (default) to false;
- (after switching FF off) renaming .mozilla folder, then running a "clean" FF

Do you know what's the cause and how to fix it?

---

### Post by Rubi1200 on 2023-06-18
Have you tried switching to private browsing and seeing if the same thing happens?

Are you using a VPN when searching?

Do you have any extensions installed recently that might cause this?

Have you cleared cache and cookies?

---

### Post by gipsyshadow on 2023-06-19
Hi,
- I'm not using any VPN;
- I've tried with private browsing without success;
- No extension installed recently.
Before clearing cookies (it'd be a real pain for me to re-digit every username and password...) I'd like to know if there's a way to upgrade FF from 113.0.2 to 114.0.1 that is the latest one. Ubuntu can't upgrade it automatically beyond 113.0.2.

EDIT
Sorry if I forgot to tell it to you before but I'm running Ubuntu 18.04.3LTS 64bit. I'm afraid that Ubuntu can't upgrade FF because 18.04 is not supported anymore. Is this the reason?

---

### Post by Holger_Gehrke on 2023-06-19
> **gipsyshadow said:**
> 
Before clearing cookies (it'd be a real pain for me to re-digit every username and password...) I'd like to know if there's a way to upgrade FF from 113.0.2 to 114.0.1 that is the latest one. Ubuntu can't upgrade it automatically beyond 113.0.2.

EDIT
Sorry if I forgot to tell it to you before but I'm running Ubuntu  18.04.3LTS 64bit. I'm afraid that Ubuntu can't upgrade FF because 18.04  is not supported anymore. Is this the reason? 		

How did you install Firefox ?
[LIST]
[*] The default installation on new systems as a snap should by now have updated you to 114.0.1-1, that's been out since June 9th. If you're using the Firefox snap, close firefox, open a terminal and run 'snap refresh firefox' to force the update. Don't know if that will work on 18.04, but I see no reason why it shouldn't.
[*]The PPA from mozilla-team is also on 114.0.1. If that's what you're using then 'sudo apt update && sudo apt upgrade' should get you there. This PPA does have packages for 18.04 aka bionic beaver.
[*]If you're using the tar-ball from mozilla, then it should have updated itself if you installed it into a directory that you've got write access to; if you open 'Help->About Firefox' it should look for updates and update itself if it can. This should be completely independent of the version of Ubuntu you're using.
[/LIST]
If you got Firefox from the standard repositories, you might have a problem and might want to switch to one of the methods I listed above.

Holger

---

### Post by gipsyshadow on 2023-06-20
Just another question.
I installed chromium from ubuntu software few months ago and now I see it's updated to the 114.0.5735.106 snap release and there's no issue searching images with it, I mean the error "Gah. Your tab just crashed" doesn't occur. Does it mean chromium is safer than firefox for my ubuntu 18.04.3?
I think I've to move to 22.04 release but I think I'll do that on july-august, I've got no time for now :)

---

