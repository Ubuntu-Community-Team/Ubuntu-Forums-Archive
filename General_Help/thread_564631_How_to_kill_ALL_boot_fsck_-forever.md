---
title: "How to kill ALL boot fsck -forever?"
date: 2007-10-01
forum: General Help
---

### Post by ubudabbler on 2007-10-01
I am a multi-flavor guy. I run several OS-s, incl 4 different linux.
I really like Ubu, it seems to grab/use more HW components than any others.
It would be my favorite except for two VERY annoying problems with Ubu:

First, I cannot get out of a big fsck waste of time at EVERY boot.
I have one partition that I experiment with, made my own OS.
And apparently, Ubu hates that partition.

On my desktop AND my laptop, every Ubu release does the same thing
at the same boot point... halts, tells me it cannot fix that partition.

And by God, even after admitting that, it tries AGAIN -every boot.

FC6, Suse and PClinux have no problems there.
(Suse even recognizes it as a UNIX, and correctly lists it in Yast/Grub).

So this is an UBU-only issue here. But I am growing FONDER of Ubu's support
resources, so I would really like to solve this.

What I want to do is tell Ubu to NEVER NEVER start fsck at boot!
I tried the usual fsck shutoff: sudo tune2fs -c 0 /dev/hdxy
and it balks on that, too. Refuses.  Starts telling me THEN that Win Tel is
wrecked, too... which it definitely AINT (it has NEVER seen the net-never will).
This isprobably due to the fact that my own lil OS is between the W2K and XPpartitions, sofsck gets confused on my hda5 OS oddity, and that effects its view of hda6.

Sorry, I know lots of people like stuff like "autofsck", but IMHO, letting ANY operating system run a auto-repair program in "limited-aware" mode is plain dumb. If the system is broken, why would I want to TRUST it to repair itself, when it has dumbed itself down to a minimal kernel and cast out MOST of its resources? I boot alive CD,with a TRUSTED and KNOWN GOOD ro OS, to fsck my partitions.That is the ONLY sensible way I believe it should EVER be done.

OK, my opinion, maybe most disagree. Regardless, it is obvious Ubu does fsck different than any other Lin that I know of, so if anybody knows how to TOTALLY castrate FSCK, I would sure appreciate the secret.

I would send you a box of penguins -or make any other promise, if you can help! :)

---

### Post by mcduck on 2007-10-01
Just edit the /etc/fstab file, and change the last number on partition's entry line to '0' to disable fsck on that partition. 

I would recommend at least keeping the setting as '1' on your root partition though. And use '2' for other partitions you want to run fsck on. They will only be checked on every 30th boot (at least after you have disabled fsck on the partition that's causing problems for you).

---

### Post by ubudabbler on 2007-10-01
Thanks! I had done that already.
Had the first 3 partitions set to zero.
BUT HERE IS THE AMAZIN PART:
i decided to turn all the linux to zero, too
except Ubu.
still same results...
went backand zeroed Ubu -and the problemstopped.
This (seems to) indicate my fluke partition has
fsck calling Ubu partition 2 instead of 5.serious confusion.
Maybe because Ubu uses UUID instead of "dev/hdaxx"???
Or maybe it is just takin' grub away from Ubu that wrecks something.

That is the only other factor i can think of...always load Suse last,
because i like the uer interface on Grub 
(and i guess I trust it more for grub,
since it always sees/sets up all my others -including the fluke.)

Anyway, since you sent me back to the place where i solved the problem,
the credit is all yours. I sure do thank you for the pronto post,amigo.
penguins on the way!

Ubu really does get my laptop better than anyone else.
intel 2200 wifi, wide screen intel 915 vid, SD slot... all loaded/waiting
for me after install(915 takes a few adjustments afterwards).
But nobody else gets all3 of those. Then,there is guys like you.
Good SW,good community,excellent OS. Thanks again!

---

### Post by randiroo76073 on 2008-02-26
I've got the same problem as ubudabbler, I too am multi booted & use Gutsy-64 as my swing partition.  Is there any other solution to this other than zeroing out all in fstab?  I tried a script "autofsck"  that was supposed to change fsck from startup to shutdown, unfortunately it didn't work on my machine[have queried author], I would be OK with it at shutdown/reboot, just not at startup.  Thanks for any help   :)

---

### Post by Herman on 2008-02-26
> I've got the same problem as ubudabbler, I too am multi booted & use Gutsy-64 as my swing partition. Is there any other solution to this other than zeroing out all in fstab? I tried a script "autofsck" that was supposed to change fsck from startup to shutdown, unfortunately it didn't work on my machine[have queried author], I would be OK with it at shutdown/reboot, just not at startup. Thanks for any help :smile:                                                               __________________
If you really have a problem in your file system, fsck will run and try to fix it. The automatic fsck runs fsck -C -R -A -a , which is okay, but may not be able to fix all file system problems.
If it doesn't, and you are getting fsck on every reboot, you might need to run a more specific file system check. Run e2fsck directly, and try to choose the appropriate options. [                      Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line.

If you don't know how to run e2fsck yourself (how to choose the right options), the easy way is to [run a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")( a user friendly GUI method).  That runs resize2fs and  e2fsck -f -v -p, and will actually fix most of your file system problems or at least tell you why not. When your problems are fixed, fsck might not need to run again for another thirty or so boots.

The most common cause of fsck running on every reboot is when there is a mistake in your /etc/fstab file or the file has not been updated since partitions have been changed.
The proper way to fix that is to update your /etc/fstab file.
To update your /etc/fstab files you just need to run '[COLOR=#000000][FONT=Bitstream Vera Sans Mono]ls /dev/disk/by-uuid/ -alh'and compare the UUID numbers in the output with your /etc/fstab file and correct the /etc/fstab file accordingly.[/FONT][/COLOR][ About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")

Regards, Herman :)

---

### Post by randiroo76073 on 2008-02-26
Sigh, have ckd  & rechkd all.  Here is last checkfs log. same as previous 3 reboots[except time] w/fsck running on every reboot. As far as I can acertain there is nothing wrong with my system.  Maybe it doesn't like me running all those other distro's  LOL!

Log of fsck -C -R -A -a 
Tue Feb 26 05:11:23 2008

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb1: 17259 files, 1312511/2092383 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb2: 29396 files, 1444592/2092391 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb3: 165643 files, 2160425/4603887 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda15: 253240 files, 4353620/5704302 clusters
Gutsy_h: recovering journal
Gutsy_h: clean, 36793/2626560 files, 4026399/5242880 blocks
Parsix_r: recovering journal
Parsix_r: clean, 137286/1966080 files, 724827/3931900 blocks
Parsix_h: recovering journal
Parsix_h: clean, 159133/2626560 files, 1896316/5242880 blocks
/dev/hda7: recovering journal
/dev/hda7: clean, 111567/1966080 files, 687208/3931900 blocks
/dev/hda8: recovering journal
/dev/hda8: clean, 2369/2626560 files, 268724/5242880 blocks
/dev/hda9: recovering journal
/dev/hda9: clean, 11/1966080 files, 104098/3931900 blocks
/dev/hda10: recovering journal
/dev/hda10: clean, 11/2626560 files, 126483/5242880 blocks
/dev/hda11: recovering journal
/dev/hda11: clean, 11/1966080 files, 104098/3931900 blocks
/dev/hda12: recovering journal
/dev/hda12: clean, 11/2626560 files, 126483/5242880 blocks
/dev/hda13: recovering journal
/dev/hda13: clean, 11/1966080 files, 104098/3931900 blocks
/dev/hda14: recovering journal
/dev/hda14: clean, 192379/2626560 files, 4805674/5242880 blocks

Tue Feb 26 05:13:05 2008
----------------

---

### Post by articpenguin on 2008-02-26
recovering jorunal means that you had an unclean mount and the kernel is replaying the journal to restore meta data consistancy.


you can avoid those long fsck times by changing filesystems to JFS or reiserfs.

---

### Post by randiroo76073 on 2008-02-26
I thought I was using a journeled file system, ext3 is what I use.

---

### Post by articpenguin on 2008-02-26
ext3 is a journalled filesystem

---

### Post by randiroo76073 on 2008-02-27
Have run Smartsuite & other drive integrity tools, all drives chk out good, guess I'll do a re-install this weekend and see if that cures it.  LOL! a good thing, after all tests I've run I know my puter's in good health.

---

