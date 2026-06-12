---
title: "How to restore a backup on a different system?"
date: 2012-10-30
forum: General Help
---

### Post by applepiefork on 2012-10-30
Hey folks, 

i'm a Linux noob. So, i get stuff installed and updated, but don't know what to do when problems arise.

My gf's thinkpad just broke, apparently a motherboard failure; it's already shipped for warranty repair. However, of course there is *important* data which needs to be restored before the weekend on the external hard drive. 

So, she used the build-in Ubuntu (12.04) backup program, i don't know which that might be (deja dup? something different?). On the external drive we do find a lot of files named like
duplicity-full.20121012T123017Z.vol1.difftar.gz and one corresponding .manifest file as well. 

And now the big question: How to get to this data?

On my second laptop, i got Linux Mint (12) installed. After searching the net, i found and typed this into the terminal:
```
for t in duplicity-full.XXXInsertNumberHereXXX.*.difftar.gz; do tar xf $t; done

```

It took a while, but i ended up with a "multivol_snapshot" folder and a "snapshot" folder. However, apparently not all files were restored, some of the important stuff is still missing. 

What am I doing wrong? Any suggestions?

Any help would be greatly appreciated.
Greetings,
 Sebastian

---

### Post by applepiefork on 2012-10-31
Okay then, got everything restored. It was just a matter of using the correct backup application. 
As Linux Mint gives me 2 different ways of performing a backup, of course i first tried the wrong one - simply called "Datensicherung" (in german, maybe "Data backup"?), which after 10 hours (!!) finished with a "multivol_snapshot" and "snapshot" folder as well, as well with missing files (as stated above). 
Then there was the "Backup" - setting (!, confusingly not to be found under applications), where i was able to choose "restore" and restore the entire backup. 

Is there an easy to handle (!) backup solution where it's possible to restore a single file/folder instead of the entire backup?
(the Deja-Dup - solution of recovering a single file doesn't help here, where i needed to restore a single file/folder to a *different* system)

s.

---

### Post by Ghost_Mazal on 2012-10-31
Not sure how you gonna do that now with that current backup files to a different system.

But for future reference look into rsync / grsync for backups. It makes straight copies
of your files and makes it very easy to get just 1 file to any other system restored.

Your problem is exactly the reason why I don't like "backup programs". It's always an issue when you need just a few files restored to another system that doesn't run that exact same backup system.

---

