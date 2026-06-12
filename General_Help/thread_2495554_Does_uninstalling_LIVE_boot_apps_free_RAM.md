---
title: "Does uninstalling LIVE boot apps free RAM?"
date: 2024-02-22
forum: General Help
---

### Post by johsal on 2024-02-22
If I uninstall Firefox because I do not need a browser, what system resources are freed if any in a live, read-only boot?

---

### Post by guiverc on 2024-02-23
I would expect none...

A *live* system is COW or COPY ON WRITE, thus changes are made via additional details being created that OVERWRITE/REPLACE the prior details (also in RAM)...

ie as changes are COPIES, nothing is actually deleted (firefox was included on the ISO; thus exists as read-only) thus its a change that needs to be recorded in RAM so that records the deletion.

I just booted a Lubuntu *noble* (24.04) daily; opened a terminal and run 

```

free

```

then removed `firefox`, which is a *snap* package on *noble*, thus 

```

snap remove firefox

```

then waited a bit, then re-ran the free command

The amount of USED RAM has increased (*slightly*)..  the original image is READ ONLY, and I actually made no CHANGES except the system had to record the removal of the `firefox` snap package, so that was recorded.  Sure a `snap list` command will show fewer results, but I didn't actually gain RAM - it's a *live* system intended for quick fixes, or TESTING out the product prior to install.

If you keep using a *live* system, eventually RAM will run out due to your *changes* (whatever they are), and re-starting the system is the fix; but it's not a normal installed system, as COW (copy on write) isn't the choice for efficiency (*in relation to RAM*)

Please note:  I'm no expert; I've not explored RAM usage close enough (*nor looked at the code*); I'd have to compare a booted system without any changes in say 10 minutes, and contrast that with one that had `snap remove firefox` run as a real test, which I didn't do.  I did run `free` a couple of times, and noted the RAM was slowly reducing anyway; so results of `snap remove firefox` could have been NO CHANGE to RAM.

FYI:  I also removed a *deb* package, the increase in RAM was more sizeable for that package removal contrasted to the *snap* package; though *snap* package I removed is actually larger on disk (*on an installed system anyway*)

---

### Post by johsal on 2024-02-23
> **guiverc said:**
> I would expect none...

A *live* system is COW or COPY ON WRITE, thus changes are made via additional details being created that OVERWRITE/REPLACE the prior details (also in RAM)...


Thoughtful response. 

I get we can summarize that package removal is more likely to *increase* RAM usage because other than ending a process it is our activity that consumes RAM, not any read-only boot app for its mere presence.

I would try to make a custom ISO without the browser (which obsoletes fairly quickly), but if that would not free RAM it wouldn't be worth the effort. 

Next question as a user who stays back OS updating is how much more processing & RAM is demanded by updates. 

I boot mostly Xenial (16) & Fossa (20) & do not know the system resource discrepancy, assuming older OS are lighter as is the case for anyone weened on Redmond. 

I prefer not to boot new OS just for browsers.

---

### Post by guiverc on 2024-02-24
> **johsal said:**
> 
I boot mostly Xenial (16) & Fossa (20) & do not know the system resource discrepancy, assuming older OS are lighter as is the case for anyone weened on Redmond. 

I prefer not to boot new OS just for browsers.

Ubuntu 16.04 LTS is way past it's EOL ; refer [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)  but I guess you're offline & thus aren't worried about security.

I don't think older software is more *lean*, though that is often the way... Newer features (*such as ability to deal with HiDef/4K etc does mandate larger addressing, let alone allowing the system to cope with different resolution screens (scaling) takes computation & RAM to execute*).

If I wanted updated software on a *live* system, I'd just use a *daily* image..  I mentioned grabbing and using a Lubuntu *noble* daily, ie. software that was up-to-date maybe 8 hours before I actually ran the test (*actually up-to-date at the time the daily was built anyway*).  I could have booted the current *jammy* daily as easily, as with [22.04.4]("https://fridge.ubuntu.com/2024/02/22/ubuntu-22-04-4-lts-released/") only recently released, *dailies *are still produced as 22.04.5 hasn't yet been released (*though I've not updated any ISO for jammy since the RC which is now the officially released 22.04.4 ISO** anyway*).

For older systems like *focal*, the last ISO that I'm aware of was produced 2023-March ([https://iso.qa.ubuntu.com/qatracker/milestones/408/builds](https://iso.qa.ubuntu.com/qatracker/milestones/408/builds)) though its still possible more will be produced if another issue causes a 20.04.7 to be required (*it was for 16.04 anyway*)

As you mention 16 & 20 (not 16.04 & 20.04), you may mean the Ubuntu Core images; sorry I'm less familiar with those ... HOWEVER some Ubuntu Core 20 ISOs are still generated, eg. [https://iso.qa.ubuntu.com/qatracker/milestones/435/builds](https://iso.qa.ubuntu.com/qatracker/milestones/435/builds) as the Ubuntu Core (16, 18, 20, 22) have a longer supported life than the standard *deb* based equivalent products (16.04, 18.04, 20.04 & 22.04)

---

### Post by johsal on 2024-02-24
> **guiverc said:**
> Ubuntu 16.04 LTS is way past it's EOL ; refer [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)  but I guess you're offline & thus aren't worried about security.

For older systems like *focal*, the last ISO that I'm aware of was produced 2023-March ([https://iso.qa.ubuntu.com/qatracker/milestones/408/builds](https://iso.qa.ubuntu.com/qatracker/milestones/408/builds)) though its still possible more will be produced if another issue causes a 20.04.7 to be required (*it was for 16.04 anyway*)



I use also Ubuntu-based distros & not just Ubuntu (Xubuntu but I like MATE as well), & what I am worried about besides system resources is DE support.

See, every Ubuntu release supports Lubuntu, Xubuntu, MATE, etc., but that's not the same in other distro families.

They'll have their standard DE then maybe another with enough community support, usually the work of an adept enthusiast, before everyone falls back in line with the standard.

So not only do I have my laborious customizations, I need the non-standard DE (in the case of 14 & 16, XFCE) for a specific distro (not Xubuntu).

I'm using it right now. It's excellent, but too much work. 

So where am I? 32-bit 14.04, 64-bit 16.04 & 20 in a non-standard DE (Ubuntu does not use it).

If 20 were as small with XFCE support I'd use it everywhere.

I know Linux isn't as system-resource heavy as Windows with updates, but Windows indoctrination is severe.

[segue]

They post an Ubuntu image of the most current .iso daily? That I did not know. Thur far I only care about browsers, & the ridiculous fact of no screen saver. Com'on, the basics. 

I may be on the Focal there, appreciate the link.

---

### Post by guiverc on 2024-02-24
> **johsal said:**
> I use also Ubuntu-based distros & not just Ubuntu (Xubuntu but I like MATE as well), & what I am worried about besides system resources is DE support.

See, every Ubuntu release supports Lubuntu, Xubuntu, MATE, etc., but that's not the same in other distro families.

They'll have their standard DE then maybe another with enough community support, usually the work of an adept enthusiast, before everyone falls back in line with the standard.

So not only do I have my laborious customizations, I need the non-standard DE (in the case of 14 & 16, XFCE) for a specific distro (not Xubuntu).



Lubuntu, Xubuntu, and Ubuntu-MATE **are Ubuntu products**, they are just [*flavors of Ubuntu Desktop*]("https://ubuntu.com/desktop/flavours"). 

You may have discovered if you opened the ISO QA tracker links I provided, you can find all *flavors* there too, as all *flavors* of Ubuntu are built by the same infrastructure that builds Ubuntu ISOs, they just use different seed files, eg. for 23.10

- [https://ubuntu-archive-team.ubuntu.com/seeds/xubuntu.mantic/desktop](https://ubuntu-archive-team.ubuntu.com/seeds/xubuntu.mantic/desktop)
- [https://ubuntu-archive-team.ubuntu.com/seeds/lubuntu.mantic/desktop](https://ubuntu-archive-team.ubuntu.com/seeds/lubuntu.mantic/desktop)
- [https://ubuntu-archive-team.ubuntu.com/seeds/ubuntu-mate.mantic/desktop](https://ubuntu-archive-team.ubuntu.com/seeds/ubuntu-mate.mantic/desktop)
- [https://ubuntu-archive-team.ubuntu.com/seeds/ubuntu.mantic/desktop](https://ubuntu-archive-team.ubuntu.com/seeds/ubuntu.mantic/desktop)

where I've listed the Xubuntu, Lubuntu, Ubuntu-MATE & Ubuntu Desktop *seed* files. These *seed* files just cause different packages to be placed on the ISO by the Ubuntu build infrastructure.

As *flavors* of Ubuntu (Lubuntu, Xubuntu etc) only provide 3 years of support; we only build ISOs up to the .5 for LTS; thus the *daily* images get turned off after (lts).5 is released. If an extra ISO is required (eg. [here is an example for 20.04.6]("https://fridge.ubuntu.com/2023/03/23/ubuntu-20-04-6-lts-released/")) the *Ubuntu Release team *ask if *flavors* want to be involved (*if within the 3 years of our support*) & if we opt yes newer dailies will be created for us to QA & thus sign off on; if we opt no then that *flavor* ISO won't be created.  The ISO QA tracker can be useful to find what is created (*esp. if recent; its harder to find things once archived*)

Key though is the Ubuntu *flavors* are still Ubuntu, and thus far closed than a Ubuntu based system (*the Ubuntu builders won't allow non-Ubuntu code as only Ubuntu repositories are searched*).

---

### Post by HermanAB on 2024-02-25
BTW, the fastest and leanest full featured Linux is still Slackware.  It is just as screaming fast as OpenBSD.  

Also, Damn Small Linux is back - though it has put on lots of weight.

Ubuntu has grown so big fat and lazy in its middle age, that I shifted to Devuan.

---

