---
title: "[SOLVED] Stupid question about rm"
date: 2007-10-30
forum: General Help
---

### Post by Excalibre on 2007-10-30
How do I remove all the files with a particular extension in a directory and its various subdirectories? My music collection has a bunch of winamp playlists with a particular extension scattered throughout and I'd like to remove them all in one fell swoop but I can't find out any parameter for rm to do that.

---

### Post by Prospero2006 on 2007-10-31
Ok, I run several middle school computer labs, and the kids are constantly dropping mp3 files and exe files on the shared storage drive. So, I researched this to get rid of all that:
(Run from the / directory)  --This should erase all .mp3 files for example.
I'll have to verify in the morning, but I think this is right:
```

find -name *.mp3 -exec rm -rf {} ; 

```


Give it a shot, but be careful with scripts like that. 
Pros

---

### Post by argosreality on 2007-10-31
I'd also highly recommend a -i switch with the rm command so it that requires a prompt from you before removal. Its way too easy to cause some nasty damage with rm without it.

---

### Post by tubasoldier on 2007-10-31
It should also as simple as being in the particular directory and typing something like:

```
rm -rf  *.extension
```

the -r option will remove everything recursively. This includes all sub-folders.
the -f option is for force. ignore nonexistent files, never prompt.
the -i option is for prompt before any removal.

so if you want to approve every file being deleted replace the -f option for the -i option.

But yes, be very careful with the rm -rf command. Files are pretty much impossible to recover on EXT3 file systems.

---

### Post by Excalibre on 2007-10-31
tubasoldier: -r was the first thing I tried, because I thought it would do this, but as far as I could tell, all that does is remove a particular directory and all its subdirectories and files. When I tried it, it just complained that "*.m3u" is not a file or directory.

But the find method works. Molte grazie!

---

