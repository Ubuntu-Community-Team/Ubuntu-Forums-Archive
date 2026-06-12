---
title: "Problem after interrupted backup"
date: 2016-07-09
forum: General Help
---

### Post by VanillaMozilla on 2016-07-09
Using Deja Dup, I think.  Whatever the program is in Ubuntu System Settings/Backups.

I made the mistake of shutting down the computer to a USB2 drive while doing a full backup.  No problem, I sez.  Just delete the files and back up again.  But, in spite of lots of new duplicity-full files, there is no signatures or manifest file, and Deja Dup tells me the last backup was done 44 days ago.

So I reboot, and it still tells me the last backup was 44 days ago.  OK, no problem.  I look at the duplicity manual, and it tells me
duplicity cleanup --force file://media/mylogin/MyDevice/path/
(which may or may not solve my problem).

So I try that and it tells me
Local and Remote metadata are synchronized, no sync needed.
Last full backup date: none  **(none?!)**
GnuPG passphrase: Mylogin@MyComp:~$ cd /media/mylogin/MyDevice/path/

How wonderful.  Deja Dup is giving it a passphrase?  Or what?

Suggestions?  Somehow I need to get Deja Dup on track again.  I have about 350 GB to back up, so it's not so easy just to start wiping stuff and experimenting.

---

### Post by DuckHook on 2016-07-11
I don't use deja-dup (duplicity), but rsync directly instead, so can only point out the most obvious stuff and can't help with details, but:

You mention the command:```
duplicity cleanup --force file://media/mylogin/MyDevice/path/
```Did you use the command *exactly* as you've posted here, or did you first substitute your own proper values for the generic placeholder names in this example? You must substitute proper values.

If you did not substitute proper values, then of course Duplicity will return a message saying everything is good: because, indeed, there are no files requiring syncing on an empty or nonexistent directory.

No idea about why it is asking for a passphrase except for the fact that you are pointing to a nonexistent device with:```
/media/mylogin/MyDevice/path/
```...so it may erroneously assume that access is being denied because this location is passphrase protected (just a guess).

As for suggestions: You may simply find it easier to work with rsync directly, as I do. Deja-dup/Duplicity is just an app based on rsync anyway. It tries to make the complexity of the rsync command line "friendly" by slathering a pretty GUI on things, but at heart, it is just rsync. If correcting the above entries don't work (or if that wasn't the problem in the first place), then I would suggest skipping the wrapper app and going straight to the meat of the matter. If you simply must have a pretty GUI for rsync, you can install grsync which will provide a basic graphical front-end for rsync with many of the most important options available via check boxes and radio buttons.

---

### Post by VanillaMozilla on 2016-07-11
No, the path was correct, and it was filled in by auto file completion.

You're right, I suppose I could just use rsync, but that's a nightmarish program for a very simple task in this case.  It would have the advantage that I could actually find files in the backup, but the drawback is that it doesn't compress.  For that matter, I could just copy the files, but I'd rather use tar and zip.  The first option is to fix the archive I have, since I just have to push a button.

---

### Post by DuckHook on 2016-07-11
Sorry, but I can't help further with Deja-dup(licity) since I don't use it. I hear what you are saying, but you may wish to double-check your path anyway just to make absolutely sure... easily done with a series of *ls* commands, starting at /media, then /media/mylogin and keep drilling down. Unless duplicity mounts your drive this way, these would not be the natural values that the OS assigns to a connected drive.

Years ago in my Windows days, I used to compress and do incremental backups, etc. but I've found that, with large capacity drives now so cheap, I no longer do so. The advantages are considerable&#8213;the most important being that I know for sure that I can restore.

Good luck and hope that someone with knowledge of duplicity sees this thread.

DH

---

### Post by VanillaMozilla on 2016-07-11
The path really IS correct.  I think the --no-encryption switch should be used, but that also tells me there's no backup.  It turns out, that's the correct answer, as Deja Dup is unable to find any backup files.

I checked some files in a tar.gz archive, and it turns out (Gnu?) Archive Manager often crashes.  It does restore files, but applications that crash are unacceptable on my system if I can avoid them.

Plus, it took a long time to read an 11 GB archive.  So for now I'm going to avoid tar.

[B]OK, back to basics.  Only well-tested, well-understood bullet-proof command lines that have been in everyday use since the year 1 will be considered, at least until Deja Dup can be proven reliable.
sudo cp -a src dest
(or sudo cp -ar src dest ?)
should do the trick.[/B]

I believe
sudo rsync -a src dest
also works, but I have played with it in the past and found it treacherous.

---

### Post by VanillaMozilla on 2016-07-12
OK, for what it's worth, I told Deja Dup to keep files for at least 6 months and made yet another backup.  This time, all appears to be well.

As a test, I deleted a couple of files and then restored them.  It was quite easy from Nautilus, and fairly prompt--I'm guessing maybe 2 minutes to find the files, and completely restore in 4 minutes.  Rough guess -- I didn't time it.

It was previously set to keep backups forever or until space was needed.  I hoped that by changing to 6 months, that would prompt it to trim the files.  It not only removed the old backups, but it also removed the bad ones from yesterday.

So, bottom line:  self-fixing.

---

### Post by VanillaMozilla on 2016-07-12
> **DuckHook said:**
> Years ago in my Windows days, I used to compress and do incremental backups, etc. but I've found that, with large capacity drives now so cheap, I no longer do so.

Deja Dup can also back up a mounted Windows disk.  In fact, I back up one Windows directory with my /home/ directory.

I doubt that it can do the boot block, however.  For that I do
1. Defragment the disk.
2. sudo dd if=/dev/zero of=/pathToWinDisk/zero.file; sync; rm zero.file;
(Fills all empty space with zeroes, then deletes the file.  Alternative you can use SDelete.exe from SysInternals.)
3. sudo dd if=/dev/sdwhatever bs=4M |gzip > /pathto/archivefile.img.gz
(or give it a name that includes the backup date).

I have not tested this for restoration.  It might be slow.  Also not tested for recent Windows, with UEFI and other gimmicks--but it should work.

---

### Post by DuckHook on 2016-07-12
Congrats! Self-solved solutions always feel so good. :guitar:

---

