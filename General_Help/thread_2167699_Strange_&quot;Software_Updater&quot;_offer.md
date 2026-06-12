---
title: "Strange &quot;Software Updater&quot; offer"
date: 2013-08-14
forum: General Help
---

### Post by linbu on 2013-08-14
Software Updater

Updated software is available for this computer. Do you want to install it now?

Details of updates;
Does not show what is to be downloaded and installed, the entire white area is blank (no details).

Technical description;
Also shows nothing (no description).

Is this normal? I got this 2 days ago and have been using the "Remind Me Later" button, hoping perhaps the update notice itself would be updated.

92 kB will be downloaded, is the only clue.

Software Updater has worked perfectly before and I never noticed anything coming through without any description until now, so just wondering if I should do the install, or be suspicious and not do the install.

---

### Post by Rex Bouwense on 2013-08-14
Yes.  That happened to me as well.  Being of a suspicious mind, I closed the updater and opened a terminal to use
```
sudo apt-get update
sudo apt-get upgrade
```
No biggie.

---

### Post by linbu on 2013-08-14
Thank you Rex. That worked for me.

---

### Post by ljerams on 2013-08-17
And me also.

Thanks Rex

---

### Post by Rex Bouwense on 2013-08-17
Cut it out guys you are making me feel good.  Seriously, we sometimes forget that Ubuntu and its derivatives have three ways to update.  Besides the good old Software Updater, we have Synaptic Package Manager and apt-get.  If one isn't doing what we want, use another.:popcorn:

---

### Post by The Cog on 2013-08-17
Ah, it happens to you too, on Lubuntu! I was thinking maybe it was just an Xubuntu bug.

---

### Post by ibjsb4 on 2013-08-17
[Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=") is my first choice; it would make a good backup package manager for you.

---

### Post by Rex Bouwense on 2013-08-17
> **The Cog said:**
> Ah, it happens to you too, on Lubuntu! I was thinking maybe it was just an Xubuntu bug.
Yes.  It has been doing that lately and I want to know what I am downloading so I use the terminal.
> Synaptic Package Manager is my first choice; it would make a good backup package manager for you. 
They all work.  Everyone has their favorite.  I just wanted to insure that they knew that there was other ways to update.

---

