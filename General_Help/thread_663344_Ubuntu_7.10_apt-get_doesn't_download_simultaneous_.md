---
title: "Ubuntu 7.10 apt-get doesn't download simultaneous files at a time"
date: 2008-01-10
forum: General Help
---

### Post by sgwong on 2008-01-10
I just install Ubuntu 7.10 and the apt-get is really slow and only download 1 file at a time.

Previously I install Ubuntu 7.03 in Windows XP using Vmware. The apt-get is really fast and stable and it can download simultaneous file at once. Then, I installed Ubuntu 7.10 in a new partition and run without using VMware on WinXP. The apt-get is really slow and it download 1 file at a time.

So, how do I configure the apt-get to download multiple at a time? Download 1 file at a time is really slow. 

Is it the default apt-get configuration for Ubuntu 7.10 to download only 1 file at a time? How come version 7.03 can download multiple time at a time?

My download speed has no problem, I can download and surfing without any problem and with good speed.

Thanks and have a nice day:). (and sorry for my bad english grammer)

---

### Post by manimal347 on 2008-01-10
Um, yes, downloading one file at a time is normal for the Debian packaging system, of which apt-get is perhaps the best known example. Sorry, but I've never heard of or seen apt-get fetch multiple files at once, not in DSL, Ubuntu, or mothership-Debian. It may exist however, and iy you're curious, try reading the apt-get man page ("man apt-get"). As for slow download speeds, you may have just picked a sluggish mirror. Try changing your /etc/apt/sources.list file through editing with nano/vim/gedit or through Synaptic (your choice). Also, that mirror could just be facing an unusually high level of traffic. 

You should see speeds maxing out most residential US broadband connections if you pick a good mirror. Currently, I'm getting about 600k a second, roughly where my cable modem is capped, with bursts at up to 1 megabyte a second.

---

### Post by sgwong on 2008-01-10
OK, may be I mean for the Sypnatic Package Manager, in Ubuntu 7.03, it downloads multiple files at once. But for the 7.10, it only download file 1 by 1.

For the sources.list file, I already set to the source from my country...may be it would be faster if I choose US? I dunno but I might need to try again.

Anyway, thanks for your reply.

---

### Post by nowshining on 2008-01-10
there is no official 7.03 - u prob. made a type - feisty fawn is 7.04.

I've seen apt-get download 2 files at once before - it's rare and random on my machine.

Synaptic package manager is a GUI that uses apt-get and it's commands and functions in the background.

---

### Post by jken146 on 2008-01-10
If the problem is slow download speeds, try changing the mirror.  Ideally use one in your country.  Downloading one package at a time as opposed to two simultaneously should not make a difference as long as the overall speed is the same, so try changing your mirror and see if that helps.

---

