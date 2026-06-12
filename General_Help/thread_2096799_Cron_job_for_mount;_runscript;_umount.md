---
title: "Cron job for: mount; runscript; umount"
date: 2012-12-21
forum: General Help
---

### Post by jim_deadlock on 2012-12-21
I want to set up a (root) cron job as below, which mounts my drive, runs my script then unmounts the drive once the script has completed.

```
0 6 * * * mount /dev/sdd2 /home/jim/sdd; /home/jim/myperlscript; umount /home/jim/sdd
```

The drive mounts, the script completes but the drive stays mounted.

I've experimented by a) having the drive initially mounted then set the job as:

```
0 6 * * * /home/jim/myperlscript; umount /home/jim/sdd
```

...which works fine - script runs, drive unmounts. I also tried b) drive is initially UNmounted and cron job is:

```
0 6 * * * mount /dev/sdd2 /home/jim/sdd; /home/jim/myperlscript;
```

... and again this works fine, drive mounts and script runs.

So why won't it do both :confused:

---

### Post by rnerwein on 2012-12-21
> **jim_deadlock said:**
> I want to set up a (root) cron job as below, which mounts my drive, runs my script then unmounts the drive once the script has completed.

```
0 6 * * * mount /dev/sdd2 /home/jim/sdd; /home/jim/myperlscript; umount /home/jim/sdd
```The drive mounts, the script completes but the drive stays mounted.

I've experimented by a) having the drive initially mounted then set the job as:

```
0 6 * * * /home/jim/myperlscript; umount /home/jim/sdd
```...which works fine - script runs, drive unmounts. I also tried b) drive is initially UNmounted and cron job is:

```
0 6 * * * mount /dev/sdd2 /home/jim/sdd; /home/jim/myperlscript;
```... and again this works fine, drive mounts and script runs.

So why won't it do both :confused:
hi
have you had inspect your /var/log about some error messages (sometihing like device is busy.
or just run the faulty job in a terminal with: sudo .........; .......; .........
may be you will get an error back.
cheers

---

