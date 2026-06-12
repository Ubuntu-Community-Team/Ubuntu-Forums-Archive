---
title: "Uninstall Evolution?"
date: 2007-03-27
forum: General Help
---

### Post by Madmoose on 2007-03-27
Hi. 

I use Thunderbird for my mail and calendar, and I was wondering if it's possable to uninstall Evolution? I went into add/remove programs, and it told me to remove it via synaptic. Yet, when I clicked the "Mark for removal" I noticed that the "Ubuntu-Desktop" was going to removed. Now... I think I need that. 

So, I tried to remove everything except Ubuntu-Desktop, and I couldn't do it.

Now, is it possible to remove Evolution at all? I'm getting updates for it, but I don't use it. Don't want to waste the bandwidth. 


Thanks, 

Moose

---

### Post by johnc4510 on 2007-03-27
Evolution is part of the basic Ubuntu package and can't be removed from the system without breaking it.

---

### Post by wrwjpn on 2007-03-27
I was wondering the same thing. I left the MS world for the freedom to remove unwanted apps and not break anything. I am wondering why can't I remove it without breaking things:confused:

---

### Post by fishmorg909 on 2007-03-27
That's odd... I use Thunderbird too, and decided to remove Evolution. I just went to Synaptic and uninstalled it (Evolution the main app, nothing else)... well, now it's off my menu and Ubuntu still works fine. (I'm using Dapper.)

---

### Post by hikaricore on 2007-03-27
> **johnc4510 said:**
> Evolution is part of the basic Ubuntu package and can't be removed from the system without breaking it.

ummm.... no

You can remove Evolution as well as Ubunutu-Desktop.

This will not break your ubuntu.

Ubuntu-Desktop is just a meta package that keeps everything nice and tidy.

Be aware that you'll need to reinstall ubuntu-desktop and any associated software
if you intend to upgrade at any time.

Enjoy,

--Aaron

---

### Post by johnc4510 on 2007-03-27
I stand corrected, and am glad to know this. Thanks

---

### Post by dcstar on 2007-03-27
> **johnc4510 said:**
> I stand corrected, and am glad to know this. Thanks

And if you don't want to uninstall but still stop any updates, go into Synaptic and use the "Lock version"(?) feature on a package.

That will lock it at the current version.

---

### Post by Madmoose on 2007-03-28
> **hikaricore said:**
> 
Ubuntu-Desktop is just a meta package that keeps everything nice and tidy.

Be aware that you'll need to reinstall ubuntu-desktop and any associated software
if you intend to upgrade at any time.



Thanks for the info. Would you know if synaptic will automaticly install the associated software like it does some other packages, or am I going to have to install everyone one by one?

[QUOTE=dcstar]

And if you don't want to uninstall but still stop any updates, go into Synaptic and use the "Lock version"(?) feature on a package.

That will lock it at the current version. [/QUOTE]

Thanks. I didn't know that. I might end up doing that just to save the hassle.

---

### Post by kinkdxm on 2007-03-28
> **hikaricore said:**
> You can remove Evolution as well as Ubunutu-Desktop.

This will not break your ubuntu.

Ubuntu-Desktop is just a meta package that keeps everything nice and tidy.

Be aware that you'll need to reinstall ubuntu-desktop and any associated software
if you intend to upgrade at any time.
That sounds bad to do.
Is it?
So after I un-install Evolution I have to then go back into symatic and select to install the ubuntu-desktop?

---

### Post by floke on 2007-03-28
You can do it that way if you want - or drop to terminal and type: sudo apt-get install ubuntu-desktop

I've uninstalled/reinstalled this loads of times with no trouble.

Some of the attached libraries for evolution are deeply embedded in the system for some reason and synaptic wants to take half of gnome with them - so I think I'll just leave them where they are :)

---

### Post by hikaricore on 2007-03-28
Unless you're dist-upgrading, after removing evolution you DON'T want to install ubuntu-desktop.

As this will just reinstall evolution.

The meta package ubuntu-desktop installs the basic elements of the ubuntu/gnome desktop environment (just as kubuntu-desktop installs the basic elements of the kubuntu/kde desktop), they can all be seperated and removed if you don't need them.  Upgrading to a new version of ubuntu (ie. Dapper to Edgy or Edgy to Feisty) will more than likely/probably require that you reinstall ubuntu-desktop so that you get all the proper packages installed and everything goes smoothly without breakage.  I hope this makes my previous statements more clear in their meaning.

---

### Post by mscir on 2007-12-21
Thanks for explaining that, I use Thunderbird too and after you posted the desktop reinstall code I uninstalled Evolution and didn't run into any problems, Thanks for explaining.

---

