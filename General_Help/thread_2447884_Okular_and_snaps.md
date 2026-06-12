---
title: "Okular and snaps"
date: 2020-07-27
forum: General Help
---

### Post by kurt18947 on 2020-07-27
I hope this is the right place for this. If not, please feel free to move it. I've followed a thread about snaps and Okular and got curious. I've installed Okular in the past and it has worked well so decided to revisit it, plus check out snaps for myself. I was able to install the Okular snap with no problem at all. It did take several seconds to start up the first time. Subsequent starts were instantaneous. Logging out did not cause a noticeably slow boot. This is on a machine with Ryzen 5 processor and NVMe drive which probably doesn't hurt. 

What I would like to fix is what folders are listed by Okular to find files to open. Right now I have Home, Trash, (remote)Network, modified today, modified yesterday, documents images, audio, videos. If I click on Home, it doesn't take me to my Home folder. If I type a path in the Name line I can find files to open. I would like to have Okular list folders like a file manager does - Home Desktop Documents etc. Anyone have a thought about how to accomplish that? My searching has not been fruitful. Thanks in advance.

---

### Post by HermanAB on 2020-07-28
Hmm, Snaps were intended to be a kind of copy of the way Apple handles packages, but something went amiss in the translation.  So until the kinks are worked out, I give Snaps a miss.  Ye Olde Fashioned "apt install whadeva" still works better.

---

### Post by Dennis N on 2020-07-28
This snap is an odd piece of work. After clicking 'Home' under places, click the '>' at start of the path. In the dropdown, you can select 'home' which will present your home folder. or your user name, which shows home folder contents. Click '/' takes you to root of the file system, from where you can navigate to other places to open files.

I use the Flatpak version instead. That, or the repository version, might be a better choice for ease of use.

---

### Post by grahammechanical on 2020-07-28
From Ubuntu 18.04 onwards once a snap application is installed we can find the app in Ubuntu software and there we are given some settings that we can change. I am not sure if this is possible in Kubuntu. Okular is a KDE app after all.

Regards.

---

### Post by kurt18947 on 2020-07-30
> **Dennis N said:**
> This snap is an odd piece of work. After clicking 'Home' under places, click the '>' at start of the path. In the dropdown, you can select 'home' which will present your home folder. or your user name, which shows home folder contents. Click '/' takes you to root of the file system, from where you can navigate to other places to open files.

I use the Flatpak version instead. That, or the repository version, might be a better choice for ease of use.

Thanks Dennis. I don't have Okular installed on this machine but I'll try this when I get home. I like the idea of not adding dozens of KDE dependencies to my main machine. Being able to delete an app and all its dependencies seems like a nice idea.

Edit: Okay, I got home and tried the above. It does work.

file -> open -> home -> [>] symbol to the left home user name -> user name opens the customary list of folders. It does seem like once I click along a path, that path is remembered.

---

