---
title: "Backup everything"
date: 2007-08-28
forum: General Help
---

### Post by PurposeOfReason on 2007-08-28
I've read a few howto's on the forum and a couple others through google though none seem to help much for what I'm trying to do. At the moment I dual boot Ubuntu and XP though the XP partition is more 'safe' because I don't ever go into it. What I'm trying to do is backup everything, settings, email contacts, bookmarks, files, or anything possible and save it as a tar. Then move that to my XP partition where it would just sit and then if something on Ubuntu went horribly wrong, I could copy that file to the new Ubuntu installation, extract it, and have everything as it was.

---

### Post by kidders on 2007-08-30
Hi there,

Is "**tar czf [PathToBackup] ~**" not sufficient for your needs?

---

### Post by PurposeOfReason on 2007-08-30
I thought about doing that, but if I were to do that with say, "/", would it still work?

---

### Post by por100pre1 on 2007-08-30
Maybe backing up your /home folder with Grsync can do the job. Just keep in mind that writing to your xp partition will require ntfs-3g, and it can be messy. So be careful.

---

### Post by kidders on 2007-08-30
> **PurposeOfReason said:**
> I thought about doing that, but if I were to do that with say, "/", would it still work?I suppose so, but doesn't Windows get upset when it's asked to handle very large files? Making a giant tarball of '/' would be overkill anyhow. You'd find yourself backing up *lots* more than you really need.

If what you want could be described as a sort of a "system snapshot", then you might consider taking byte-for-byte dumps of some of your disk partitions. What you'd end up with could simply be written directly back onto a botched up disk at some point in the future, by virtually any OS.

Personally, my ideal backup contains nothing in any way related to my operating system ... only personal files & settings. In a sense, I tend to consider my OS to be "disposable". In the event of a major screw-up, I simply reinstall a new one (ie not necessarily the *same* one), and restore my personal data from the backups.

Each to his own though ... you should do whatever you feel comfortable with, and do it whatever way you feel sure you can restore confidently, in the event you ever need to.

> **por100pre1 said:**
> Maybe backing up your /home folder with Grsync can do the job. Just keep in mind that writing to your xp partition will require ntfs-3g, and it can be messy. So be careful.Yep! It's also worth bearing in mind that, arguably, storing your files *and* their backups on the same physical disk is probably unwise, since it only protects you against problems that aren't hardware-related.

---

### Post by -SpaZ on 2007-08-30
It would be really easy to just put a copy of your Home folder on a usb drive.

---

### Post by beercz on 2007-08-30
[http://rsnapshot.org](http://rsnapshot.org)

---

### Post by jay4e on 2007-09-06
its important to note that tar is not a good primary back up for your root system.  it doesnt back up the file system and thus if you restore to a new drive or a repartitioned drive your in for some trouble. 

however most of what you are talking about is all contained in /home (bookmarks, email, desktop, ect...).  so tar is good for /home but to back up root you need to use dd or some other back up program.

---

### Post by por100pre1 on 2007-09-06
> **kidders said:**
> Yep! It's also worth bearing in mind that, arguably, storing your files *and* their backups on the same physical disk is probably unwise, since it only protects you against problems that aren't hardware-related.

I agree with you. I actually keep my backups in an external HDD, good advice. :)

---

### Post by rg_stephens on 2007-09-07
I hope I'm not changing the subject, but I have a dual boot laptop and I've decided that I want to totally ditch XP. I'm under pressure to get some CAD projects done for school, and I'm out of disk space on my linux partition. 

I don't have time to install and re-configure everything. Can I just back up the entire "/" onto DVDs and then somehow move it back after I delete my current partition? Is this even necessary? If I knew everything was installed in "/home" it would be easy. I tried resizing, but it Gparted didn't let me do it.

---

### Post by kidders on 2007-09-07
Hi there,

> **rg_stephens said:**
> Can I just back up the entire "/" onto DVDs and then somehow move it back after I delete my current partition?Yes, you can. There are various approaches to doing it. If the amounts of data you're dealing with are relatively small, and you have lots of spare (perhaps removable) disk space, the one that would probably give you the best results would be ...
[LIST]
[*]Make a giant tarball out of your whole system.
[*]Chop it up into DVD-sized bits.
[*]Wipe & repartition your hard disk, etc.
[*]Re-concatenate the tarball & extract its contents into your new filesystems.
[*]Perform any necessary tweaks.[/LIST]However, if all you're planning on doing is erasing a filesystem currently used by Windows, you needn't bother going to all that trouble. Instead, you could simply decide to use the space as a /usr directory, or maybe your /home ... or both.

> **rg_stephens said:**
> I tried resizing, but it Gparted didn't let me do it.Partition resizing should never be done without making a backup anyway, so it's very rarely useful in the sort of situation you've described.

---

### Post by rg_stephens on 2007-09-07
> Instead, you could simply decide to use the space as a /usr directory, or maybe your /home ... or both.

That sounds like a great idea. I'm not clear how to do it, but I'll try... all my important stuff is already backed up, it's just a hassle getting programs reinstalled

So after I delete the XP partition and create a new partition, I could just move files from /usr and /home to my new location, like /media/sda3/usr or whatever and create simlinks to the new location?

---

### Post by kidders on 2007-09-07
More or less, yeah.

Don't type this straight into a terminal without thinking, but something in the same ballpark is what I would do, personally. For the sake of argument, sda1 is your Windows root.

```
$ sudo su
# mkfs.jfs -L "Home" /dev/sda1
# mkdir /mnt/newhome
# mount /dev/sda1 !$
# cp -dpR /home/* !$
# umount !$
# rm -R !$
# mv /home /home.old
# mkdir /home
# mount /dev/sda1 /home
# nano -w /etc/fstab
```

Anyhow, like I said, that's just intended to be a general explanation, rather than something to be copied verbatim ... if you'd prefer me to translate it into English, I'd be happy to though!

In any case, the point is that Linux doesn't mind being spread over multiple filesystems (in fact it is traditionally laid out that way), and you should be able to do it on your own box in around 10 short commands. One thing worth underlining is that you should only attempt something like this under very controlled circumstances...
[LIST]
[*]**lsof | grep /home** should return nothing (ie nothing you're about to copy is in use).
[*]Your X server has been stopped.
[*]Nobody is logged into your box remotely.
[*]And so on.[/LIST]Once you were confident the copy went well, you could delete /home.old to reclaim some disk space.

What would you think of that approach?

---

### Post by rg_stephens on 2007-09-07
I'm not familiar with some of the commands, but this is basically what I want to do. I'll check out the manual pages before I do something rash. Eventually I want to do this with /usr as well, because I think that's where most of my programs are, most likely.
 
Thanks for helping me out with this. I'm still learning my way around in the Linux world. I generally don't pay attention to where I install programs, and then I can't find them once they're installed.

---

### Post by kidders on 2007-09-07
> **rg_stephens said:**
> I'll check out the manual pages before I do something rash.Be sure to post back if you have trouble with the man pages ... some of them can be a little impenetrable lol.

> **rg_stephens said:**
> I generally don't pay attention to where I install programsBy convention, applications tend to go one of four places:
[LIST]
[*]/usr
[*]/usr/local
[*]/home/<username> (in rare cases)
[*]/opt[/LIST]Exactly what winds up where is something you develop a sense for after a while. If you lose something, you can always try **whereis realplay** or **whereis firefox** and so on.

Just by way of further explanation, in case you need it...

[B]sudo su
[/B]Switch to super-user mode and stay there 'til you hit CTRL+D.

[B]mkfs.jfs -L "Home" /dev/sda1
[/B]Wipe /dev/sda1 and replace it with a JFS filesystem called "Home". The filesystem choice is a personal one ... entirely up to you.

[B]mkdir /mnt/newhome
mount /dev/sda1 !$
[/B] Create a temporary mount point & put /dev/sda1 there.

[B]cp -dpR /home/* /mnt/newhome
[/B]Recursively copy (NB: *do not move*) the contents of /home to the new filesystem, being careful to preserve all permissions & ownership.

[B]umount /mnt/newhome
rm -R !$
[/B]Unmount /dev/sda1 and remove the temporary mount point.

[B]mv /home /home.old
mkdir /home
[/B]Move /home out of the way & create a new, empty one.

[B]mount /dev/sda1 /home
[/B]Mount the new "Home" filesystem.

[B]nano -w /etc/fstab
[/B]Make this change permanent, by appropriately modifying /etc/fstab. Any system services you stopped can then be restarted, and you can continue using your PC as normal.

> **rg_stephens said:**
> Eventually I want to do this with /usr as wellIn that case, depending on the size of the filesystem you intend to erase & hand over to Linux, you might want to repartition it into two chunks before getting started.

If you're trying to decide what's worth moving to a partition on its own, and what's best left where it is, you might like to try the "du" tool, to see where the space guzzlers are at. For example, try...```
sudo du -sh /home /usr
```

That command will take a *long* time to run. The "sudo" is only necessary where your system has multiple users, in which case your own account won't have sufficient privileges to calculate the space being used by /home.

---

### Post by rg_stephens on 2007-09-07
Thanks!!! These commands will help me out a lot.

---

