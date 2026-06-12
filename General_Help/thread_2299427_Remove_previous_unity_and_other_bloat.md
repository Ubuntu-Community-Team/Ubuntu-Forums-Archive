---
title: "Remove previous unity and other bloat"
date: 2015-10-18
forum: General Help
---

### Post by Afnan on 2015-10-18
Hello there I was having some issue with unity search where my computer would freeze or hang after searching on unity, after googling I used this code:

```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

```

This seems to have fixed the issue but previously my drive was 12.7GB used/occupied now its 14.7GB occupied. I would like to know if there are two instances of unity running if so how do I disable and remove the previous buggy one? If two unity aren't running but there are two unity on my PC then I would also like to know how to remove the previous one. I have synaptic package manager on my machine I just need to know what I should remove and if it is safe. Thank you

---

### Post by ian-weisser on 2015-10-18
Use the 'ps' command to discover if you have more than one instance of Unity running. It's highly unlikely.

Here's what it should look like:
```
$ ps -e | grep unity
 1916 ?        00:00:00 unity-settings-
 1928 ?        00:00:00 unity-panel-ser
 1991 ?        00:00:00 unity-fallback-

```

Since your code doesn't include any of the system responses, it's impossible to determine exactly what your actual problem was, nor what what your solution actually did, nor what additional packages you may have installed.

Having two 'unity' packages on your system is impossible without a great deal of effort to damage your system first. And that still doesn't mean both would run simultaneously, nor that one would consume 2 GB of space.

Use the 'Disk Usage Analyzer' application to determine what you are using your hard drive space for.
Don't delete anything unless you understand exactly what you are deleting and why. Randomly deleting packages is a quick way to irrecoverably destroy your system.

---

### Post by vasa1 on 2015-10-18
Shouldn't```
sudo apt-get install --reinstall ubuntu desktop
```have given some sort of error?

---

### Post by ajgreeny on 2015-10-18
> **vasa1 said:**
> Shouldn't```
sudo apt-get install --reinstall ubuntu desktop
```have given some sort of error?
Yes it should have done so; there is no package avaiolable to install called either **ubuntu** or **desktop**, but there is, of course, a package called **ubuntu-desktop** (note the dash or hyphen).

---

### Post by mc4man on 2015-10-18
The total size of unity & it's supporting/additional packages is probably less than 20Mb so not your issue
(and no, you cannot have 2 unity versions installed at once
ubuntu-desktop does have quite a number of recommends that could take up some space though again nowhere near 2GB
Use the disk usage app as mentioned & also clean the package archives
sudo apt-get clean

---

### Post by Afnan on 2015-10-19
> **vasa1 said:**
> Shouldn't```
sudo apt-get install --reinstall ubuntu desktop
```have given some sort of error?
Sorry my mistake it was **ubuntu-desktop **not ubuntu desktop



and yes thank you all, there was not two instances of unity running. The bloat was created by residual configs and other obsolete dependencies and such other packages with these codes:

```

sudo apt-get autoclean

sudo apt-get clean

sudo apt-get autoremove

```

This cleared up a lot of space and now its back to 13GB which is normal and OK.

Now what was actually causing unity to hang was **I SUSPECT **was the _ICON THEME NUMIX CIRCLE_. After reinstalling the ubuntu dekstop and unity I still had another crash, and then I went to software updater and it offered me update for numix circle icon theme which I installed then restarted my machine and voila! PERFECTION, works smooth, fast and exactly like how I am used to with my ubuntu no problem at all. Been checking and testing for over 24hr+ and no issues so hopefully its fixed permanently. Now when I checked my software & updates setting on my system settings; under updates tab I noticed "When there are other updates" is set to "Display Weekly" which I changed to "Display Immediately" now I believe the update will be notified instantly and after updating I will not face this type of issues in the future. Thank you all for the support. If anyone faces similar problem try and implement what I did about the Icon updates and hopefully it will be fixed.

---

### Post by vasa1 on 2015-10-19
> **Afnan said:**
> ...
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```
...
BTW, *apt-get clean* is more thorough than *apt-get autoclean*, so if you intended running *apt-get clean*, there was no need to run *apt-get autoclean* first.

*sudo apt-get autoclean* removes debs from */var/cache/apt/archives* for software that has been uninstalled  
*sudo apt-get clean* is stronger than autoclean and removes *all* debs from */var/cache/apt/archives*

---

### Post by Afnan on 2015-10-19
Thank you so much for the explanation!! :D

---

