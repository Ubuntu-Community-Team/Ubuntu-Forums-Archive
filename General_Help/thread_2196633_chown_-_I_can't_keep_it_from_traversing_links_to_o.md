---
title: "chown - I can't keep it from traversing links to other partitions. Why?"
date: 2013-12-30
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-12-30
I assumed chown would default sensibly to NOT crossing links to other partitions. Dumb assumption. I studied the man and the --help and internet crib sheets, all of which SEEM to say that:```
 sudo chown -R -P -h --preserve-root -v me:me /home/me
```should NOT cross out of the partition that /home/me is in, or for that matter, cross any kind of link to something outside of that directory. But it doesn't work that way. I keep links to other partitions in ~/. By links, I mean directories that the other partitions are mounted to. Maybe "links" isn't the right word. I have a thunar action to call a script to chown to me:me, recursively in the case of directories, any files I have selected. Is there an easy way to keep chown from crossing into other filesystems?

 In a script I can compare```
stat -c "%d" $FILE
```with```
stat -c "%d" $FILE/../
```and not chown if they aren't the same but that way I can't use the -R with chown but would have to write something that handles the recursion by by cd-ing to the subdirectory if the stat outputs are the same and starting over in the subdirectory for each subdirectory. Offhand that sounds like something that could be done but would be terribly hairy, as I'd have to keep track of every eligible subdirectory. If that is the only way it can be done I'd probably need to write a script that could call multiple instances of itself. That sounds like a several day project. Alternately, I could start by simply unmounting every partition except the one the active system is on. The problem with that is that I'll often want to use this on files, which could include directories to be dealt with recursively, on other partitions. I could umount everything but that partition and the system partition. I can't think of any circumstances in which I'd be likely to have another partition mounted to a folder in a third partition, so probably that would work for me. But it is somwhat inconvenient, as I'd probably need to remount something after running it, it's certainly neither elegant nor foolproof since such mount points ARE possible even if I can't at the moment think of any reason to make one. If chown could be confined to the same filesystem the selected files are on, that would seem the sensible way to do it. If one of those is or contains a directory to which some other filesystem is mounted or something is linked I'd prefer it to chown only the folder or link, not the stuff it points to or is mounted to it. Is this possible?

I think I just totally borked my other system by inadvertantly chowning the whole darn thing. Hmmm. Too late now, but I think a script to check all permissions on a system and automatically construct a script or a data file that can be used by another script to restore all perms, might be a good precaution against surprises like this. Does something like that already exist?

---

