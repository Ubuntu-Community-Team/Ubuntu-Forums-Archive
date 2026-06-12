---
title: "luckyBackup question about rsync backups and more"
date: 2015-09-14
forum: General Help
---

### Post by AgentZ86 on 2015-09-14
Hi 

I didn't fully understand the default Ubuntu backup and restore program. I was able to backup, to a network shared folder, but every time I restore it fails at some point.

So I am trying luckyBackup.

My question is about the backup copy. What is the permissions and the actual files backed up ? Are they just copies ? 
This backup is a network shared folder as the source. and the destination is my local machine.

When I restore do I use the local machine to restore back to the network folder or do I use the second machine to restore back onto itself ? 
I really don't know how backups are suppose to work.

Please advise

---

### Post by mastablasta on 2015-09-15
lucky backup works in the way you set it up. they have quite a few options. it worked well for me on Linux but not on windows so I dropped it until they fix the issue.

what are you backing up? is it static data (like family photos, videos) or is it dynamic data (like some work you are doing or some docs that change a lot)?

---

### Post by AgentZ86 on 2015-09-15
> **mastablasta said:**
> lucky backup works in the way you set it up. they have quite a few options. it worked well for me on Linux but not on windows so I dropped it until they fix the issue.

what are you backing up? is it static data (like family photos, videos) or is it dynamic data (like some work you are doing or some docs that change a lot)?

Although there are photos and videos and things the most important is the ability to edit our documents like spreadsheets for libre office etc.

---

### Post by mastablasta on 2015-09-17
in that case shared content is hosted elsewhere while backup of this are on another place. backup are compressed (usually) and then you uncompress them when you restore. by all means try it out before you commit to the solution. if you want to also share docs in same area then have a loot at owncloud or seafile. they have versioning available I believe. but this would be more like your own dropbox not really a proper backup solution.

there are plenty of other interesting backup programs and each do it a bit differently. there is Areca, back in time, simple backup, Duplicati, urbackup, freefilesync, grsync, and various command line rsync and [COLOR=#1a0dab]rdiff-backup ....[/COLOR]

---

### Post by Bucky Ball on 2015-09-17
What you're saying is you want to back-up everything from the server machine (b) to your local machine (a), then swap functions and generate data on machine (a) using machine (b) as the target? In the first instance b = source, a = target; then b = target, a = source?

Set up the first instance then, with a bit of thinking, some copy/pasting, you will be able to reverse that exactly to swap target and source. 

You can setup recursive backups and all sorts with luckybackup which backup only things that have changed. And yes, it is a copy. There are tweaks and I have more to share as I use it a lot, but I gotta go right now, sorry. :| :)

---

### Post by AgentZ86 on 2015-09-17
ok thanks. Seems like my problem is samba. The backup over the network doesn't seem to like the files.

---

