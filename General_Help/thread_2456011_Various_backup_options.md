---
title: "Various backup options"
date: 2021-01-02
forum: General Help
---

### Post by linerman on 2021-01-02
Hi,

I would like to backup my whole ubuntu partition - all the files.
The goal is to to have backup in some kind of image file, and restoration would be eventually made on a clear, formatted partition.

I want to backup and at the same time work so software like Clonezilla is not a solution.

I tried "dd" but it takes horrible amount of time and "dd" is not showing estimation time of work.

I've read that  "gnome-disk" would do it, but have found that restoration with "Disk"  needs space which is "larger than the saved image". That sentance made me puzzle.

Also tried "Timeshift" but couldn't make it to backup whole partition.

Anyway, "dd" looks the best, but that lack of estimation time is unacceptable. 
Any ideas, which program would meet my expactions? 

Regards

---

### Post by TheFu on 2021-01-02
I think your expectations are unrealistic.

If you want the system to be used during backups AND use a slow, inefficient, imaged based backups, then you'll need to use advanced file systems (ZFS) or LVM with snapshots.  **dd** has an option to show progress. I don't recall what it is, but it is definitely documented as I've seen it in the manpage.  dd is great for all sorts of needs, but backups is simply not one of them.  _Any image-based backup needs to use either ZFS-snapshots, LVM-snapshots or boot from alternate media_. Not doing these things will lead to corruption and useless restores more than the effort involved would warrant.

Image based backups suck for many reasons.  They are great for 1 reason only. Huge sizes, long processing times, corruption likely on active systems.

I would strongly encourage you to consider NOT using image based backups, since we all need versioned, daily, automatic backups these days thanks to all the malware in the world.  Efficient versioned backups don't need 2x the storage for two versions.  The links below will show that 60-90days needs 1.15 - 1.25x the storage backed up.

I've written about backups in these forums for years now.
A Simple Script: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) has more discussion.

Restoring backups: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

Backup storage needs: [https://ubuntuforums.org/showthread.php?t=2436798&p=13932882#post13932882](https://ubuntuforums.org/showthread.php?t=2436798&p=13932882#post13932882)

aljames2 script w/ LVM snapshots: [https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)
I disagree with parts of this script and think all the snapshots should be included in a single backup command, but it is still useful in showing LVM snapshots.

rsnapshot: rsync + hardlinks for versioned backups (requires Linux file system like ext4)
[LIST]
[*][https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[*][https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/)
[/LIST]

rsnapshot has been around a very long time and works. I first used it in the 1990s, but some flaws in that method that ended with incorrect permissions forced me to rethink the method used. Most people would be fine using it.  rsnapshot and Back-in-Time use the same underlying methods.

There is a trade-off between simple backups and efficient backups.  I can restore any of my systems after an OS disk failure within 30-45 minutes. That time is reasonable and I've used it to solve OS problems that I couldn't figure out too.  After working on some new issue 30 minutes, I stop and consider if just restoring the system from backups taken overnight would be more efficient. About once a year, it is.  I'm running about 20 system here. Doing image-based backups would be completely crazy.  I don't have that sort of storage to retain 90 days of versioned backups if images were involved. Some systems are high-risk and need more protection - 180 days of versioned backups.

Anyways, those are some ideas for consideration.

If you absolutely insist on image-based backups, _you'll need LVM or ZFS plus snapshots_.  You can use dd, ddrescue, **fsarchiver** or partimage tools.  fsarchiver can restore to smaller partitions, provided the data will fit into that restore location.  I use fsarchiver to make backup images for raspberry-pi systems that are for play, not production. It will compress the image as part of the process. Of course, the storage is connected to another running OS to safely accomplish this.

Hopefully, some others will chime in with their suggestions too.

---

### Post by GhX6GZMB on 2021-01-02
> **linerman said:**
> Hi,

Also tried "Timeshift" but couldn't make it to backup whole partition.



Timeshift per default excludes /home and /root, but you can change this if you want.

I'm no fan of image based backups either, for all the reasons TheFu mention.

File based backups are much more flexible, but have the downside that a (x)ubuntu reinstall is needed in case of a crash.

---

### Post by TheFu on 2021-01-02
> **ml9104 said:**
>  ... but have the downside that a (x)ubuntu reinstall is needed in case of a crash.

I see that as a PRO, not a CON.  Starting from a fresh install (15 minutes of effort) cleans up all sorts of unknowns after some issue sufficient to require restoring a system-level backup. Well, it can be a CON, I suppose. Just depends.

Make a list of all the manually installed packages on the system, then feed that list into the fresh install.  apt-mark makes getting the list easier, with some caveats.  In the old days, we'd get a list of all installed packages, which included thousands of already-installed packages and old dependencies no longer needed.  I suppose it is possible to filter that entire list somehow. After a fresh install, I use apt-mark to tell APT that every package on the system was automatically installed.  From that point forward, APT will keep track of manually-named packages installed separate from dependencies. With this little bit of preplanning and a good backup of our HOME directories most typical desktop systems have a sufficient backup they can restore in 30 minutes or so, including having all their old APT programs back.

Servers are just a little more complex, since there is almost always data stored elsewhere, settings stored elsewhere, and perhaps some custom programs that were not installed via APT.  The admin would know those places, any modified files, and which daemons need to be shutdown to safely get a backup OR other steps to capture the data without corruption - like dumping a small SQL DB to a text file.  Files that are open during backups are a concern for corruption.  Sometimes those files don't really matter. Other times, those files are THE ENTIRE REASON a system exists. The data is more important than the hardware, software, or your job.

But we don't know that from the OP.

---

### Post by linerman on 2021-01-03
Thank you for your comprehensive answer.

I think, I should be more precise. 
The point is, that I like to explore my Ubuntu system, with various configuration files, compiling programs etc. 
Sometimes something goes wrong, and my most usuful sofware stop working. Most of the times I know what went wrong, but there are moments when I do not know.
That is why I have made clean install, configured the system with my basic needs and software and now it works.
Now, that is the moment I would like to backup . 
So when something will go wrong again, then instead of clean install and making basic configuration (5 hours), I would just restore my backup.
I would like to have restored all files, because as I wrote earlier Timeshift did not made that properly. (He did not delete residues of old compiled programs, and did not fixed ubuntu software malfunction).
I would just delete or format my partition and restore files. With restoration of Grub, I would manage different way.

I do not push that backup has to have form of image. It could be different form of backup. 

My Ubuntu partition is only 300 GB, so it shouldn't take much time.

---

### Post by TheFu on 2021-01-03
Did you look at the links?

---

### Post by linerman on 2021-01-03
> **TheFu said:**
> Did you look at the links?

Yes. But syncing is not what I need. I do not want to have scheduled backup and making snapshots.
Just one backup of whole files every 6 or 12 months.

That is why your script looks interesting.
Is such a command would be good, regarding my needs?
```

rdiff-backup -exclude-special-files --include  /etc  --include /root   --include  /home  \  --exclude '**'    /       /my-backup/01-2021

```

And what about estimation time of such backup?

---

### Post by GhX6GZMB on 2021-01-03
> **linerman said:**
> Thank you for your comprehensive answer.

The point is, that I like to explore my Ubuntu system, with various configuration files, compiling programs etc. 
Sometimes something goes wrong, and my most usuful sofware stop working.
...
So when something will go wrong again, then instead of clean install and making basic configuration (5 hours), I would just restore my backup.
I would like to have restored all files, because as I wrote earlier Timeshift did not made that properly. (He did not delete residues of old compiled programs, and did not fixed ubuntu software malfunction).
...


This is where I don't understand your problem.
I'm in exactly the same situation as you. I'm relatively new to Lubuntu and like to play around, sometimes with disastrous results.
Timeshift has saved my behind so many times, that I've stopped counting.
"Damn, I've messed this up!"
No problem, a Timeshift restore brings the system back to where it was in a couple of minutes. (provided you did a backup before messing around!)

I think you just don't quite understand how to configure Timeshift.

---

### Post by linerman on 2021-01-03
> **ml9104 said:**
> 

I think you just don't quite understand how to configure Timeshift.

It could be. What should proper configuration looks like, then?

---

### Post by GhX6GZMB on 2021-01-03
> **linerman said:**
> It could be. What should proper configuration looks like, then?

Timeshift as default excludes all user directories. That is: $HOME and /root. This is fine for a system backup - except it isn't 100%.

What you should do is to add "Hidden directories" and $HOME/Desktop to the backup directories.

Then you can play around as you like.

---

### Post by TheFu on 2021-01-03
> **linerman said:**
> Yes. But syncing is not what I need. I do not want to have scheduled backup and making snapshots.
Just one backup of whole files every 6 or 12 months.

That is why your script looks interesting.
Is such a command would be good, regarding my needs?
```

rdiff-backup -exclude-special-files --include  /etc  --include /root   --include  /home  \  --exclude '**'    /       /my-backup/01-2021

```

And what about estimation time of such backup?

```

rdiff-backup -exclude-special-files --include  /etc  --include /root   --include  /home  \
     --exclude '**'    /       /my-backup/01-2021

```

Notice how I forced a line break where the \ was?  That's what that character does.

How can anyone estimate the time to backup a system withing knowing your network, your disks, how much data there is, and a consulting fee?  Try it. See how long it takes.  Then make some changes and try it again.  The first **rdiff-backup** will be as long as an **rsync** of the data requires.  But all the following backups will be much less, depending on how many files and the changes to those files, over time.  I've posted backup times in these forums, perhaps in the links already provided for different systems.

If all you do is backup, backup, backup, you'll eventually run out of storage.  There's an rdiff-backup command, hopefully in the script, that removes backups older than X days.  rdiff-backup doesn't allow removing intermediate backups, since they are reverse-differential.  If you want to keep 90 days of versions, then after the current backup finishes, run a command to remove all backups over "90D" old. My script uses perl, so this is how it looks:
```
   `$rdiffb --remove-older-than $days --force $target`;
```

IMHO, backups need to happen at least weekly on a system. Monthly is definitely much too long and the backups really need to be automatic or humans won't actually do them.  I know.  I'm a human.  ;)

---

### Post by dragonfly41 on 2021-01-04
All very solid advice from @TheFu which I have bookmarked and will apply.
But are there any points to look out for in my desktop 20.04 (running on external SSD1) 
with a second external SSD2 dedicated to backup? 
In particular, I am constantly juggling around (relocating) development directories in $HOME and installing new apps to test which in turn are reflected into various configuration files. For example I have just installed a batch of Java apps.
Image backups are soon out of kilter. In other words, what is the best backup plan for a fast changing desktop development landscape and filesystem? Backup while still actively developing is important.

---

### Post by wmcl on 2021-01-06
What's everyone's strategy for reliably dealing with encrypted homes?

The only idea I could come up with so far was to mount the volume the homes are on into a different directory and back up the users' homes in their encrypted state, which of course creates the problem of having to deal with huge binary files each of which changes every time the users log in, rendering file based incremental backups pretty much useless in terms of saving storage space.

Detecting whether an encrypted home is mounted and only backing up those that are currently mounted breaks the encryption and runs the risk of not having any recent backup of the home of users that happen to be logged out when the backup happens. Just ignoring the reality of encrypted backups will create a huge mess of sometimes backing up a home in its encrypted state and sometimes unencrypted, depending on whether the user is logged in at the time of the backup.

---

### Post by dragonfly41 on 2021-01-06
I have had Tressorit[ bookmarked]("https://tresorit.com/") for some time pending future consideration.
But I have not applied it so far. 
Still wary about implications of encrypted cloud as incremental backup.
I would appreciate views on this.

---

### Post by Advait on 2021-08-27
> **ml9104 said:**
> Timeshift as default excludes all user directories. That is: $HOME and /root. This is fine for a system backup - except it isn't 100%.

What you should do is to add "Hidden directories" and $HOME/Desktop to the backup directories.

Then you can play around as you like.

This was very helpful. I just updated my Timeshift settings per these suggestions. Thanks!

---

### Post by Advait on 2021-08-27
> **ml9104 said:**
> Timeshift as default excludes all user directories. That is: $HOME and /root. This is fine for a system backup - except it isn't 100%.

What you should do is to add "Hidden directories" and $HOME/Desktop to the backup directories.

Then you can play around as you like.

PS: How did you get the thumbnail images into your post? What menu button creates those thumbnails?

---

### Post by monkeybrain20122 on 2021-08-27
> **Advait said:**
> PS: How did you get the thumbnail images into your post? What menu button creates those thumbnails?

Scroll down and click "manage attachment", then upload a screenshot and attach.

---

### Post by oldfred on 2021-08-27
If you use the Forum's Go Advanced editor, you can use the paperclip icon to attach screenshots. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
Forum do & don't
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by Advait on 2021-08-28
> **monkeybrain20122 said:**
> Scroll down and click "manage attachment", then upload a screenshot and attach.

> **oldfred said:**
> If you use the Forum's Go Advanced editor, you can use the paperclip icon to attach screenshots. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
Forum do & don't
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

Got it. Thx!

---

