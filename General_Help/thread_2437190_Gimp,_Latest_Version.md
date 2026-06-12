---
title: "Gimp, Latest Version"
date: 2020-02-19
forum: General Help
---

### Post by oldbob2 on 2020-02-19
Hi all,

another user who's finally seen the light! 

I was using Mint Cinnamon for a few weeks, but it reminded me too much of the Win 7 desktop, plus I fancied a change so I installed Ubuntu 18.04.4 today and so far I'm liking it.

There is one thing I'm not sure about, and that's updating software. I like to use Gimp, the one in the Software store is a little out of date, how do I get the latest version without breaking my fresh install?

---

### Post by yetimon_64 on 2020-02-19
> **oldbob2 said:**
> Hi all,

another user who's finally seen the light! 

... I like to use Gimp, the one in the Software store is a little out of date, how do I get the latest version without breaking my fresh install?

Welcome oldbob2, that should really be in a tech thread, but just a quick tip you can use a PPA, personal package archive for gimp.

For example follow the instructions for gimp [[COLOR=#0000ff]--here--[/COLOR]]("https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp"). That should give you version 2.10, up from the normal 2.08 on Bionic.

Any further problems post a thread in New to Ubuntu for example, if you are a new starter.

Regards and good luck with your Ubuntu-ing, yeti.

---

### Post by oldbob2 on 2020-02-19
Thanks for the welcome yetimon_64, and the info re PPA. I'll take a look in the morning.

Apologies for messing up my first post too, advice taken :oops:. I'm not that familiar with OS forums, and coming from 25 years of the Redmond OS 'point and click', everything's quite a steep learning curve.

---

### Post by CatKiller on 2020-02-19
You install and update software through a [package manager](https://en.wikipedia.org/wiki/Package_manager). That will keep all of the software installed through the package manager - OS and applications - up to date. Adding a PPA gives an additional source for your package manager to pull software from.

Security updates and bugfixes get backported for the software in the repositories. You don't need to have the highest version number to get those. Higher version numbers get you new features; if you don't need those features then you don't need the higher version number. Some software will be upgraded to a higher version number through normal updates: the kernel and graphics stack through the Hardware Enablement Stack, browsers because they mix in security updates with feature updates, and software with particularly desirable new features which go through the Stable Release Update process.

Welcome to Ubuntu :)

---

### Post by mastablasta on 2020-02-20
you could also open software sources in software center and then add this new source to it. after software center update the new version will appear in software center for oyu ot pull down.

it's the sam thing that happens if you copy and paste those commands into terminal. oit's just that those ocmmands work the same no matter if oyu use Mint, Ubuntu, Kubuntu, Xubuntu, Budgie...

---

### Post by yetimon_64 on 2020-02-20
> **oldbob2 said:**
> ...Apologies for messing up my first post too, advice taken :oops:. I'm not that familiar with OS forums, and coming from 25 years of the Redmond OS 'point and click', everything's quite a steep learning curve.
No worries, it is all good now oldbob2. It seems the staff have split this out to its own thread now in general help so any problems you have with the PPA or your question in general can be done here. Cheers, yeti.

---

### Post by oldbob2 on 2020-02-20
Thanks to yetimon_64's advice, all is now installed. S'easy when you know how innit! ;).

---

### Post by Dennis N on 2020-02-20
> I like to use Gimp, the one in the Software store is a little out of date, how do I get the latest version without breaking my fresh install? 

To always have the most recent version of Gimp, simply install the Gimp Snap package or the Gimp Flatpak package. I'm using the Flatpak package of Gimp in Ubuntu 18.04.

---

