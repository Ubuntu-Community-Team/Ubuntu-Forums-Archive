---
title: "Permission denied in Glimpse (probably a snap install issue?)"
date: 2020-09-02
forum: General Help
---

### Post by david503 on 2020-09-02
18.04.5

I installed glimpse via:

sudo snap install glimpse-editor

Everything went fine.  I launch glimpse (via the gnome GUI, not from the CLI) and try to open a file (via file->open) from a mounted partition, it gives me permission denied.  It won't even read the directory.  

I don't have this problem in any other app.  So is it a snap thing or a glimpse thing? Or I guess a combination thereof?

I (deliberately) have the most generic vanilla install of Ubuntu 18.  So that my when I have a problem it isn't exceptional. Well, or is it? Why? Thanks,

TIA

---

### Post by CelticWarrior on 2020-09-02
Yes, it's a snap thing.

Either open the software app, search for your app, click in the permissions button and enable "removable media" or, in terminal:
```
[FONT=Consolas]snap connect glimpse-editor:removable-media[/FONT]
```

---

### Post by deadflowr on 2020-09-02
Note that snaps only give access via removable-media connections to devices mounted at /media, or /mnt.
Devices mounted anywhere else won't have access.

---

### Post by david503 on 2020-09-02
You're the best, @CelticWarrior. Thanks.

---

### Post by david503 on 2020-09-02
> **deadflowr said:**
> Note that snaps only give access via removable-media connections to devices mounted at /media, or /mnt.
Devices mounted anywhere else won't have access.
[COLOR=#000000]
My device is mounted in /media.

[/COLOR]

---

### Post by deadflowr on 2020-09-02
> **david503 said:**
> [COLOR=#000000]
My device is mounted in /media.

[/COLOR]

Most do too.
My note was a "for the record".
As some might have devices mounted at more customized locations, like a created directory named /DATA,
which doesn't exist on a normal Ubuntu.
Devices mounted somewhere like that wouldn't have snap access, whereas a device mounted at , say, /mnt/DATA would.

Snaps also don't handle symlinks (very well or at all, I forget)
So creating a symlink from an off location won't work.
What can work is binding the mount point to one of the snap approved locations.

But that all feels moot, since you've seem to have it figured out.
Which if CelticWarrior's post help solve the issue, please mark this thread as Solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

