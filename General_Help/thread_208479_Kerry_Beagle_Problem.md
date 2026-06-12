---
title: "Kerry Beagle Problem"
date: 2006-07-03
forum: General Help
---

### Post by wyth on 2006-07-03
Hiyas all around.

I've recently installed Kerry Beagle on my Kubuntu Dapper, and am running into a bit of a problem.  It's not finding a darn thing.  I've set up Beagle before in Gnome, and have libbeagle installed and files on the indexing list, it's set to run at start-up and it runs, but every search comes up  :neutral:  blank.  

So there must be some sort of configuration I'm just too dense to find.  I've spent a couple hours now combing forums and looking for set-up how-tos, to no avail.  

So if you've gotten Kerry Beagle to successfully operate and know the mechanics behind it, would you mind posting your wisdom?  I and I'm sure some others would appreciate it.

Cheers.

---

### Post by cptnapalm on 2006-07-04
I'm having a beagle related problem too.  What output do you get if you run beagle-search from the command line?

---

### Post by wyth on 2006-07-05
[QUOTE=cptnapalm]I'm having a beagle related problem too.  What output do you get if you run beagle-search from the command line?[/QUOTE]

When run from the command line (beagle-search), I get:

[INDENT](search:5662): Gdk-WARNING **: locale not supported by Xlib

(search:5662): Gdk-WARNING **: cannot set locale modifiers
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Could not load spinner image
/bin/sh: /usr/bin/esd: No such file or directory[/INDENT]

And then a search window pops up.  I'm currently logged in under my accound, which at least finds things in my home folder, but under my wife's account, nothing comes up, not even the stuff in her home folder.

So that's where I'm at with this stuff.  As far as I can tell, it's all set up correctly, with identical indexes for both accounts, but it only seems to search some of those in my account, and none in my wife's.

For what it's worth, I have a fat32 partitition with all my mp3's on it.  This partition is in the index, but it never finds a thing.  I haven't looked for this yet, but does Beagle not search fat32 partitions?

---

