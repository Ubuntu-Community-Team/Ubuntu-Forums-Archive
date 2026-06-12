---
title: "[SOLVED] Totally hosed my perssions, need advice"
date: 2008-01-30
forum: General Help
---

### Post by peabody on 2008-01-30
[B]Edit: Good news!  I booted a live cd and mounted my drive.  Turns out the only problem was that the execute bit had been turned off of / and my home folder.  I will say with utmost certainty that it was the find command that caused the outage, because that command was only concerned with the execute bit.

Still, I'm a bit confused and flustered...I don't know why that command would have done what it did.  My hypothesis is the symbolic link thing.  I guess I'll have to test that out for myself.

Edit: Yep!  Undeniably the symbolic link thing![/B]

This is somewhat embarrassing.  I've used Linux since 1999, administered servers, writen scripts, tweaked apache.  Not once in that time, have I ever managed to do something like this, and I'd like think that I'm fairly comfortable around the command line.  To be fair, I think once I explain the circumstances you'll understand how I made the mistake...

I had an external drive that I use for backup purposes.  I use a slight modification of the script found here for incremental backups of my home folder (just my home folder, I'm currently rethinking this philosophy).

[http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html)

Recently it was acting up and rsync was giving me IO erros.  I was worried the drive might be dying on me, so I umounted it, and ran an e2fsck -C 0 -c /dev/sdb1 on it.  Thankfully, no bad blocks were found, but quite a frightening number of file systems errors were reported and fixed.

After this, I plugged the drive in, ran the backup script again and happily, no errors were reported this time and the script completed.  Some time passed and I got the idea of looking into the lost+found folder.

This would prove my undoing.  I'm still not *exactly* sure what technically happened next, but I have a vague idea what did.  But I'm getting ahead of myself...

My first instinct was to try and glance at lost+found on /media/Backup in nautilus.  This of course, didn't work...silly me...of course that would require root privilges.  So I proceeded into a terminal and one 'sudo su' later, was taking a look-see through the graveyard of orphaned inodes.

This, for anyone who hasn't done it, isn't a particularly readable listing of stuff.  It's largely a huge amount of folders numbered by god-knows-what, my guess is the # of the orphaned inode.  I saw pretty quickly that this would be a pain to browse on the terminal...

and here's where I became unacceptably lazy...

Sure, I know of midnight commander.  I realize there's ways to open a nautilus with root privileges.  But nah, that'd be a pain!  All this stuff just sitting in here on a removable drive.  I'm only the one who cares about it, screw it, why don't I just chmod this mess into something readable by nautilus.

```

cd ..
chmod -R 777 lost+found

```

Oops, that's right, probably don't want all those regular files having their execute bit set.

```

find lost+found \! -type d -exec chmod 664 {} \;

```

Not shortly after this...my desktop went bananas.  It was the apocalypse.  Icons went white, fonts became boxes and I came to the horrific conclusion that I had done something terribly, terribly stupid.

So ***what*** actually happened?  All I know is, the find walked lost+found on my external drive and somehow ended up on my /.  Can't exactly fathom how.  My best guess, is that it the '\! -type d'  in the above find command, told find to work with symbolic links.  And that somehow, bounced the bugger onto my /.  I tried rebooting...no avail.  My best guess is that files under /lib got their executable bits unset.

Historically, I know these sorts of things usually require a reinstall.  It's late, I have school tomorrow, and I really, really would like to see if there's a better solution to this than that.

I'm all ears, but I have my CD ready just in case I have to start this over.

*sigh*... it's been a long day...

---

