---
title: "Installing programs and dependencies offline?"
date: 2018-03-24
forum: General Help
---

### Post by pedrovay2003 on 2018-03-24
I'm kind of new to Linux, so I apologize in advance if I sound a bit ignorant here.

I'm trying to make local, offline backups of the Ubuntu programs that I want to keep. I know that installing a program through the terminal while online is the best way to go about things, so that's what I do. I also know that any dependencies that are downloaded this way are stored in **/var/cache/apt/archive**, and they can be copied to any other folder as backups. The part I'm not understanding is that if I try to install these backed up .deb files using **sudo dpkg -i *.deb**, even in a fresh Ubuntu installation, the vast majority of them fail, even though the same files were installed successfully while connected to the internet and using the terminal.

As as example, the Wine frontend, PlayOnLinux, downloads 25 .deb files into **/var/cache/apt/archive** if you follow the installation instructions [found here.]("https://www.playonlinux.com/en/download.html") However, if I try to manually install those same files offline, nearly everything returns error messages, and the program doesn't work correctly.

There's clearly a difference in installation methods, and being new to the entire Linux world, I don't see what they are. Is there any way to make sure I can make offline backups of everything I need to get programs running, or am I asking for too much? Thanks in advance to anyone who can help me with this.

---

### Post by TheFu on 2018-03-24
dpkg doesn't do dependency resolution.
apt, apt-get, and aptitude will, but all the dependencies need to be available. There are subtle differences in each.

For details about any commands, there is a manual page - manpage.   Those have a set layout which takes time to learn and understand. Took me about 6 months before it "clicked" - after that, it was clear how smart the people were who created manpages.

You can also make a local, shared, cache of installed programs using something like apt-cacher-ng.  I use this to make weekly patching faster, but because all my systems are a little different, the rate of useful savings for the cache really isn't all that great.  I'm patching now (every Saturday morning), but when it finishes, I'll pull the stats for cache hits (good stuff).  I have a mix of releases, architectures and installed programs, so that doesn't help with package reuse. The email server has different programs  loaded than the blog server or my home theatre server.  I don't game and I avoid WINE stuff after it became too hard to get the 2 MS-Windows programs I still use working.  apt-cacher-ng stats from today:

```

Transfer statistics
Period 	Cache efficiency
  	Requests 	  	Data
  	Hits 	Misses 	Total 	  	Hits 	Misses 	Total
2018-03-23 09:03 - 2018-03-24 09:03	 	374 (64.04%)	210 (35.96%)	584	 	44.87 MiB (57.92%)	32.59 MiB (42.08%)	77.46 MiB
2018-03-22 09:03 - 2018-03-23 09:03	 	138 (63.89%)	78 (36.11%)	216	 	7.53 MiB (29.62%)	17.88 MiB (70.38%)	25.41 MiB
2018-03-21 09:03 - 2018-03-22 09:03	 	140 (69.65%)	61 (30.35%)	201	 	5.81 MiB (30.51%)	13.23 MiB (69.49%)	19.04 MiB
2018-03-20 09:03 - 2018-03-21 09:03	 	165 (71.43%)	66 (28.57%)	231	 	13.67 MiB (44.23%)	17.23 MiB (55.77%)	30.90 MiB
2018-03-19 09:03 - 2018-03-20 09:03	 	177 (70.24%)	75 (29.76%)	252	 	18.21 MiB (52.05%)	16.77 MiB (47.95%)	34.97 MiB
2018-03-18 09:03 - 2018-03-19 09:03	 	147 (75.00%)	49 (25.00%)	196	 	3.74 MiB (35.67%)	6.74 MiB (64.33%)	10.48 MiB
2018-03-17 09:03 - 2018-03-18 09:03	 	349 (62.88%)	206 (37.12%)	555	 	38.32 MiB (18.87%)	164.72 MiB (81.13%)	203.04 MiB
```
Appears about 60% of the time, today, the local cache was used.

---

### Post by pedrovay2003 on 2018-03-24
Okay, I think I see what you're saying. I figured that it had something to do with bulk installing everything at once, instead of the dependencies first. Is there a way to specify that you want the dependencies install first if they can be found locally? Thanks for the reply, by the way.

---

### Post by TheFu on 2018-03-24
Not sure I said what you got.  In short, use apt-cacher-ng and pre-load all dependencies into that system.  There may be other methods too, but I've not used them.  Perhaps if you ran your own PPA?  IDK.

---

