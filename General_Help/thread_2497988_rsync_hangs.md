---
title: "rsync hangs"
date: 2024-05-25
forum: General Help
---

### Post by Old Jimma on 2024-05-25
Hello Forum:

Once in a while, rsync hangs up and does not complete.

Here is the command I use:

> rsync -azP --delete /home/ollie/ /mnt/Crucial

I'd be greatful for advice on this.

Old

---

### Post by currentshaft on 2024-05-25
?

---

### Post by oldfred on 2024-05-25
What format is /mnt/Crucial?

Space issues? I run this as part of my script, so I know if starting to use too much space.
df -hT -x squashfs -x tmpfs -x devtmpfs

---

### Post by TheFu on 2024-05-25
> **currentshaft said:**
> Throw some v's in there for verbosity? Does SSH work? scp?

His rsync is all local, nothing remote, so ssh isn't involved at all.  The -vvv option would be a good idea.  I didn't look up the other options to know if they make sense with the --delete usage.  

Compressing isn't useful for local rsync commands, however. It just wastes CPU. Don't use it for local stuff.  For slow networks with files that aren't already compressed, it does make sense.

---

### Post by Old Jimma on 2024-05-25
Hello to all who responded to my concern about rsync haninging.

I checked if the device was mounted. It was.
I checked to see whther sync was being used properly. It was.

What worked was: 
[LIST]
[*]using the disks utility to erase the disk.
[*]
[/LIST]
After that sync worded flawlessly and completed.

Go figure.

I don't really understand it, but that worked.

Thank you for your replies. All them them were very good and provided good ideas to pursue.

Sincerely,
Old

---

### Post by Old Jimma on 2024-05-25
slight correction: 

I deleted the '--delete' option. 

Fu is probably correct. In an initial backup it may not make sense to use --delete option.

---

### Post by aljames2 on 2024-05-25
I would also drop the -z as TheFu indicated since it is local and not over the network. 

The filesystem at your destination matters.  For example, if it is exfat or fat on a USB attached device, the -a can give you troubles because -a is the same as -rlptgoD, and it doesn't like some of those options, especially -D won't work.  Your problem however seems to be irratic, so perhaps your target is a linux filesystem.  

Strange that you had to wipe the disk (or partition) to get it to work, is your destination partition large enough.

Without --delete, rsync will not delete anything at your target, it will just add-to your target. You could try --delete along with the --dry-run (or -n) option.  -n will simulate the rsync and let you see what it will do, before commiting it for real.  If you like the output then you can remove the -n to make it real.  

```

rsync -avn --delete /source/ /destination/ 
OR
rsync -av --delete /source/ /destination/ --dry-run

```

---

