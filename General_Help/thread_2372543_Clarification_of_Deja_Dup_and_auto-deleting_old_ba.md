---
title: "Clarification of Deja Dup and auto-deleting old backups."
date: 2017-09-26
forum: General Help
---

### Post by Roasted on 2017-09-26
Hi friends. For years I've sworn by just using rsync to do backups. It's done the job and I've had no problems using it. As time has passed and life has gotten much busier I've found myself taking a closer look at Deja Dup. I've always turned away from it because of its default behavior, where it will just fill up a destination until it's maxed and then begin to delete old backups. This didn't jive with me having a 6TB array in my home server as I have many other things on that array -- not just backups of laptops and stuff. Because of this unpredictability, I just chose to use rsync.

But having come across some additional hard drives (2x1TB), I began to flirt with the idea of just branching backups off of my main array anyway, so I spun up a second mdadm RAID1 array with the 2x1TB drives. I have space on my secondary backup server (which is a clone of my main file server) so I figured this would be a neat idea.

One bit of confusion though -- now that I have this set up, I'm questioning how Deja Dup acts when it comes to multiple users using Deja Dup and saving to the same destination.

My wife and I each use Ubuntu. She has one system, I have 3 (one main, two that I beat up with testing). Ultimately this means 2 users/4 systems will be backing up to the 1TB array that will be destined for Deja Dup backups alone.

Let's say that my main laptop has 200GB of data and it has backed up a number of full copies. Let's say my wife's laptop has 100GB of data and it too has backed up a number of full copies. Let's say that 900GB out of a possible 1TB of storage is in use, thus leaving 100GB of available space on /media/backups (the 1TB array). What happens if I plug in another system to Deja Dup and aim it to save in /media/backups of that server? What happens if that additional system has a total of, say, 150GB of data to back up? How would Deja Dup handle the fact that I'm doing a *first* backup of 150GB to a destination that has 100GB free? Would Deja Dup be intelligent enough to acknowledge that there are 3, maybe 4 old backups of roasted-primary-laptop and delete an older copy to make room for the 150GB worth of data on roasted-new-laptop? Or is Deja Dup only "self aware" enough to acknowledge its *own* backups made from the very device you're initiating the backup from at that moment?

---

### Post by untrustytahr on 2017-09-26
> One bit of confusion though -- now that I have this set up, I'm questioning how Deja Dup acts when it comes to multiple users using Deja Dup and saving to the same destination...

Do you mean the same destination or same destination device?  The former would be inadvisable.  The latter would be fine.  Deja Dup (Duplicity) works by putting files into a series of volumes of compressed tar files.  The name of the tar files is complex but basically is a timestamp_volX name.  Putting all files in the same destination most likely would not cause conflicts but theoretically could if two computers kicked off a backup at the same instant.  That's easily solved by just creating different target destination directories for different hosts- i.e. /media/backups/roasted/primary-laptop  and /media/backups/wife/primary-computer.  Trust me when I say if you ever have to manually look at the target destination, you will want them separated.
> What happens if I plug in another system to Deja Dup and aim it to save in /media/backups of that server? 


Deja Dup works on a 'per host per user' basis.  It creates a manifest that is kept in a .cache file so the individual users & hosts are discrete.  The problem would be if the target destination file had the same name as I said before.
> What happens if that additional system has a total of, say, 150GB of data to back up? How would Deja Dup handle the fact that I'm doing a *first* backup of 150GB to a destination that has 100GB free? 
It would try to write a full 150 MB backup as there would be no manifest or backups for that computer.  I don't think (but don't quote me) that it does a 'pre-check' for available space.  That is because there is no way of knowing the 'compressability' of the data to accurately calculate.
You should also know that deja dup doesn't run on any given day unless you logged into that machine.  You don't have to stay logged in, but it won't run if you didn't log in at all.




If you understand rsync, you would probably be better off using duplicity on the command line directly from a cron job or two (deja dup is just a gui to it but reduces it's flexibility).  It has command switches that will handle your 'unchecked growth' problems.


example:
```
duplicity --full-if-older-than 1M /source /destination


the 1M means if the last full backup is over 1 month old, do a new full backup otherwise it will do an incremental if a backup exists or a new full if none exist.  You can change the interval to your requirements (week, days, etc)




duplicity remove-all-but-n-full 2 --force /destination


This will look at how many full backup chains are in your destination directory and keep the last two full chains deleting the others.

```

The man page has tons of useful information if you can get through it.  It's pretty similar to rsync's structure so you should be alright.

---

### Post by Roasted on 2017-09-26
Hey there. Thanks for your in depth response. Appreciate it! To clarify, yes I meant the same destination device. I have a 2x1TB RAID 1 array in my file server that I was going to exclusively use for backups from my laptop, my wife's laptop, and a test laptop that I often tinker with. 

The disk array will be mounted at:
/media/backups

The storage path for the users *was* looking to be (more info on this later***):
/media/backups/jason_lenovo_laptop
/media/backups/jason_toshiba_laptop
/media/backups/kristi_lenovo_laptop

My concern comes in with Deja Dup acknowledging other backups. So let's say for example jason_lenovo_laptop is using 600 GB of space across multiple full backups. On top of that, kristi_lenovo_laptop is using 300 GB of multiple full backups. Between those two, we're at 900 GB, leaving (in theory) 100 GB remaining. But now yours truly wants to light up jason_toshiba_laptop, and that laptop contains 150 GB of space. This is where things get curious. Would Deja Dup just fail because it knows I have 150 GB of data and the destination has 100 GB of remaining space? Would Deja Dup say, hey hang on a second, I see 8 full backups from jason_lenovo_laptop, let me nuke an old backup to free up space and try to get jason_toshiba_laptop in here with that system's first full (150 GB) backup.

Interestingly, I see that in my testing of Deja Dup there's a directory with the hostname of my laptop*** (referenced above). I don't recall creating this. That makes me wonder if Deja Dup is auto populating it. If that's the case, it makes me wonder if I can just point all machines to back up to server://media/backups (and that's it) and let Deja Dup create its own hostname-named-directories for each individual system. That would suggest that Deja Dup might (maybe? hopefully?) acknowledge other data within /media/backups, and thus, might (maybe? hopefully?) be intelligent enough to delete an older backup from a different machine to make space. Total guess, total speculation, but... maybe?

I did consider just using Duplicity and writing my own script. Currently I use an rsync script, and it's fine. My needs are quite basic, as I really just want to house backups locally on my LAN in case a machine tanks. I like that Deja Dup is included by default, as surely a backup application included in the box makes a world of sense. If Deja Dup can do this, and I think it can, I think it'll be fine. I'm just trying to understand what Deja Dup would do in certain circumstances where space gets maxed. In a single user world, it makes sense -- it'll wipe old backups to free up space for new backups. Self explanatory. It's just the multi-user thing that raises an eyebrow.

On that note, I did explore Duplicity more, because I didn't want to put all my eggs in one basket. I mean, if Deja Dup turns into a dumpster fire, I wanted to know how I could retrieve the data using Duplicity. After some reading I was able to successfully restore a Deja Dup backup utilizing Duplicity via command line. I was using this command:

duplicity restore --no-encryption file://FOLDER-CONTAINING-DUPLICITY-ARCHIVES/ restore-folder

It worked fine. I received two basic errors, but googling a bit suggested it was relating to Duplicity being unable to reassign ownership to the restored files (I pulled the Deja Dup backup over to a different machine and was using Duplicity on this entirely different rig to restore the files as I wanted to simulate a total loss of my main system that did the initial Deja Dup backup). After this success, I was more confident in Deja Dup, as I can always drop to terminal to manage things at a lower level if need be. Reason I explain all this is, in theory, I should be able to also use Duplicity to list all prior backups and delete an older backup manually to create more space for that new 3rd system (jason_toshiba_laptop) to run its 150 GB backup in the event Deja Dup would be unable to do so due to jason_lenovo_laptop and kristi_lenovo_laptop using all the other space.

The TL-DR of all this is I'm curious about Deja Dup's intelligence when it comes to nuking old backups. If Deja Dup will delete an old backup for User/Machine_A in an effort to make space for User/Machine_B to run their backup, that seems pretty kosher. If it can't, I can always drop to CLI with Duplicity to manually nuke an old backup for User/Machine_A.

In the end, I guess I really don't need to worry about it until the 1TB storage gets maxed, at which point Deja Dup would of course error out. If it never errors out with backing up and I see backups rotating, then... great! That will take a lot of time in day-to-day use though, and my curiosity is not quite as patient. :) 

Again, thanks for your response. Appreciate it. :D

---

### Post by untrustytahr on 2017-09-26
No, neither deja dup nor duplicity will delete backups from other users or machines.  That would be a complete recipe for disaster.

---

### Post by Roasted on 2017-09-26
It makes sense, surely. I guess my only concern is whether this will create a relative imbalance in the end. For example, say my wife uses her laptop 3 days a week, but I use mine 7 days a week. My "requirements" for a full backup that Deja Dup would automatically determine would be a bit higher. The net effect of that is me backing up more frequently, thus me having more full backups in the end. Me having more full backups translates to less available space for my wife to do her backups. Maybe it matters less because she'll be using the computer less frequently && she'll therefore need less full backups? Or maybe this is grounds for putting some more thought into the destination that these backups will reside on. Maybe I should look into a way to enable quotas, or just partition the array so there's some walls in place and so she has her section for her Lenovo laptop and I have my section for my Lenovo laptop + another section for my Toshiba laptop?

...or maybe I'm putting way too much thought into this algorithmic thought process and should just let the machines unleash Deja Dup onto the destination and let the software hash it out organically and hope for the best? :P

---

### Post by Roasted on 2017-09-27
So... after a lot of thought and reading I decided to refocus my attention a bit. The combination of rsync with hardlinks stuck out to me as being a nice option, as it's effectively rsync (raw data, no bulk of tar's -- major bonus) but with incremental changes after the initial data push. I found myself reading into some other backup utilities to get a sense of how things tick. This brought back some memories, as I remember sbackup, luckybackup, etc., but those projects haven't been updated in years. Interesting.

As I was reading through the documentation for Back In Time I took note that it's based on... rsync with hardlinks! Neato. I checked out their GitHub page and was happy to see the development activity. I ultimately installed it and toyed around with a test laptop. So far, definitely liking what I'm seeing. This should make storage space a bit more predictable, as I won't have to worry about having some random number of full backups taking up additional space. Likewise, some of the settings stuck out to me, such as retaining x-days worth of snapshots. I chose 30 for my setup to see how things go. If I understand right, this will allow a sense of automatic deletion for deleted files in old snapshots. For example, if I have a 5GB ISO, back in time will include it in the snapshot. If I later delete it, it'll be gone from the destination (server) in 30 days after the 30-days-worth of snapshot retention cycles it through. This is assuming my assumption/understanding of what that feature means is accurate, of course... I also, really, *really* like its restore option. It's fast and doesn't sit there churning forever just to grab an old txt file. Very much appreciated.

I think it's nice that Deja Dup is included by default in Ubuntu, but the more I read into it and recalled the conversation in this thread, the more I began to accept that Deja Dup strikes me as an oversimplified backup for my needs. If I was one guy, one laptop, one external hard drive, that may be fine. In this day and age with multiple systems and centralized storage becoming more commonplace in home environments, I don't think it jives too well with accommodating that crowd. I tried to make it work but I guess the need for a more predictable sense of server storage dictated otherwise.

Kudos to the Back In Time devs. I'm thoroughly enjoying what I'm seeing here. Thanks again for hashing this out with me untrustytahr! It's now time to unleash the other systems and see how things go as the weeks and months pass.

---

