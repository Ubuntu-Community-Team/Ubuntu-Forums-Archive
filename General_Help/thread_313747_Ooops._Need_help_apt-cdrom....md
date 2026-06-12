---
title: "Ooops. Need help apt-cdrom..."
date: 2006-12-06
forum: General Help
---

### Post by Get_Ya_Wicked_On on 2006-12-06
Hi all.

While running a routine "apt-get update", I noticed it was taking a while.

Then I noticed it was trying to update my system to Feisty!

I have no clue how my sources all got changed from 'Edgy' to 'Feisty' but...


So anyway, I changed them all back to 'Edgy' but the cdrom still gives me trouble.

```

Fetched 6B in 1s (3B/s)

Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 

(20061025.1)]/dists/edgy/main/binary-i386/Packages.gz  Please use apt-cdrom

to make this CD-ROM recognized by APT. apt-get update cannot be used to add

new CD-ROMs

```

I was wondering if anyone could tell me how to get my install cd working again with apt-cdrom?

---

### Post by eriefisher on 2006-12-06
Place the CD in the tray, 

sudo apt-cdrom add

This should add it to apt, but if you have been updating it will pobably be of no use to you.

---

### Post by Get_Ya_Wicked_On on 2006-12-06
If you mean if I updated to Feisty, I haven't

I just updated my packages, which then made 561 updates available.

But I changed all my sources and didn't touch one of the updates.

---

### Post by eriefisher on 2006-12-06
The packages on the cd probably have been updated and if you are current the old versions are of no use.

---

### Post by Get_Ya_Wicked_On on 2006-12-06
Does it make a difference if I never touched my original install cd during this whole fiasco?

---

### Post by eriefisher on 2006-12-06
You shoundn't really need again except for rescue. You can get rid of the message by:

sudo gedit /etc/apt/sources.list

find the line for the cd and place a # in front of it. You should no longer see the message.

---

### Post by Get_Ya_Wicked_On on 2006-12-06
But what if a package I need is on my install disc?

It asks me for it very often...

---

### Post by eriefisher on 2006-12-06
There probably is an newer version available from the repos. By editing the sources.list you won't be asked for the CD.

---

### Post by Get_Ya_Wicked_On on 2006-12-06
Oh, ok. So the cd is just an alternative manner.

As long as I can get the same stuff on the repos, off to # the cd...

I appreciate your help, by the way.

---

### Post by eriefisher on 2006-12-06
Most packages have more than likely been updated. It's usually better to stay with the most current unless there is a problem.

---

