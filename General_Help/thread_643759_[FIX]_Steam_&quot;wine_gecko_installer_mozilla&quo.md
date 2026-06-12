---
title: "[FIX] Steam &quot;wine gecko installer mozilla&quot; crash."
date: 2007-12-18
forum: General Help
---

### Post by drewg on 2007-12-18
Hi,
I got a popup when starting steam to install wine gecko for mozilla.

Here's how I fixed it.

If you've got the latest wine installed from winehq and not synaptic file manager skip to installing steam. If you've installed steam already scroll down to the wine gecko installer bit.

Install wine. (Don't use Ubuntu synaptic package manager to install wine)
- [www.winehq.org](www.winehq.org)
winehq.org

Skip this next process if you want to install steam yourself, using wine, or any other method.

Get wine-doors from [http://www.wine-doors.org/](http://www.wine-doors.org/)

Install steam (using wine doors or other method)
- When using wine-doors it will automatically install steam, it crashed for me, but in the end it did install.

There you go, you have steam.

If you get a wine-gecko install popup when using steam, it will crash.
So do this - 

Install Gecko Engine by running in terminal

```
wine iexplore http://winehq.org
```

If that doesn't work servers are down. But follow the method to install wine-gecko on this website:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554) scroll down a bit and you will see "HOWTO: Installing and Running Steam"
Start from step 3.

Hope I helped anyone with this problem.

If anyone has access to wine-hq forums, or the google group they use, please post it there.

Sorry if this has already been posted. Might as well keep the fix alive anyway.

---

### Post by Zars on 2007-12-18
Thanks drewg!

Bought the Orange Box the other day, so very glad it works on my PC! My problem was that Stream would hang when trying to load as the Gecko installation would crash. Using the 

```
wine iexplore http://winehq.org
```

trick worked though.

Thanks again :D

Zars

---

