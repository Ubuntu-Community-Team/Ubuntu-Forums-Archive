---
title: "mdadm experts - advanced recovery thoughts"
date: 2013-01-02
forum: General Help
---

### Post by shushry on 2013-01-02
Working on a bit of a recovery effort with an mdadm array.   Here's the background:

8 x 1.5TB disk raid 5, created with mdadm, housing an XFS filesystem (default chunk, etc).

Array has run fine for quite some time.   Occassionally, usually under heavy load, or an aging disk, the array will kick out a disk (bad block, or some other i/o error).  Not a problem, you can simply remove the disk, re-add it (or replace it) and rsync happiness.

Once in a while, usually under some heavy I/O operation, TWO disks will get kicked out.  This might otherwise be a problem, but a trick i've used (and is often cited online) is that you can simply RE-create the array with the same parameters and disk order on top of the existing array without data loss.   Usually, it's best to use the "missing" keyword on one of your disks in the create statement, so that the array is created but NOT DOES NOT START SYNCING, so that you can verify all is well with your filesystem...then add your last disk, and again, rsync happiness.

Recently I ran into the above scenario, but complicated things greatly.   I rebooted the server before recreating the array, just to give things a clear start, and didn't realize that my Ubuntu system (12) often makes block device assignments in a DIFFERENT order, depending on what controller is seen first, etc.  So /dev/sda in one boot, might show up as /dev/sde in another.   Again, shouldn't be a problem, since ever disk has mdadm metadata identifying the order, and raid details, UUID, etc.   However, in this case, not thinking my drives were out of order, I RECREATED the array with my last known order - which wasn't right after the boot.   Essentially creating a NEW set of metadata on every drive, with an array out of order.     No sync's happened (used the missing drive method above), so data "should" be intact - I just need to figure out which drive was which from the original create!

I have SOME log information (hdparm outout, /proc/mdstat output, etc) from the original array, but thus far haven't succeeded in guessing the original order.

A note to self - a good bit of data to obtain from your healthy, in-sync array, is to create a simple mapping of the constituent block devices to their corresponding drive serial number - that way you can always go back and know physically which drive was which at the time of happiness.

Anyhoo, I don't have that, so I've thought of maybe scripting a process to literally try every drive combination order (again, with one drive missing so no sync's occur) checking for a valid filesystem with each iteration.   Hip calculations put this process as taking 3-4 days to complete (9 actual disks, but only 8 in use ~ 141k permutations) - which I'm fine with, but would there be any dangers to this?

As a second question - is there something smarter I'm missing?  IS there a way to somehow examine the disks, aside from the raid metadata (which had since been overwritten), that might give a clue as to their order?

Thanks all in advance...

---

### Post by TheFu on 2013-01-02
Perhaps using UUID-based mdadm.conf would be a good idea?
Or 
Using the by-path-based disk pointers as seen here: /dev/disk/by-path
I think by-path is recommended for enterprise setups.

I have no clue for your recovery problem.  At this point, I'd recreate it from scratch and restore from backups. THAT would be faster, right?

---

### Post by shushry on 2013-01-02
> **TheFu said:**
> Perhaps using UUID-based mdadm.conf would be a good idea?
Or 
Using the by-path-based disk pointers as seen here: /dev/disk/by-path
I think by-path is recommended for enterprise setups.

I have no clue for your recovery problem.  At this point, I'd recreate it from scratch and restore from backups. THAT would be faster, right?

The entire backup is offsite, and would take WEEKS to restore based on my bandwidth, etc.   Not that it isn't an option, but I'd love to try to solve this first before resorting to that.

---

### Post by TheFu on 2013-01-03
> **shushry said:**
> The entire backup is offsite, and would take WEEKS to restore based on my bandwidth, etc.   Not that it isn't an option, but I'd love to try to solve this first before resorting to that.

Wow. Seems you have a major backup solution issue too. :(
Can't you have that service ship you a few HDDs with your data FedEx?  If the data isn't worth $1500 for that service, perhaps all the RAID isn't needed?  That is what I'd ask the boss/money man.

---

### Post by SaturnusDJ on 2013-01-04
> **shushry said:**
> 
A note to self - a good bit of data to obtain from your healthy, in-sync array, is to create a simple mapping of the constituent block devices to their corresponding drive serial number - that way you can always go back and know physically which drive was which at the time of happiness.

I think this will do:
Save the "mdadm --detail /dev/md" output.
Then add to the output the corresponding UUIDs.

Knowing more is always better so if you're able to add serial numbers, do so.

[SIZE="3"]**EDIT: the above does not work! Here is the fix:**[/SIZE]
Of course all disk have the same UUID in an array. Therefor we need unique information:
#1. Save "mdadm --detail /dev/md" output.
#2. Save "ls -al" in "/dev/disk/by-id" ouput.
#3. Compare and get the right order of serial numbers.
#4. When rebooted run the command from #2 again.
#5. Now the right order of disks is based on the serial numbers saved previously.

> **shushry said:**
> Usually, it's best to use the "missing" keyword on one of your disks in the create statement, so that the array is created but NOT DOES NOT START SYNCING, so that you can verify all is well with your filesystem...then add your last disk, and again, rsync happiness.
Good thinking. Did you use --assume-clean and --force?

> **shushry said:**
> 
Anyhoo, I don't have that, so I've thought of maybe scripting a process to literally try every drive combination order (again, with one drive missing so no sync's occur) checking for a valid filesystem with each iteration.   Hip calculations put this process as taking 3-4 days to complete (9 actual disks, but only 8 in use ~ 141k permutations) - which I'm fine with, but would there be any dangers to this?

As a second question - is there something smarter I'm missing?  IS there a way to somehow examine the disks, aside from the raid metadata (which had since been overwritten), that might give a clue as to their order?

Thanks all in advance...
Before reading your solution, I thought of the same. As far as I know the superblock is already lost due to replacement. ([https://raid.wiki.kernel.org/index.php/RAID_superblock_formats](https://raid.wiki.kernel.org/index.php/RAID_superblock_formats))

In mdadm terms it isn't dangerous ([http://arstechnica.com/civis/viewtopic.php?f=16&t=121767](http://arstechnica.com/civis/viewtopic.php?f=16&t=121767)), unless (1) doing a (re)create using another superblock version than the original because they are saved at different locations, as stated in the link above or (2) not telling mdadm about the already existing array.

You can use read-only:
--create ... --readonly / -o ...

---

### Post by SaturnusDJ on 2013-02-17
If you're still having this problem, or someone else reads this: I just came across a script to do all the possible re-creates: [https://raid.wiki.kernel.org/index.php/RAID_Recovery#Recreating_an_array](https://raid.wiki.kernel.org/index.php/RAID_Recovery#Recreating_an_array)

---

