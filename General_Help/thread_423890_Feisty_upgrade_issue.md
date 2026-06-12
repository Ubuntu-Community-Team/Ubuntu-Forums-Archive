---
title: "Feisty upgrade issue"
date: 2007-04-26
forum: General Help
---

### Post by Stonecougar on 2007-04-26
Hey all, I've been trying to perform an online upgrade from Edgy to Feisty. When I do, it gets partway through fetching the required packages, then comes up with an error that says "A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry." Then it spits out the following:

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

Well, there's not a thing wrong with my network, so far as I can tell. I haven't tried installing off my live CD yet, but if I have to, I will.

---

### Post by pooslinger on 2007-04-26
1. Those aren't official repos, check the source.
2. Edit for feisty : [http://wine.budgetdedicated.com/apt/dists/](http://wine.budgetdedicated.com/apt/dists/)[COLOR="Red"]**edgy**[/COLOR]/main/binary-i386/Packages.gz

comment those sources out, then upgrade Wine separately.

---

### Post by Stonecougar on 2007-04-26
Right then... um... please forgive my noobery, but... how do I do that? I don't really know what I'm doing; most of the changes I've affected to my system have been following step by step how-to's.

---

### Post by zvacet on 2007-04-26
```
gksudo gedit /etc/apt/sources.list
```

comment (put # sign in front of line) [http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz)

---

### Post by Stonecougar on 2007-04-28
Well, it installed smoothly enough. I was able to walk away and do stuff over the day while it did so. When I tried to finish up last night, it was broken. I'd try to boot, and it would freeze. Never in the same place, but always so early that I wasn't able to do anything. Most of the time, I couldn't even get past the login screen; once, it even froze on the Nvidia splash screen. I had upgraded online, rather than with the CD. When I tried to put the CD in to try and at least boot in long enough to recover my data, it sat there with the little orange bar bouncing back and forth for probably a good 10 minutes or so, and then finally said that there was a soft crash error on the CPU, or something to that effect. So far as I can tell, I'm going to have to pull the main drive, install 6.10 on the secondary drive, replace the main to recover the data, and either go back to 6.10, or switch back to Windows. Any suggestions?

---

### Post by pooslinger on 2007-04-29
What did you run to edit sources.list?


Boot. press "e" when GRUB loads.  Delete "quiet" from the end of the boot options.  It will show you where it is stopping.  You can also ctrl-alt-f1 to see what is loading during the regular splash screen.

---

### Post by Stonecougar on 2007-06-16
So, after a hectic month and a half of school, I can finally devote my attention back to Linux. 

Removing the "quiet" entry and using ctrl+alt+F1 didn't do anything constructive. I installed Edgy on my secondary drive, turned that to master, and couldn't get into the files on the other drive. I'm rusty as hell now, and I don't remember any of my terminal commands or anything. Please help!

---

