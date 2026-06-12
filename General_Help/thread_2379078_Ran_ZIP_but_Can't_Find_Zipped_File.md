---
title: "Ran ZIP but Can't Find Zipped File?"
date: 2017-11-30
forum: General Help
---

### Post by Rick St. George on 2017-11-30
I'm confused! UbuntuStudio v16.04 LTS (updates current) 250GB SSD, 32GB Ram, 8 Core AMD

Ran the following to Zip an Rsync Archive to a external USB WD 2GB Passport. Here is the output showing it seemed to be working. 
However, after finishing, I looked on the Ext. HDD and even searched .. could not find the ZippedArchive.zip file. 

```

sudo zip -r /media/stephen/My Passport/Backups/Mainsys/ZippedArchive.zip /media/stephen/Data/Backups/
<snip>

  adding: media/stephen/Data/Backups/.clamtk/restore (deflated 30%)
  adding: media/stephen/Data/Backups/.clamtk/db/ (stored 0%)
  adding: media/stephen/Data/Backups/.clamtk/db/main.cvd (deflated 0%)
  adding: media/stephen/Data/Backups/.clamtk/db/mirrors.dat (deflated 78%)
  adding: media/stephen/Data/Backups/.clamtk/db/freshclam.log (deflated 90%)
  adding: media/stephen/Data/Backups/.clamtk/db/daily.cld (deflated 62%)
  adding: media/stephen/Data/Backups/.clamtk/db/bytecode.cld (deflated 79%)
  adding: media/stephen/Data/Backups/.bashrc (deflated 54%)
  adding: media/stephen/Data/Backups/.asunder_album_genre (stored 0%)
  adding: media/stephen/Data/Backups/.psensor/ (stored 0%)
  adding: media/stephen/Data/Backups/.psensor/psensor.cfg (deflated 75%)
  adding: media/stephen/Data/Backups/.psensor/log (deflated 93%)
  adding: media/stephen/Data/Backups/.linphonerc (deflated 70%)
stephen@stephen-evo-5723:~$


```

Any ideas?? What did I do wrong? Size of Home Dir. backed-up is 73GB. Size of Free Space on ext.HDD is 685GB.

---

### Post by kostkon on 2017-11-30
Well, all those folders start with . so they are hidden. Just select the option in your file manager to view hidden files and folders.

---

### Post by spjackson on 2017-11-30
> **Rick St. George said:**
> 
```

sudo zip -r /media/stephen/My Passport/Backups/Mainsys/ZippedArchive.zip /media/stephen/Data/Backups/

```

That ought to create the zip file /media/stephen/My.zip along with a warning about not being able to find Passport/Backups/Mainsys/ZippedArchive.zip. You need to quote the archive name or escape the space e.g.
```

sudo zip -r '/media/stephen/My Passport/Backups/Mainsys/ZippedArchive.zip' /media/stephen/Data/Backups/

```

---

### Post by Rick St. George on 2017-11-30
> **spjackson said:**
> That ought to create the zip file /media/stephen/My.zip along with a warning about not being able to find Passport/Backups/Mainsys/ZippedArchive.zip. You need to quote the archive name or escape the space e.g.
```

sudo zip -r '/media/stephen/My Passport/Backups/Mainsys/ZippedArchive.zip' /media/stephen/Data/Backups/

```

I suspected as such ... and sure enough, there it is.

Now if I could just get Rsync to sync within the Zipped File .. that would be cool. As it is, using Rsync, then Zipping to save space and offload it, creates 3 separate copies which is totally unecessary.

Thanks!

---

