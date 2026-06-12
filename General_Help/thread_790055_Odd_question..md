---
title: "Odd question."
date: 2008-05-11
forum: General Help
---

### Post by The Avatar of Time on 2008-05-11
Hello,

I have five hard drives and the way they are mounted is: 

I have one that is partitioned off for root, home, and swap. 

The other four I have mounted as 1,2,3,4 inside a folder named media-server in my home folder. Or rather in /home/avatar, thus being /home/avatar/media-server. 

Now I want to backup my /home/avatar folder to one of the four media-server drives, just in case the drive it's on goes bad. Now the problem is that if I try to copy /home/avatar into say drive 4 then it tries to also copy the contents of /home/avatar/media-server also. 

So how would I go about copying the contents of /home/avatar to /home/avatar/media-server/4 without it trying to copy the media-server contents? I can't unmount media-server or I couldn't copy to it.

I know I could just do it one folder at a time, but that would be boring. I will, of course, do it that way if it is the only way, I just thought that I would try for a quicker method first. I guess by the time I get a reply I could have just done it the other way, but that's alright because I have a few things to do right quick anyhow. Now I hope I explained this okay, if not I will try to elaborate more. 

Thank you for any assistance provided.

---

### Post by Rocket2DMn on 2008-05-11
We don't normally mount drives in the /home directories, they are usually put in /media
I suggest unmounting them, changing their mount points in fstab, then remounting them at the new locations.  Then you can easily backup anything in your /home directory without recursing into other drives.

---

### Post by The Avatar of Time on 2008-05-11
I see, thank you for the information.

---

### Post by der_joachim on 2008-05-11
You could use a program like rsync of rdiff-backup. At home I use rsync. The advantage of rsync is that only the files modified since tha last synchronisation will be copied to your backup folder. AFAIK, symlinks are ignored by rsync. If not, you can use the --ignore option to explicitly ignore your home media backup folder.

If you do not feel comfortable using the command line, use the grsync tool. It should be in the repos.

---

### Post by sdennie on 2008-05-11
You could use tar with --one-file-system.  That should prevent it from recursing down your mounted partitions.

---

### Post by The Avatar of Time on 2008-05-11
Thank you,

I'm a Fluxbox user so I use the command line a bit, still rather new so I don't know many of the things that can be done with it though. 

What code would I use to do this? Something like:

```
cp /home/avatar /home/avatar/media-server/4 --ignore /home/avatar/media-server
```

? The copy feature is something that I rarely use, I generally use Midnight Commander instead so if you could elaborate a bit I would appreciate it.

Thanks.

---

### Post by The Avatar of Time on 2008-05-11
> **vor said:**
> You could use tar with --one-file-system.  That should prevent it from recursing down your mounted partitions.

Would that work with cp also? I have plenty of room so I have no real desire to compress anything.

---

### Post by sdennie on 2008-05-11
I don't think cp has --one-file-system.  Really, if you want a more solid option, you may want to look at simple backup:

```

sudo apt-get install sbackup

```

That should allow you to easily customize and setup backups.

(It will be installed in System->Administration->Simple Backup).

---

### Post by Rocket2DMn on 2008-05-11
> **The Avatar of Time said:**
> Would that work with cp also? I have plenty of room so I have no real desire to compress anything.

Yes, it will, you can always check man pages on commands, ex:
```
man cp
```
Scroll with KB or mouse wheel and hit q to quit from the man page.  Again, I suggest moving the mount points, but it's really your preference.  In this case the command would probably be
```
cp -Rx /home/avatar /home/avatar/media-server/4
```
-R = recursive
-x is synonymous with --one-file-system (for cp, -x is different for tar)

However, I think you are still making work for yourself.  If you are serious about making backups, I use a program called Simple Backup (sbackup in the repositories).  You can specify which folders to include in a backup and which folders to exclude.  So you can include /home and exclude /home/avatar/media-server/1 (and 2, 3, 4).  You access Simple Backup from System->Administration->Simple Backup Config.  It creates compressed backups, so it is not as useful for backing up lots of music, photos, and videos, but is great for backing up configurations and text files.

edit: oh snap, my man vor also uses sbackup :)

---

### Post by The Avatar of Time on 2008-05-11
Not to argue, but -x is listed as --one-file-system in cp --help and man cp. However, I don't seem to be using cp right because I tried as a practice to:

```
cp /home/avatar/documents ~/media-server/1
```

And I get a:

```
cp: omitting directory '/home/avatar/documents'
```

What is it that I am missing out on here? I also tried sudo with the same result.

Oops, I was still typing when you posted. What is the reason that /home/avatar is listed twice in a row? That is apparently what I did wrong. 

Also I should have mentioned, the reason that I wasn't wanting to install anything just yet is because as soon as I get this done I am installing Hardy, and I have a monthly download limit so I try not to waste it.

Oh, I see now. It is to specify that /home/avatar is what the -Rx applies too. I can be dense some times :).

---

### Post by Rocket2DMn on 2008-05-11
Sorry, I fixed my post, that was a typo.

So your login name is william, but you have the systems mounted under the avatar username?  This is just getting confusing.  I would change your mount points like I suggested earlier so that we are working with the generally accepted way of doing things, it will take the confusion out of this process.
BTW, I'm going to bed soon, it's going on 1:30 am here.

---

### Post by The Avatar of Time on 2008-05-11
I just had to fix a typo in mine too. My real name is william, and it's getting late (3:42 here) so I typed my name on the post instead of what it should be: avatar. My mistake.

I already used your code before you edited it and it seems to be working. Will it hurt anything that way that it is?

Yes, this has been a learning experience and when I get Hardy installed I will fix everything to how it should be. The reason that I mounted them in /home/avatar to begin with is that I didn't know how to make links and wanted them handy instead of clear over in media.

---

### Post by Rocket2DMn on 2008-05-11
You should be OK to use the command, assuming the information you gave me is correct.  However, with the one filesystem command, I'm not even sure it will allow you to copy from one filesystem to another, so the command may not even run.  If you don't feel comfortable running any command ever, don't run it!
If you want to edit /etc/fstab to change the mount points, let me know and I will get back to you in the morning.  I really do think this will be the easiest way to fix your problem, you won't have to deal with any recursive mounting and excluding and all that jazz.

---

### Post by The Avatar of Time on 2008-05-11
It seems to be working right so far. It made a media-server and 1-4 folders but did not try to put anything in them, just like I wanted.

Yep, it just finished and everything seems to be in order. Thanks to everyone for the help. I'll have everything setup as it should be by morning. Unless I fall asleep on my chair here :).

---

