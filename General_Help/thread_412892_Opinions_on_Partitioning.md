---
title: "Opinions on Partitioning"
date: 2007-04-18
forum: General Help
---

### Post by Raptor45 on 2007-04-18
I've been (happily) running Ubuntu Feisty for some time since alpha, but I plan to reinstall when the final release comes. Along with the reinstall, I've been thinking about changing around my partitioning.

I have two hard drives, a 100GB (currently pure NTFS for windows), and a 60GB (currently 20GB ext3 for linux, swap, and the rest as NTFS storage).

I've been thinking about doing a 10 GB root, 1GB swap, and leaving the remaining 49GB to home, then adding ext3 functionality to windows so I can access home.

Some people recommend making a separate partition for home like this, but what is the real reasoning behind that? I guess its possible to reinstall without having to backup, but it seems pretty easy to me to just simply burn my files to a CD and wipe it. I've also heard recommendations about making other partitions for other directories?

---

### Post by Oki on 2007-04-18
/ 	20gig(then you can install a lot of programs)
swap 	Your ram x2
Home 	As much as you can/want

ext3 is a good filesystem, stabel – but not the fastest. I have the same. 

*Some people recommend making a separate partition for home like this, but what is the real reasoning behind that?*
So it is more safe to do upgrades later(or change distro); if something goes wrong you can easily fix it without being worried about your data or settings. Remember; some had problems with last upgrade. 
[I]
I've also heard recommendations about making other partitions for other directories?[/I]
Me to, some want to have different filesystems for different parts of the system. But I have also been told by more advanced users that it is not necessary today – so I have only 3  partitions(and one extra where I store my music, since amarok works faster that way).

---

### Post by moon2js on 2007-04-18
If I'm setting up a home server for me and maybe one other person to practice/experiment/develop with rails apps (http server, mysql, php, ruby, etc), should I make a separate partition for /var or /var/logs?

I normally don't bother with any separate partitions except /home, and this is by no means a mission-critical server, but it would be annoying if some cranky web app brought it down and I can't remote it to get files or try to fix it.

---

### Post by Raptor45 on 2007-04-18
> **Oki said:**
> swap 	Your ram x2

I've heard this can be overkill?

---

### Post by Oki on 2007-04-18
Yes, some will say that 512mb is more then enough, otheres will stick with the x2 rule. But I dont find this so importent since the different are so small, and it cant do no wrong to have a to big swap file.

---

### Post by moon2js on 2007-04-18
I've been monitoring my memory usage on a slightly sluggish system that has 768-mb of physical RAM. The RAM is usually completely used (which is good), but the swap is generally untouched or a flat/constant very low usage (which I think is also good or at least normal).

I take it this is ideal behavior, but I'm wondering what would have to do to get the system to actually use the swap, not that I'm trying so hard to use the swap, more that I'm just curious.

---

### Post by Oki on 2007-04-18
I dont know. Try to open a lot of programs and then shut them down, I guess the system will(if need for more free ram)put the files from memory onto the swap file. Perhaps try the quickstarter in OOo, start the program and shut it down. But I as I said, I dont know.

---

