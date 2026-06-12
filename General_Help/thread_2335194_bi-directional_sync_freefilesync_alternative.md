---
title: "bi-directional sync freefilesync alternative"
date: 2016-08-26
forum: General Help
---

### Post by alain.roger on 2016-08-26
Hi,

i'm having some issue to make correctly work freefilesync under kubuntu 16.04 with my desktop computer. I used this app for 1 year under windows without problem, but it seems some locks and permissions of linux make it tricky to use under ubuntu.
I'm looking for an alternative with a gui (if possible) to sync /home, and some other directories (/perso, /work) to my NAS (so later i can sync NAS content with my laptop).

i use to work on 2 different computers so NAS acts like a repository for synchronization.

i know that a command line program osync do bidirectional sync, however i have concern about: 
1. how are raised error/conflicts and how they are manageable in command line (in fact, what to do in case of conflict/error)
2. the program should be scheduleable
3. a huge plus, if data can be compressed before sending them through network

Any idea would be very good as today i have a lot of documents and i do not want to lose them.

thx

---

### Post by TheFu on 2016-08-26
General Unix knowledge. Never trusted 2-way sync enough to use it.

1) log files.  Use a log monitoring program to provide alerts however you want them - emails, texts, daily summaries. Whatever. Up to you.
2) cron is the tool to schedule **anything** on a Unix system. There are 4 places where cron looks for configurations. Learn to use it.
3) To transmit files over the internet requires either a VPN or ssh-tunnel.  Good news, both of these protocols support compression. Check the manpage for whichever tunnel you've decided to use.  **ssh -C** is a hint. ;)  BTW, rsync uses ssh tunnels by default. Just setup ssh-keys between the systems you want to sync. Unfortunately, since most mobile clients don't have a static IP, that means that the clients will need to push and pull the data. This is less secure than having the server push/pull the data.

Lastly - HTTPS security is broken. If you don't care about how well security actually works, then it is probably sufficient. If you do, then it is terribly broken and all security professionals already know this and have for about 8 yrs.

---

### Post by alain.roger on 2016-08-27
If you do not trust 2-way sync, how do you solve such situation that once i work on laptop and next day i work on desktop computer ?
In order to have both computers with same data (up-to-date) i need to sync them, so to make a 2-way sync.

I tried rsync to push all data from laptop to repository folder on my NAS, but how to take all data from NAS and do sync back to desktop and check conflict ? 
Or should i do 2 rsync jobs scheduled by a cron ?

---

### Post by TheFu on 2016-08-27
I cannot say what you should do, since I don't have any personal experience with 2-way sync tools.

I solved it with remote access and keeping straight in my mind where the current working-copy is located when off line.  I have 4 systems that I constantly work on, but 2 are much more "primary" than the others. Daily, automatic, versioned backups are another key to my solution. These are well outside any sync efforts.

Not a perfect solution, but it has been working for over a decade. I've traveled to 5 continents using the remote access method. My main desktop is running inside a private cloud inside a VM that I access remotely. It is usually the "system of record" for anything desktop related. All important data has a "system of record" in my mind.  Any data found elsewhere is a copy and not important - BY DEFINITION.

For example, my password manager DB is 99.9999999% read-only (in practical terms). I make to it changes on 1 system.  Daily, that file gets pushed to 6 other systems just after midnight local time.  I know this, so if I do make any changes on a different system, those changes must be pushed to the "system of record" by midnight.

If I were still doing software development, I'd use git to manage differences between text files, but that doesn't work for blobs (like a DB). I know this.

My "system of record" for Contacts is a Zimbra contact manager, not an email program or anything on a desktop machine.  I make updates only inside Zimbra and dump those out from time to time to be used by all the different email/contact clients.

Ran 2 rsync jobs on mirrored web servers for a few years.  rsync push from A --> B; rsync pull from B --> A.  Had to be certain the system clocks were extremely accurate (which isn't hard thanks to ntp).  A and B were about 500 miles apart and didn't use a DB.  This 2-way sync job ran daily, but also on-demand after I update the static files.

So you'd think that I misplaced files all the time, but that doesn't happen.  Thanks to recoll (an amazing search tool).  It is like having google for my personal network. Very fast, but sometimes it returns too many results.  Needed to update a large spreadsheet with some collectable diecast model information this week (got 2 more items!). Took about 5 minutes to find that file, because I didn't remember the name or where it was located, but I had left hints on another system ... which got me to the file immediately. It was on my main desktop in the HOME directory (which isn't really the best place for it, but ...).

Anyway ... this might seem like a bunch of effort. OTOH, I've never lost any of this data even if HDDs failed.  Right now, one of my VM host systems has a broken RAID1 array. This morning a new disk will be swapped in (after weekly patching) to correct the issue.  Couldn't replace it earlier in the week when the disk failed. It runs about 15 VMs and didn't want to impact users. Saturday morning is a known, published, maintenance window. Those systems are allowed to be off-line for 3 hrs during that window.  Anyway, I have a plan and it is working.

There are other solutions used by lots of people like seafile or opencloud. Have you considered those options?  I'm security paranoid, so won't allow any php programs directly on the internet, but over a full vpn, sure. Just haven't gotten around to setting one up enough to be happy using it.  Did play with owncloud for a few months - found it a hog and slow - but that was years ago.

---

