---
title: "Best tool for file/dir synchronisation?"
date: 2013-02-01
forum: General Help
---

### Post by sugarat on 2013-02-01
I keep a backup copy of my files on a separate backup server and every few days, or whenever takes my fancy, I run a synchronisation tool to mirror my files onto the backup server. 

The main requirement is not a silent synchronisation of the directories however, as I need an overview of what changes have been detected so that I can examine this before committing to the synchronisation. I have had instances in the past where files were accidentally deleted, and the changes were then propagated to the mirror, so I specifically need the tool to show me what files have been deleted before it deletes them from the backup. 

I've tried rsync, but I can't reach a place where it clearly shows me what files it would delete on the destination. 

Thanks

---

### Post by sudodus on 2013-02-01
Try ***Unison***. It is in the repositories.

See this link
[[COLOR="Red"]http://www.cis.upenn.edu/~bcpierce/unison/[/COLOR]]("http://www.cis.upenn.edu/~bcpierce/unison/")

---

### Post by btindie on 2013-02-01
What options were you using with rsync?

If you specify --dry-run it'll tell you what it would do, you can then filter the output through grep to just see which ones it would delete, i.e.
```
rsync --dry-run -avh --delete src/ dst/ | grep ^deleting
```

The below example is for when I deleted the file README from the src directory and tried rsyncing back to dst.
```
root@localhost:/tmp$ rsync --dry-run -avh --progress --stats --delete src/ dst/ 
sending incremental file list
deleting README
new/
deleting new/README

Number of files: 6
Number of files transferred: 0
Total file size: 9.99K bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 150
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 167
Total bytes received: 16

sent 167 bytes  received 16 bytes  366.00 bytes/sec
total size is 9.99K  speedup is 54.57 (DRY RUN)
```

---

### Post by sugarat on 2013-02-01
> **sudodus said:**
> Try ***Unison***. It is in the repositories.

See this link
[[COLOR="Red"]http://www.cis.upenn.edu/~bcpierce/unison/[/COLOR]]("http://www.cis.upenn.edu/~bcpierce/unison/")

Okay will do, thanks!

---

### Post by sudodus on 2013-02-01
> **sugarat said:**
> Okay will do, thanks!

You are welcome :-)

Good luck, and if you have problems or questions how to use it, please come back to this thread!

---

### Post by sugarat on 2013-02-01
> **btindie said:**
> What options were you using with rsync?

If you specify --dry-run it'll tell you what it would do, you can then filter the output through grep to just see which ones it would delete, i.e.
```
rsync --dry-run -avh --delete src/ dst/ | grep ^deleting
```

The below example is for when I deleted the file README from the src directory and tried rsyncing back to dst.
```
root@localhost:/tmp$ rsync --dry-run -avh --progress --stats --delete src/ dst/ 
sending incremental file list
deleting README
new/
deleting new/README

Number of files: 6
Number of files transferred: 0
Total file size: 9.99K bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 150
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 167
Total bytes received: 16

sent 167 bytes  received 16 bytes  366.00 bytes/sec
total size is 9.99K  speedup is 54.57 (DRY RUN)
```

Ah that's odd, I couldn't get that to work before, but doing that command line with the grep is just the ticket. Thanks!

---

### Post by zSeries on 2013-02-01
I have been using FreeFileSync on Windows and Ubuntu for years. GUI based and never had a problem with it. I would prefer it over a command based program (eg rsync) if you want to review the changes before doing the sync.

---

### Post by sudodus on 2013-02-01
Sometimes I use rsync directly, and sometimes I use rsync via the user interface Unison.

Example using the GUI
```
cd .unison
```
```
sudo unison-gtk syncro-1.prf
```
will give you a visual view what will be done.

*Edit*: you have to create the set-up file syncro-1.prf.

---

### Post by sugarat on 2013-02-01
> **zSeries said:**
> I have been using FreeFileSync on Windows and Ubuntu for years. GUI based and never had a problem with it. I would prefer it over a command based program (eg rsync) if you want to review the changes before doing the sync.

Thanks for the recommendation. It looks similar to a program called Allway Sync I have used for years on Windows. Now that I am running Linux on my servers though I thought it best to use something native and fast. Also, because my main work desktop is a Windows box it's a bit fiddly to bring the Ubuntu desktop back here.  Something I can run on the command line is preferred. 

I think now that I have rsync telling me what it's going to delete on the dry runs, I'll just use that. Nice and fast and no messing with VNC/X11 for remote GUI stuff. 

Thanks

---

