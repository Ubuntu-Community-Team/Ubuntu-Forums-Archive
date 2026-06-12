---
title: "Shred Command in Terminal"
date: 2016-10-05
forum: General Help
---

### Post by Incarnadine on 2016-10-05
I was curious to know how Shred works.

I used Shred to erase a HDD, but the partitions still existed on the HDD after the shred process was finished. I was under the assumption that shred would work like DBAN, and would erase everything from the HDD. I'm obviously wrong, and would like to know how Shred works, and why it didn't wipe the partitions on the HDD.

---

### Post by HermanAB on 2016-10-05
Well, firstly bear in mind that Shred doesn't actually work...

---

### Post by Keith_Helms on 2016-10-05
shred writes over files multiple times to hide whatever they originally contained.  It doesn't remove partitions.  see
```
man shred
```

---

### Post by yetimon_64 on 2016-10-05
> **HermanAB said:**
> Well, firstly bear in mind that Shred doesn't actually work...
It works fine here ... your source of info ? I realize there are limitations regarding some journalling setups or RAID arrays with it not being effective but under a default installation it still works as far as I'm aware and can still use it here.

> **Keith_Helms said:**
> shred writes over files multiple times to hide whatever they originally contained.  **It doesn't remove partitions.**  see
```
man shred
```

I can't see any reference to what you say there in the man file, even though there are some constraints on it effectiveness  ...
> ```
       Delete FILE(s) if --remove (-u) is specified.  The default is not to remove the files  because
       it  is  common to operate on device files like /dev/hda, and those files usually should not be
       removed.  When operating on regular files, most people use the --remove option.

       CAUTION: Note that shred relies on a very important assumption: that  the  file  system  over&#8208;
       writes  data  in place.  This is the traditional way to do things, but many modern file system
       designs do not satisfy this assumption.  The following are examples of file systems  on  which
       shred is not effective, or is not guaranteed to be effective in all file system modes:

       *  log-structured  or journaled file systems, such as those supplied with AIX and Solaris (and
       JFS, ReiserFS, XFS, Ext3, etc.)

       * file systems that write redundant data and carry on  even  if  some  writes  fail,  such  as
       RAID-based file systems

       * file systems that make snapshots, such as Network Appliance's NFS server

       * file systems that cache in temporary locations, such as NFS version 3 clients

       * compressed file systems

       In  the  case of ext3 file systems, the above disclaimer applies (and shred is thus of limited
       effectiveness) only in data=journal mode, which journals file data in addition to  just  meta&#8208;
       data.   **In  both  the  data=ordered  (default) and data=writeback modes, shred works as usual.**
       Ext3 journaling modes can be changed by adding the data=something option to the mount  options
       for  a particular file system in the /etc/fstab file, as documented in the mount man page (man
       mount).

       In addition, file system backups and remote mirrors may contain copies of the file that cannot
       be removed, and that will allow a shredded file to be recovered later.

```
If you want to remove partitions run it as root on the device file for the drive (DO NOT use the -u switch which will remove the device file permanently though). Any boot records and partition information will also be erased. Remember though it is only effective on a default installation and NOT on a RAID set up though. 

_*I wonder what the OP's circumstances are regarding those constraints if it failed to wipe partitions (I would suspect some sort of RAID array may be in use).*_

@ OP, are you using a RAID array or do you have non standard journalling boot options set up on your installation ? That could explain why shred failed for you if the command you used was correct for the task.

On a default installation not using RAID the next command will clean off a complete drive including partition information (it is not designed for secure deletion with the iterations switch at 0, though that can be increased if needed)...
**Warning: do not use this next command on /dev/sda of a newer UEFI drive unless you have a backup of the EFI boot partition (YOU WILL LOSE IT)...**
```
sudo shred -fvzn0 /dev/sd**x**
``` where **x** is the drive letter of the drive to be cleaned off.

The switches used : f=force, v=verbose, z=zero (do a final run of zeros over the file), n0 = 0 iterations (no random data etc, just do the previously listed zeroing run. If you want it more secure increase the iterations, the default value is 3 runs if not otherwise specified.) 

**Edit:** On newer large drives shred is incredibly slow to do a full run and can take days to complete a drive. I use the iterations switch to speed up run times at the expense of "security". My use of shred is more for when rearranging data partitions over multiple drives not for data security of deleted files.

Obviously there are better tools than shred for secure deletion, like the secure-delete package, amongst others but as noted the above command will wipe all partitions on a drive (provided a default install regarding journalling and NO RAID arrays in use).

Regards, yeti.

---

### Post by Incarnadine on 2016-10-06
@yetimon_64 Wow, thanks for all the feedback! The HDD I ran Shred on had Windows installed on it (NTFS file system) and was not in any type of RAID. I had the HDD mounted and targeted the drive via the shred command. I ran shred with the following command:

```
sudo shred -v /dev/sda1
```

What I ended up doing is manually deleting the partitions from the HDD and running Shred again on the drive. It sounds like your command will make things easier next time though: ```
sudo shred -fvzn0 /dev/sdx
```

Thanks again! :popcorn:

---

### Post by yetimon_64 on 2016-10-06
> **Incarnadine said:**
> @yetimon_64 Wow, thanks for all the feedback! The HDD I ran Shred on had Windows installed on it (NTFS file system) and was not in any type of RAID. I had the HDD mounted and targeted the drive via the shred command. I ran shred with the following command:

```
sudo shred -v /dev/sda1
```

What I ended up doing is manually deleting the partitions from the HDD and running Shred again on the drive. It sounds like your command will make things easier next time though: ```
sudo shred -fvzn0 /dev/sdx
```

Thanks again! :popcorn:
You're welcome, just a few more notes about your command used are below. :)

That command you used will only wipe the contents of the first partition on the drive as you have specified /dev/sda**1**. It will not touch the boot records or the partition table hence your partitions being left alone in your first post. I don't think it is a good idea to have the drive mounted when running the command on a device file, may possibly cause some unintended consequences, not entirely sure but I would not tend to do that. I always use the command on the device file without it being mounted and it will completely clean out a drive contents. Obviously to shred a single file the partition would need to be mounted but to do a complete partition just writing to the unmounted device file will wipe it totally clean.

Take note if you need to completely wipe all partitions you will need to point the command at /dev/sda (but be particularly aware of the warning I gave in my first post regarding the EFI boot partition contents being wiped with it on newer hardware, do a backup of the HDD EFI partition contents _*if they exist*_). 

I think that is your main problem (pointing it at /dev/sda**1**) not so much the command itself, though the -f, force switch may be of some help. You can fine tune the command I used to be more or less secure depending on how much time you want to dedicate to the job and/or how secure you need the wipe to be. For general maintenance and rebuilding machines I tend to use the iterations switch "-n" set to 0 (zero), which is a very quick complete wipe but relatively insecure. If you need to securely wipe data leaving out the iterations switch will automatically do 3 passes plus if you use the zero switch a 4th zeroing pass as well, which can take up to a day or even two on very large drives (extremely slow). 
Cheers, yeti.

**Edit:** *_I should also note_* if you do fully shred any device like /dev/sd**x** you will need to use a tool like gparted from an install with it added or (if you shred the main installation drive sda) from a live boot dvd/usb to reinstall the partition table. Either an ms-dos or gpt partition table depending on what type of hardware and set up you are running will be needed to be added before you can repartition. It is possible to do from terminal but gparted on the live dvd/usb makes it very easy to do such re-installation of the device partition tables etc.

---

### Post by HermanAB on 2016-10-06
Shred doesn't work with a journaling file system and it doesn't work on a solid state disk either.

Therefore it doesn't work on anything from this century.

---

### Post by yetimon_64 on 2016-10-06
> **HermanAB said:**
> Shred doesn't work with a journaling file system and it doesn't work on a solid state disk either.

According to the man file in data=ordered mode, the default installation type, and data=writeback mode it does. Only IF full journalling is enabled with the data=journal mode turned on will its usefulness be negated. 

AFAIK you're right about the SSD, but I don't see any mention of such from the OP. Something for the OP to note if such hardware is in use.

> **HermanAB said:**
> Therefore it doesn't work on anything from this century.

You're wrong with that assumption, plenty of machines still ship with sata2 drives; even within the last couple of years I have brought a new laptop with only a sata2 drive (not cheap hardware, just not "top of the line" stuff either with only SSDs included) and with no SSD hardware. Plenty of such machines are still sold.

Still hardware/drive type is something to be aware of for the OP and others, but the outright statement that it, shred, "doesn't actually work" is misleading to say the least. Full circumstances should be taken into account before stating such in my opinion, shred still can be a very useful tool under the right hardware/set up circumstances.

---

### Post by HermanAB on 2016-10-06
Better to use 'full disk' encryption, then if you need to 'shred' your data - simply hit yourself upside the head with a brick to forget the password...

---

### Post by yetimon_64 on 2016-10-06
I am not "needing to shred my data" but am using shred to clean the drive off prior to further usage. Having a clean drive before partitioning and installing can also be useful, not just to protect old data that encryption would be better used with. Note I only use ONE pass of zeros, and am not using passes of random data for data security purposes. I also noted in my previous posts to the OP how to alter the command to suit the circumstances the OP may be needing it for (security vs speedier drive cleanup).

After doing heaps of partitioning and setting up and having some error crop up has lead to me on occasions to having to use tools such as testdisk. When running tools like testdisk on a new installation it is nice not to have to dig through the "cruft" it can pull up from previous usage of the drive. 

When you shred a drive and such situations crop up the use of shred can speed up recovery work when using tools such as testdisk. I do such clean up as I often make one or two too many partition tweaks and have on occasion rendered a drive inaccessible needing the use of such recovery techniques. Doing so on a cleaned out drive makes for easier recovery work on new installations that have gone "haywire". 

Cheers, yeti.

---

### Post by Incarnadine on 2016-10-07
> **yetimon_64 said:**
> That command you used will only wipe the contents of the first partition on the drive as you have specified /dev/sda**1**. It will not touch the boot records or the partition table hence your partitions being left alone in your first post.

BINGO! Damn, I feel like an idiot. This was the problem with my command.

Thank you so much for all the input and advice regarding Shred. I didn't think I would get so much immediate help and feedback regarding this problem. Truly helpful!

Thank you everyone :popcorn:

---

### Post by DuckHook on 2016-10-07
> **HermanAB said:**
> Shred doesn't work with a journaling file system and it doesn't work on a solid state disk either.

Therefore it doesn't work on anything from this century.You are correct. *Shred* cannot bypass the journaling in ext3/4, nor the automatic allocation algorithms built into SSDs. However, at least for journaling, I believe that *srm* can. This command is part of the *secure-delete* suite and is designed to bypass journaling while it does its job. The only way I know to overwrite an SSD is using *wipe* or *sfill*. *sfill* is part of the same *secure-delete* suite that contains *srm*, *sfill* and *sswap*.

For general users, be aware that *wipe* and *sfill* may brick your SSD, especially older ones. This is because older SSDs needed a minimal amount of free allocate-able space to swap data blocks around and do their magic. Filling up a SSD completely would turn it into read-only or render it completely unusable. I am told the newer SSDs have more intelligent algorithms that handle full disks more gracefully, but have never had occasion to test this out.

---

### Post by QIII on 2016-10-07
The best way to wipe an SSD is probably hdparm --security-erase, which clears all memory cells.

You end up with a "virgin" SSD.

---

### Post by DuckHook on 2016-10-07
> **QIII said:**
> The best way to wipe an SSD is probably hdparm --security-erase, which clears all memory cells.

You end up with a "virgin" SSD.QIII, you are da' man. Just looked this up and it is sweet, sweet, sweet. I feel stupid, though. Have used hdparm but never bothered to explore all its options.

Finally, a simple way to do a real security erase. From the man page, this should also work with HDDs too. Or am I missing something?

And does the erase do true multiple overwrites, or just a one-time reset to "zero"?

---

