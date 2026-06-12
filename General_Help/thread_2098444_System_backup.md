---
title: "System backup"
date: 2012-12-26
forum: General Help
---

### Post by pastim on 2012-12-26
I have what I supposed to be a trivial problem with getting a full system backup.  I have searched forums (including much of the large one at [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)), tried several tools, many variations on parameters, all to no avail.

How can this be so hard?

All I want to do is backup the whole of my ubuntu 12.04 system, compressed and encrypted, which I will then copy to a usb drive.  I want to be able to restore individual files if needs be. I need to exclude several mounted local drives and one remote, plus /dev, /proc and a few other directories and their contents.

With zip I cannot persuade it to exclude a directory with all its contents including subdirectories, and I get loads of zip warnings from /sys/... and /dev/....  so I always have to stop it before it completes.  I have tried every combination of *s, /s, \s, with and without quotes, and so on.  Nothing seems to make any difference.  It is quite bizarre.

With 7z it fails because running as sudo it cannot stat my /home/user/.gvfs directory, even though that directory is explicitly excluded.  I have read that this is intentional for security reasons, but it means I can't create backups, which is ridiculous.  Security should never, ever, override the ability to make backups.

I feel appallingly dumb having to ask this, but I am at my wits end.  I can't believe I am the only person who wants to backup a whole system in this way, so how do others do it?  There must be a free tool somewhere that will do it.

---

### Post by N00b-un-2 on 2012-12-26
I've had really good experiences with CloneZilla in the past.

---

### Post by CharlesA on 2012-12-26
> **N00b-un-2 said:**
> I've had really good experiences with CloneZilla in the past.
Likewise.

LVM Snapshots are other method of getting a full system backup from a live system.

---

### Post by pastim on 2012-12-26
> **N00b-un-2 said:**
> I've had really good experiences with CloneZilla in the past.
Doesn't that require a complete fresh partition at least as large as the one I'm backing up?  I really want to backup the files and directories rather than a complete partition.

---

### Post by sudodus on 2012-12-26
If you want a complete image of your system, I suggest that you use ***Clonezilla***. Read about it and download it from its web site on the Internet.

The simplest way is to boot from a Clonezilla CD or USB drive and run through its menu system. You can save the boot script and later on re-use it still booting from the Clonezilla drive, but running the command line interface.

If you want nightly backups from a running system, I suggest that you make a script running ***rsync***. The manual ```
man rsync
``` is really good. Rsync is already installed in [KLX]Ubuntu. There are several GUI front-end programs, that run rsync, if you prefer that way to work.

---

### Post by pastim on 2012-12-26
> **CharlesA said:**
> Likewise.
LVM Snapshots are other method of getting a full system backup from a live system.
I took a quick look at LVM.  At first sight it looks ferociously complicated, and way above what I need for a humble desktop PC.
  
I had foolishly assumed that creating a backup (just copying, compressing and encrypting files) would take me a couple of hours, not days of research, trial and error.  I begin to yearn for my Windows system.....

---

### Post by d4m1r on 2012-12-26
Did you not want to use Deja Dup? It is built into 12.04 and is really easy to use through the UI....Just search for "backup" in your lens.

---

### Post by sudodus on 2012-12-26
> **pastim said:**
> Doesn't that require a complete fresh partition at least as large as the one I'm backing up?  I really want to backup the files and directories rather than a complete partition.
No, a compressed image compresses the files and does not store the empty space at all. But if you don't make a compressed image, but clone the drive, that clone will need as much space as the original drive or partition.

You asked for a full system backup, but now I think what you want is a selective backup of important files (personal files and system files). And that can be done with rsync (as is or via some GUI).

---

### Post by pastim on 2012-12-26
A funny thing about forums is that everyone is very helpful, but many often answer the question they want you to ask, rather than the question you actually asked. 

I'm aware many will say that is because I am wrong, but I'd still like to get the method I prefer working.  I know some people like to take clones, but I really don't want to not least because my offline storage solution won't cope with that, and I want to be able to restore individual files, which Clonezilla does not support.

So I want to backup files and directories, not take a clone - I don't need a complete clone.  I also need to compress and encrypt the files, and rsync won't do that.  I have used rsync for my home directory, but following a stupidly self-inflicted wound on some system files, I want to have a copy of them around as well just in case....

---

### Post by pastim on 2012-12-26
> **sudodus said:**
> You asked for a full system backup, but now I think what you want is a selective backup of important files (personal files and system files). And that can be done with rsync (as is or via some GUI).

But rsync won't compress or encrypt will it?

---

### Post by pastim on 2012-12-26
> **sudodus said:**
> No, a compressed image compresses the files and does not store the empty space at all. But if you don't make a compressed image, but clone the drive, that clone will need as much space as the original drive or partition.
But as I understand it Clonezilla states that "The destination partition must be equal or larger than the source one."

---

### Post by sudodus on 2012-12-26
> **pastim said:**
> But as I understand it Clonezilla states that "The destination partition must be equal or larger than the source one."
- When you clone the drive, yes.
- When you restore the system from the image, yes.

- But that backup image will be much smaller because of compression.

---

### Post by pastim on 2012-12-26
> **d4m1r said:**
> Did you not want to use Deja Dup? It is built into 12.04 and is really easy to use through the UI....Just search for "backup" in your lens.My "lens"? I've never heard that term before.  

Anyhow, thanks for the idea.  I can't see any compression or encryption options on that tool. I may have, reluctantly, to resort to a 2 stage backup process, assuming I can get that to work.

---

### Post by pastim on 2012-12-26
> **sudodus said:**
> - When you clone the drive, yes.
- When you restore the system from the image, yes.

- But that backup image will be much smaller because of compression.
Unless I totally misunderstand you, since the place I want to place the backup is smaller than the linux partition, that means I can't use the tool. 

And anyway it seems I can't restore files from the clone (at least not easily).

---

### Post by sudodus on 2012-12-26
> **pastim said:**
> My "lens"? I've never heard that term before.  

Anyhow, thanks for the idea.  I can't see any compression or encryption options on that tool. I may have, reluctantly, to resort to a 2 stage backup process, assuming I can get that to work.
Which flavour of Ubuntu are you running? The lens is a tool in Unity, the DE of vanilla Ubuntu.

Restoration of single files will be more difficult, when you compress the backup. But several GUI tools offer that. Have you looked into the details of deja-dup?

[[COLOR="Red"]https://launchpad.net/deja-dup[/COLOR]]("https://launchpad.net/deja-dup")

---

### Post by pastim on 2012-12-26
> **pastim said:**
> My "lens"? I've never heard that term before.  

Anyhow, thanks for the idea.  I can't see any compression or encryption options on that tool. I may have, reluctantly, to resort to a 2 stage backup process, assuming I can get that to work.
I have set it off, and it did ask for an encryption password, so I'm hoping it will do the job.  

It may take some time.  I'll report back later.

---

### Post by pastim on 2012-12-26
> **sudodus said:**
> Which flavour of Ubuntu are you running? The lens is a tool in Unity, the DE of vanilla Ubuntu.
Acronym hell.... 40 years programming & using computers and I never saw DE before.

I'm on 12.04, for 8 months or so.  I surmise that Dash is a "lens" although the meaning of that defeats me.  No matter.  I'll carry on with a trial of the native Backup.

---

### Post by sudodus on 2012-12-26
Good luck with your backup :-)

I just want to add a comment about ***pictures and multimedia files***, that are already compressed, yet take a lot of disk space, at least after some time.

I suggest that you backup these files without compression, because it takes a lot of time, and decreases the size of the backup very little, maybe 1%.

So you can have two backup jobs, one for the pictures and multimedia files (without compression), and one for the system and the rest of the home directory tree (with compression).

---

### Post by CharlesA on 2012-12-26
> **pastim said:**
> I took a quick look at LVM.  At first sight it looks ferociously complicated, and way above what I need for a humble desktop PC.
  
I had foolishly assumed that creating a backup (just copying, compressing and encrypting files) would take me a couple of hours, not days of research, trial and error.  I begin to yearn for my Windows system.....
Backing up doesn't have to be hard. Backing up a live system is hard.

See here for info on LVM:
[http://ubuntuforums.org/showpost.php?p=12419793&postcount=6](http://ubuntuforums.org/showpost.php?p=12419793&postcount=6)

---

### Post by pastim on 2012-12-26
> **sudodus said:**
> Good luck with your backup :-)

I just want to add a comment about ***pictures and multimedia files***, that are already compressed, yet take a lot of disk space, at least after some time.

I suggest that you backup these files without compression, because it takes a lot of time, and decreases the size of the backup very little, maybe 1%.

So you can have two backup jobs, one for the pictures and multimedia files (without compression), and one for the system and the rest of the home directory tree (with compression).
Thanks.

I could do without multiple jobs (and anyway I'm not sure how I would do that with the Backup tool - is it even possible?).  I'm trying to keep things simple.  

My first attempt with Backup skipped many files, I think due to permissions.  I'm not quite sure what will happen if I try and run it with sudo, but I'll try again tomorrow (I have a nasty feeling it will lose all my settings and probably fail to backup some of my personal user files).

I'll then have to see if I can restore from it via a Live CD.

I have a suspicion that this is still not going to work.  If that's the case I shall probably have to give up and live without a full system backup.  I have my personal files backed up (several places), and can restore the whole system from an ubuntu CD plus personal files in about 15 hours (I know because I've just done it).  I just imagined I would be able to backup all the system files securely so as to save time & effort if I screw the system up again or have a system failure.  It may be that I was naive.

Over the last few months I have learned that everything in linux is hard.  Nothing is ever quite the way one imagines it will be, and always has complex twists and turns. It seems to require a certain way of thinking that I don't have, even though I was brought up using command line tools.  With Windows you do it the way they want you to because you don't have many options.  With linux there are 50 shades of way, none of which is quite satisfying.;)

---

### Post by sudodus on 2012-12-26
> **pastim said:**
> ... I have my personal files backed up (several places), and can restore the whole system from an ubuntu CD plus personal files in about 15 hours (I know because I've just done it).  I just imagined I would be able to backup all the system files securely so as to save time & effort if I screw the system up again or have a system failure ...

You have your own backup system already. Maybe you should not expect it to be easy to get something that is much better.

If you want a complete backup, Clonezilla is a good choice, used by many people. You need not take such complete backups very often, for example only when you make major manual changes of your system.

Instead take frequent backups of your personal files! Consider including the hidden files and directories in your home directory (the .files and .directories), if you use applications that store important data in such files, for example Thunderbird and Virtualbox.

---

### Post by pastim on 2012-12-27
Running deja-dup as sudo (via gnome-control-center) and backing up to my (smallish) USB drive seems to have done the trick.  No errors reported.

It's a shame there seems to be no easy way to browse what is in the backup (as there would have been if only I could have got a zip-style method to work).  I am having to take on trust that what I want is there, and that makes me uneasy ....

Still, I booted from my ubuntu live CD, ran deja-dup, and it looks as if I could restore files or the whole system from there if I ever have to.

So I now have:

1) Personal file backups (several) for normal recovery
2) This new deja-dup/duplicity method to attempt recovery if something more significant fails, without having to start all over again.
3) The ubuntu live CD to do a full clean reinstall, plus personal file backups, if all else fails.

I'll be moving into the New Year a little happier now :)

---

### Post by pastim on 2012-12-27
And thanks to all who responded to my cry for help.  I really do appreciate it.

---

