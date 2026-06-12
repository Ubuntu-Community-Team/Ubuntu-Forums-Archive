---
title: "Problem deleting files with FSlint"
date: 2014-07-24
forum: General Help
---

### Post by pat4 on 2014-07-24
I am running Ubuntu 14.04 LTS.

I have a large number of duplicate files - mainly jpg's - spread across two external hard disks. I want to find and delete the duplicates.

I installed FSlint - I have used it before under 12.04 - and ran the programme. It found the dupes and allowed me to select the ones I wishes to delete but when I hit "delete" nothing happens. 
I ran the prog on each drive individually and it worked OK - finding and deleting dupes. When I ask it to search across the two drives it won't delete anything. 

A search of the 'net found a post from a forum from someone who had a the same problem. It was suggested that the prog should be run as "root". I opened a terminal, typed   gksudo fslnt-gui   (as suggested) and ran the programme again. Still no joy...

Can anyone help me out here please? I know I have correct permissions and access to the drives set as I can create and delete files manually without problem. There are too many files to pick off individually.

Any and all help appreciated.. Thanks.

---

### Post by henkeldg on 2014-08-04
Same problem here. Must be a recent bug, as I've used Fslint many times in the past with no such difficulties. And I can confirm that running it with root privileges doesn't help.

---

### Post by pat4 on 2014-08-10
Thanks henkldg.. I hope someone can find a way to fix the problem. 

Is there a way of reporting such bugs?

---

### Post by freddy5 on 2014-11-06
Same problem, I just find that if you select within groups and then "select all but first" it works. But if you select the other choises nothing happens, at least in my case (ubuntu 14.04)

---

### Post by Lyngbakken on 2015-01-31
I had the same problem under Trusty Tahr (14.04.1) 64-bit. Now I´ve installed an older version of FSlint, and that works like it should.
See: [http://www.webupd8.org/2009/07/fslint-clean-your-linux-filesystem.html](http://www.webupd8.org/2009/07/fslint-clean-your-linux-filesystem.html). Click on ¨download from here¨ in the sentence: The application is in the Ubuntu repositories, so you can easily install it using Synaptic, but a newer version just came out which fixing some bugs which you can download from here.
My syste then warnd me it was an older version than the one in the 14.04 repo´s, but I´ve neglected that warning, because the newer version doesn´t work properly.

---

