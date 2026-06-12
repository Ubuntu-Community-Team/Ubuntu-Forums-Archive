---
title: "How to perform scheduled backups?"
date: 2007-04-04
forum: General Help
---

### Post by wrycatcher on 2007-04-04
I'm looking for a bit of experienced guidance on how to create a backup script and set it to run at scheduled times.  Here's what I'm trying to do:

[LIST][*]Copy my home folder from one physical disk to another (same machine)[*]Copy files from a networked wireless laptop to a local disk[*]Schedule this script to run on a specific schedule
[/LIST]

Each of the two copy operations takes awhile.   The copy from the wireless machine takes especially long...somewhere around an hour.  The point of all this is just so if one machine (or disk) dies, I have a fairly recent copy of data on another disk.

Anyone out there doing something similar and willing to post some instructions or sample scripts?

Thanks in advance.

---

### Post by andy gee on 2007-04-04
Hi,

I use rsync on a crontab. Rsync is a command-line program that will syncronise one defined folder with another, and you can also use compression to reduce bandwidth use. I use it to backup a laptop to a 500 Gb USB drive on a desktop via wifi. I think Ubuntu comes with rsync - if not, it'll be in the repos.

Cron is a way of performing regular tasks. You can edit the crontab to instruct your computer to perform a particular instruction at a particular time. The advantage of this is that you can do it when I'm not using the computer since it slows my system right down. See man crontab for more.

I don't know (but would love to know) if rsync can backup straight to an archive rather than backing up and the having to manually archive them at some point.

I have used two other backup programs: SImple backup and backup2l (i think thats what they're called - I can't get into my Ubuntu box at the moment). Simple backup seemed very promising , with a sweet gui and excellent options. However, It stopped backing up after a few weeks. Not sure why. After my last complete reinstall of Ubuntu I tried again, same result. 

Backup2l is good, a little complicated, no gui, but backs up to an archive, and it is crontab friendly. I'm not using it right now since I haven't gotten around to downloading it again, but it was pretty good.

Try rsync first, and then if you want more options, try backup2l. If you have any cron related questions, let me know and  I'll try to look up the web-pages I got my info from.

Good luck!

---

### Post by TheWizzard on 2007-04-04
check this site:
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by wrycatcher on 2007-04-04
> **TheWizzard said:**
> check this site:
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

This is great stuff!  Exactly what I want to do...and the option to do "incremental" (or changes only) updates is a nice feature, too.  I had forgotten about that possibility...

---

