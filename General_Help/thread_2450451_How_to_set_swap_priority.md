---
title: "How to set swap priority?"
date: 2020-09-14
forum: General Help
---

### Post by cedric9 on 2020-09-14
I have two aging 500 GB *Seagate BarraCuda* hard drives installed in my desktop PC.  My two hard rive configuration is a holdover from the days when I used to run both Windows and Kubuntu, but now I’m only running Kubuntu.  (I’m a real noob, so I probably don’t have some of the terminology right.)

 
 
 Kubuntu is installed into partition sda1 on the first drive.  I also have a Linux swap partition and a logical NTFS partition occupying the rest of my sda hard drive.   

 
 
 My second hard drive, sdb, is similarly partitioned, but my primary partition no this drive is a NTFS partition (where Windows 8 used to live) followed by another Linux swap partition, and then another logical NTFS partition for storing documents and backups.  (I’ve been using  *Hiren's* Boot CD *PE to do occasional defragging and scans of my NTFS partitions, and so far that has been working out well.)*

 
 
 *My problem is that, GS Smart Control states that my first hard drive (sda) now has over 11,000 hours of head flying time on it, and that this drive has errors and pre-failure listed under its attributes.  However, my other hard drive (sdb) has only around 6,000 hours on it, and GS Smart Control does not report any errors for my sdb drive.  * 

 
 
 *So, I would like to give the swap partition residing on sdb a higher priory, so that the older sda drive won’t have to work so hard?  I’ve tried to poke around on this myself, but can’t seem to figure it out.  * 

 
 
 *Below is the area of my fstab file describing my swap partitions:*
 *=======================================================================*
 *# swap was on /dev/sdb6 after installation*
 *UUID=c1ffc854-681b-4433-adfd-6e15a374b8e7 none            swap    sw              0       0*
 *# swap was on /dev/sda9 during installation*
 *UUID=039b776e-a845-4763-9eab-42276bfc8dc0 none            swap    sw              0       0*
 *========================================================================*
 Below is an example of what is listed when I enter the “swapon -s” command:
 
 
 Cedric@home-System-ku-2004:~$ swapon -s
 Filename                                Type            Size    Used    Priority
 /dev/sdb5                              partition       4190204 0       -2
 /dev/sda5                              partition       4202492 0       -3
 =========================================================================
 
 
 I plan on changing out both of my aging *BarraCuda drives within the next few months, and I’m hoping to use this as a stop gap measure **until** then.  * 

 
 
 Below are my system specs:


 Operating System: Kubuntu 20.04
 KDE Plasma Version: 5.18.5
 KDE Frameworks Version: 5.68.0
 Qt Version: 5.12.8
 Kernel Version: 5.4.0-47-generic
 OS Type: 64-bit
 Processors: 4 × Intel® Pentium® Gold G5400 CPU @ 3.70GHz
 Memory: 7.6 GiB of RAM
 Hard Drives:  Two 500 GB Seagate Barracuda  
 
 
 
 
 Any info greatly appreciated.

---

### Post by Bashing-om on 2020-09-14
cedric9; Hello -

One does not need 2 swap partitions - linux will happily mount and use whatever swap it is directed to.
Were me I would change the UUID in sda to point to the swap partition on sdb :
```

sudo fdisk -lu
sudo blkid

```
to know for sure the UUID to write into the sda /etc/fstab file.

[INDENT]just my two cents worth
[/INDENT]

---

### Post by mastablasta on 2020-09-14
you can also reduce swappiness if you don't use hibernation much.
 
SWAP: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

how to reduce swapiness: [https://askubuntu.com/questions/103915/how-do-i-configure-swappiness](https://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

also i suggets you change drive sooner than later. i suggest you use clonezilla disk to disk option to create bit-by-bit copy of your disk, then you can stretch it (since 1 or 2 Tb drives are not that expensive now) or add a partition to it. 
here is a step by step guide you might want to have open on another screen or printed when you do it: [https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

i succesfully moved 500 MB failing windows disk to 1 TB new HDD. i haven't decided to stretch the partition because i wanted to put linux on the second half. in the end i just bought a new disk for linux.

---

### Post by HermanAB on 2020-09-14
Everything about swap is in the *swapon* man page (it is well worth a read):
$ man swapon

---

### Post by Impavidus on 2020-09-14
Do you need all that swap space? If not, you could simply disable one of the swap partitions (comment the line out in your /etc/fstab). Do you use that swap often? If swap is never used, it won't affect hard drive life. Since I increased my ram to 8GB, I've never seen swap in use on my Xubuntu system. With 8GB of memory, swap is mostly for emergency use.

---

### Post by cedric9 on 2020-09-14
> **Bashing-om said:**
> cedric9; Hello -

I would change the UUID in sda to point to the swap partition on sdb :



That is also an interesting idea. Or since I already have lines in my fstab file referencing both swap areas, can I just add a # symbol to the beginning of the line referencing the swap on sda, thus disabling the swap on sda?

---

### Post by cedric9 on 2020-09-14
> **mastablasta said:**
> you can also reduce swappiness if you don't use hibernation much.
 
i suggest you use clonezilla disk to disk option to create bit-by-bit copy of your disk, then you can stretch it (since 1 or 2 Tb drives are not that expensive now) or add a partition to it. here is a step by step guide you might want to have open on another screen or printed when you do it: [https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)



I've successfully used clonezilla many times in the past, but when I recently tried to use it to copy my Kubuntu installation to a different drive, the drive that was being copied to wasn't bootable after the copying process.  I admit that it was probably something I did that wasn't right, but rather than figure it out, I used Macrium Reflect which seemed to copy everything, and resulted in a bootable drive when I was finished.  Yeah I know I that I need to replace both of these drives in the near future, but unfortunately I live in area that doesn't have any computer stores near by, and it often takes several months for things to get shipped here.  But that is another story.

---

### Post by cedric9 on 2020-09-14
> **Impavidus said:**
> Do you need all that swap space? If not, you could simply disable one of the swap partitions (comment the line out in your /etc/fstab). Do you use that swap often? If swap is never used, it won't affect hard drive life. Since I increased my ram to 8GB, I've never seen swap in use on my Xubuntu system. With 8GB of memory, swap is mostly for emergency use.

I honestly couldn't tell you if the swap space is being used very often or not.  I just assumed that it would work similar to the swap file used in a Windows system, but I guess that is not the case.  I guess that I could just put a # symbol at the start of the line referencing the swap on sda, and that would do the trick?

---

### Post by mastablasta on 2020-09-14
bit by bit copy will make them bootable as they are both exactly the same. imaging is another matter. although i have to admit i haven't tried it yet on UEFI boot. otherwise it might be easier fresh install, then copy the data from /home. sometimes that is just faster & easier.

> **cedric9 said:**
> Yeah I know I that I need to replace both of these drives in the near future, but unfortunately I live in area that doesn't have any computer stores near by, and it often takes several months for things to get shipped here.  But that is another story.

sometimes living in a more remote area is a plus. for example during virus pandemic. :)

---

### Post by cedric9 on 2020-09-15
I went into my fstab filed and added a # to the line referencing the UUID number for the swap area on sda.  I like this option, because in the future, after  I clone my old 500 GB BarraCuda to a new hard drive, then I can go back in and remove the # to make it work again.  But still, I was wondering if it is possible to manage the swap priority by adding additional statements to the lines in fstab referencing the swap areas.  Also, don't see how to mark this thread solved anywhere up above?

---

### Post by HermanAB on 2020-09-15
For the terminally lazy...

$ man swapon

swapon(8) &#8212; Linux manual page

NAME | SYNOPSIS | DESCRIPTION | OPTIONS | EXIT STATUS | ENVIRONMENT | FILES | NOTES | HISTORY | SEE ALSO | AVAILABILITY | COLOPHON
  
SWAPON(8)                   System Administration                  SWAPON(8)
NAME         top

       swapon,  swapoff  -  enable/disable  devices and files for paging and
       swapping
SYNOPSIS         top

       swapon [options] [specialfile...]
       swapoff [-va] [specialfile...]
DESCRIPTION         top

       swapon is used to specify devices on which paging and swapping are to
       take place.

       The device or file used is given by the specialfile parameter.  It
       may be of the form -L label or -U uuid to indicate a device by label
       or uuid.

       Calls to swapon normally occur in the system boot scripts making all
       swap devices available, so that the paging and swapping activity is
       interleaved across several devices and files.

       swapoff disables swapping on the specified devices and files.  When
       the -a flag is given, swapping is disabled on all known swap devices
       and files (as found in /proc/swaps or /etc/fstab).
OPTIONS         top

       -a, --all
              All devices marked as ``swap'' in /etc/fstab are made
              available, except for those with the ``noauto'' option.
              Devices that are already being used as swap are silently
              skipped.

       -d, --discard[=policy]
              Enable swap discards, if the swap backing device supports the
              discard or trim operation.  This may improve performance on
              some Solid State Devices, but often it does not.  The option
              allows one to select between two available swap discard
              policies: --discard=once to perform a single-time discard
              operation for the whole swap area at swapon; or
              --discard=pages to asynchronously discard freed swap pages
              before they are available for reuse.  If no policy is
              selected, the default behavior is to enable both discard
              types.  The /etc/fstab mount options discard, discard=once, or
              discard=pages may also be used to enable discard flags.

       -e, --ifexists
              Silently skip devices that do not exist.  The /etc/fstab mount
              option nofail may also be used to skip non-existing device.

       -f, --fixpgsz
              Reinitialize (exec mkswap) the swap space if its page size
              does not match that of the current running kernel.  mkswap(8)
              initializes the whole device and does not check for bad
              blocks.

       -h, --help
              Display help text and exit.

       -L label
              Use the partition that has the specified label.  (For this,
              access to /proc/partitions is needed.)

       -o, --options opts
              Specify swap options by an fstab-compatible comma-separated
              string.  For example:

                     swapon -o pri=1,discard=pages,nofail /dev/sda2

              The opts string is evaluated last and overrides all other
              command line options.

       -p, --priority priority
              Specify the priority of the swap device.  priority is a value
              between -1 and 32767.  Higher numbers indicate higher
              priority.  See swapon(2) for a full description of swap
              priorities.  Add pri=value to the option field of /etc/fstab
              for use with swapon -a.  When no priority is defined, it
              defaults to -1.

       -s, --summary
              Display swap usage summary by device.  Equivalent to "cat
              /proc/swaps".  This output format is DEPRECATED in favour of
              --show that provides better control on output data.

       --show[=column...]
              Display a definable table of swap areas.  See the --help
              output for a list of available columns.

       --output-all
              Output all available columns.

       --noheadings
              Do not print headings when displaying --show output.

       --raw  Display --show output without aligning table columns.

       --bytes
              Display swap size in bytes in --show output instead of in
              user-friendly units.

       -U uuid
              Use the partition that has the specified uuid.

       -v, --verbose
              Be verbose.

       -V, --version
              Display version information and exit.
EXIT STATUS         top

       swapoff has the following exit status values since v2.36:

       0      success

       2      system has insufficient memory to stop swapping (OOM)

       4      swapoff syscall failed for another reason

       8      non-swapoff syscall system error (out of memory, ...)

       16     usage or syntax error

       32     all swapoff failed on --all

       64     some swapoff succeeded on --all

              The command swapoff --all returns 0 (all succeeded), 32 (all
              failed), or 64 (some failed, some succeeded).

              The old versions before v2.36 has no documented exit status, 0
              means success in all versions.
ENVIRONMENT         top

       LIBMOUNT_DEBUG=all
              enables libmount debug output.

       LIBBLKID_DEBUG=all
              enables libblkid debug output.
FILES         top

       /dev/sd??  standard paging devices
       /etc/fstab ascii filesystem description table
NOTES         top

   Files with holes
       The swap file implementation in the kernel expects to be able to
       write to the file directly, without the assistance of the filesystem.
       This is a problem on files with holes or on copy-on-write files on
       filesystems like Btrfs.

       Commands like cp(1) or truncate(1) create files with holes.  These
       files will be rejected by swapon.

       Preallocated files created by fallocate(1) may be interpreted as
       files with holes too depending of the filesystem.  Preallocated swap
       files are supported on XFS since Linux 4.18.

       The most portable solution to create a swap file is to use dd(1) and
       /dev/zero.

   Btrfs
       Swap files on Btrfs are supported since Linux 5.0 on files with nocow
       attribute.  See the btrfs(5) manual page for more details.

   NFS
       Swap over NFS may not work.

   Suspend
       swapon automatically detects and rewrites a swap space signature with
       old software suspend data (e.g., S1SUSPEND, S2SUSPEND, ...). The
       problem is that if we don't do it, then we get data corruption the
       next time an attempt at unsuspending is made.
HISTORY         top

       The swapon command appeared in 4.0BSD.
SEE ALSO         top

       swapoff(2), swapon(2), fstab(5), init(8), fallocate(1), mkswap(8),
       mount(8), rc(8)
AVAILABILITY         top

       The swapon command is part of the util-linux package and is available
       from [https://www.kernel.org/pub/linux/utils/util-linux/](https://www.kernel.org/pub/linux/utils/util-linux/).
COLOPHON         top

       This page is part of the util-linux (a random collection of Linux
       utilities) project.  Information about the project can be found at 
       &#10216;[https://www.kernel.org/pub/linux/utils/util-linux/&#10217;](https://www.kernel.org/pub/linux/utils/util-linux/&#10217;).  If you have a
       bug report for this manual page, send it to
       [email]util-linux@vger.kernel.org[/email].  This page was obtained from the
       project's upstream Git repository
       &#10216;git://git.kernel.org/pub/scm/utils/util-linux/util-linux.git&#10217; on
       2020-08-13.  (At that time, the date of the most recent commit that
       was found in the repository was 2020-08-12.)  If you discover any
       rendering problems in this HTML version of the page, or you believe
       there is a better or more up-to-date source for the page, or you have
       corrections or improvements to the information in this COLOPHON
       (which is not part of the original manual page), send a mail to
       [email]man-pages@man7.org[/email]

util-linux                      October 2014                       SWAPON(8)
Pages that refer to this page: swapoff(2),  swapon(2),  fstab(5),  org.freedesktop.systemd1(5),  proc(5),  procfs(5),  systemd.swap(5),  mkswap(8),  mount(8),  swaplabel(8)

---

### Post by cedric9 on 2020-10-03
> **mastablasta said:**
> 
  
.......here is a step by step guide you might want to have open on another screen or printed when you do it: [https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)



I think that I figured out something about clonezilla, at least as in regards to my system.  If I boot clonezilla from a DVD it doesn't seem to work, but if I boot if from a USB thumb drive, then it seems to work perfectly, and then I end up with a bootable copy at the end of the process.  Could it have something to do with secure boot settings in my bios?

---

### Post by GhX6GZMB on 2020-10-04
> **cedric9 said:**
> I think that I figured out something about clonezilla, at least as in regards to my system.  If I boot clonezilla from a DVD it doesn't seem to work, but if I boot if from a USB thumb drive, then it seems to work perfectly, and then I end up with a bootable copy at the end of the process.  Could it have something to do with secure boot settings in my bios?

More likely your boot sequence in the BIOS/UEFI. DVD and USB need to be top of the list. After that your hard drives.

---

