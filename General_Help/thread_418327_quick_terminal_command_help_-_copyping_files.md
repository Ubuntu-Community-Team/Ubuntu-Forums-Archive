---
title: "quick terminal command help - copyping files"
date: 2007-04-22
forum: General Help
---

### Post by darweth on 2007-04-22
```
 [bepogi@bepogi ~]$ cp /media/potbelly/audio/unorganized /media/disk
cp: omitting directory `/media/potbelly/audio/unorganized'
 
```

Hey.  I feel like an idiot.  I am trying to copy over the first directory to the second but it is giving me that.  What is the problem exactly?

---

### Post by astoltz on 2007-04-22
try using the cp command with a "-r" flag: ```
bepogi@bepogi ~]$ cp **-r** /media/potbelly/audio/unorganized /media/disk
```

---

### Post by darweth on 2007-04-22
> **astoltz said:**
> try using the cp command with a "-r" flag: ```
bepogi@bepogi ~]$ cp **-r** /media/potbelly/audio/unorganized /media/disk
```

Ah, thanks! It appears to be working! :)  I need to use the terminal because I am copying to a FAT32 partition and getting some problems with FAT32 not being able to handle certain characters in the filename.  Nautilus gives me a pop-up telling me transfer failed but does not identify the file needing a spankin.'  Hopefully this will help me.

**edit**
cp: cannot create regular file `/media/disk/unorganized/Japanese Punk/8 Roof/Yeah If You Can\'t Win/04 Acap?Fatratscreaming.mp3': Invalid argument

Yay.  Found the file in question.  Bad ?.  FAT32 cannot handle that!  I really need an external drive in ext3 instead of fat. :/

---

