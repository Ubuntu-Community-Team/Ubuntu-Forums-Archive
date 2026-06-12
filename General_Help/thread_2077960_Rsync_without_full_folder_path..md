---
title: "Rsync without full folder path."
date: 2012-10-29
forum: General Help
---

### Post by Trapper on 2012-10-29
I am no rsync pro but I do get by. I am having a problem though that I am unable to figure out.

Let's say I have /home/trapper/archives and I want to backup the contents of the archives folder and all it's subfolders to /media/storage

Everything I have tried ends up with a /media/storage/home/trapper/archives + subfolders scenario. All I am wanting is a /media/storage/archives + subfolders scenario.

Obviously I am unaware of a switch that rsyncs a source target to a backup target without including the path to the source target. Right now I am using:
 
```
rsync -arvRO --delete 
```but that includes /home/trapper/  folders at the backup.

---

### Post by markbl on 2012-10-29
If you have a problem with a command then it is best to tell us what the exact command line looks like.

Anyhow, it just seems you should not add the -R option. Take if off and try again. BTW, the rsync man page describes all this fairly well, see the words under the -R option.

---

### Post by Trapper on 2012-10-29
> **markbl said:**
> If you have a problem with a command then it is best to tell us what the exact command line looks like.

Anyhow, it just seems you should not add the -R option. Take if off and try again. BTW, the rsync man page describes all this fairly well, see the words under the -R option.

Sorry, I guess I just got a little lazy there and figured it would be assumed the 

rsync -arvRO --delete would be tied to the paths I had already referred to.


Thanks for the -R tip. I had read the man several times and breezed right over the relative path and was probably twisting it and absolute around. Anyhow, eliminating the -R did the trick and I now get what I am wanting. Thank you.

---

