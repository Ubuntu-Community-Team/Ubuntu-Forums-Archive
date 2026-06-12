---
title: "Rsync Compare-dest function"
date: 2019-01-17
forum: General Help
---

### Post by zubbs1 on 2019-01-17
I have three directories:
/media/sharemore/Raid/Shows  (I'll call this A from here on)
/mnt/Backup1                             (I'll call this B from here on)
/mnt/Backup2                             (I'll call this C from here on)

A has more data than can fit on B.  So I copied from A to B until B was full.  Now I want to copy to C what is missing on B that is present on A.  To test my command line, I set up three directories (called first second and third).  I put 14 files in first (numbered 1 through 14).  I put the files with names ending in even numbers in second.  Then I ran the following command:

```
rsync -av --compare-dest=/home/sharemore/Desktop/second/ /home/sharemore/Desktop/first/ /home/sharemore/Desktop/third/
```

This did exactly what I intended, it copied only the odd named files to third.  I changed the path names for my real run with the following command:


```
rsync -avn --log-file=testrun.txt --progress --compare-dest=/mnt/Backup1/Shows /media/sharemore/Raid/Shows/ /mnt/Backup2/Shows
```

When I view the created testrun.txt file, it shows everything from A was copied to C.  Why isn't it sending only the missing files as my test above did?


I appreciate any insight.

Cheers.

---

### Post by TheFu on 2019-01-17
A **du -shc /media/sharemore/Raid/Shows/A-M]*** should show whether it will fit into "B" or not.

```
$ rsync -avz /media/sharemore/Raid/Shows/[A-M]* /mnt/Backup1/
$ rsync -avz /media/sharemore/Raid/Shows/[N-Z,0-9]* /mnt/Backup2/

```

Tweak the last/first letter to size stuff.

I limit LV/partition sizes to be less than the sizes of my available backup storage for this reason.  Maybe setup the RAID with to quota settings?  IDK.

---

### Post by zubbs1 on 2019-01-17
> **TheFu said:**
> A **du -shc /media/sharemore/Raid/Shows/A-M]*** should show whether it will fit into "B" or not.

```
$ rsync -avz /media/sharemore/Raid/Shows/[A-M]* /mnt/Backup1/
$ rsync -avz /media/sharemore/Raid/Shows/[N-Z,0-9]* /mnt/Backup2/

```

Tweak the last/first letter to size stuff.

I limit LV/partition sizes to be less than the sizes of my available backup storage for this reason.  Maybe setup the RAID with to quota settings?  IDK.



This could work. 


As with almost everything Ubuntu, I didn't know I could do this.  Knowing how to direct A-M and N-Z towards each backup drive, would have been the best route to go from the beginning.

Thanks for the further lesson on functions I wasn't aware of.


I'll try this tonight, and update with results.


Cheers.

---

### Post by TheFu on 2019-01-17
rsync behaves in different ways by default when copying local and copying remote.  Some of the default for local copies are bad for large, media, files. For local copies, rsync just recopies the entire file unless told to do differently.  It was believed this was faster almost always than doing the complex comparison math. You can override this behavior.  I don't remember the option. Sorry.  I vaguely remember a check size + timestamp option before copy.

a) rsync is a good tool. I use it for stuff like this too. You've nailed this.
b) happy to see that RAID isn't being considered a backup. It never should be.  Some RAID failures can only be fixed by wiping everything and starting over, using backups.  You've nailed this.
c) Linux is Linux is Unix for stuff like this. You don't need to think "Ubuntu", you should think "Unix."  Besides the GUI (and that only applies if you use Unity or a heavily customized by Canonical Gnome3), Ubuntu isn't different from any other Linux.  At the command line using a tool like rsync - Ubuntu is Linux is Unix. same, same, same.

There is a very approachable, free, PDF book called "The Linux Command Line" [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) which explains much of the things you haven't learned up to now.  We all have gaps in our knowledge, but how to use fileglobbing and regex matching is an important skill.  Unix globbing is very different and much more powerful than Windows.  We can use *some* to find files/directories with "some" in the name anywhere.  Windows treats extensions as something special. Unix doesn't care about extensions. They are only what happens to come after a period and mean NOTHING to the core OS.  Don't get me wrong, extensions are handy for humans, but Unix doesn't care.

And I'll say this 1 more time.  Don't let any primary storage area have more space than the backup area you plan to use has.  I would fix that.   For example, in general, I use 4TB disks for backups. When 8TB became available, cheap, I picked up one.  This new disk was split into (2) 4TB partitions (well, I use LVM, so they are really 4TB logical volumes) so that it would fit my backup method better.
```
/dev/mapper/istar--8TB-istar--back3--a        3.6T  3.4T  208G  95% /misc/b-D3
/dev/mapper/istar--8TB-istar--back3--b        3.5T  3.4T   51G  99% /misc/b-D4
```
I left a little unallocated storage on the 8TB drive so it could be easily added to either the a or b LVs when completely full and give me a week or 2 to get more storage.

Anyway ... rsync ... 
I would simply move the [A-M] in backup2 to backup1 and the [N-Z] in backup1 to backup2.  It isn't like you need to watch the jobs. 

BTW, you might want to use the **tee** command for logging.   $ *rsync ..... | tee /tmp/log.rsync-attempt *  Just saying.

From the rsync manpage:```

       --compare-dest=DIR
              This  option  instructs  rsync  to  use  DIR  on the destination
              machine as an additional hierarchy to compare destination  files
              against  doing transfers (if the files are missing in the desti&#8208;
              nation directory).  If a file is found in DIR that is  identical
              to  the  sender’s  file, the file will NOT be transferred to the
              destination directory.  This is useful  for  creating  a  sparse
              backup  of  just files that have changed from an earlier backup.
              This option is typically used to copy into an  empty  (or  newly
              created) directory.

              Beginning  in version 2.6.4, multiple --compare-dest directories
              may be provided, which will cause rsync to search  the  list  in
              the  order  specified  for  an exact match.  If a match is found
              that differs only in attributes, a local copy is  made  and  the
              attributes  updated.  If a match is not found, a basis file from
              one of the DIRs will be selected to try to speed up  the  trans&#8208;
              fer.

              If  DIR  is  a  relative path, it is relative to the destination
              directory.  See also --copy-dest and --link-dest.

             [B] NOTE: beginning with version 3.1.0, rsync  will  remove  a  file
              from  a  non-empty  destination  hierarchy  if an exact match is
              found in one of the compare-dest  hierarchies [/B] (making  the  end
              result more closely match a fresh copy).

...
```  I have version 3.1.x here on a 16.04 box without doing anything special. That last part can make for some undesirable situations.

---

