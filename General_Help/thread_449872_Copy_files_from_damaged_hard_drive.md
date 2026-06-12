---
title: "Copy files from damaged hard drive"
date: 2007-05-20
forum: General Help
---

### Post by Dave54 on 2007-05-20
I have a small (10 Gig!) hard drive that got damaged and corrupted. It used to run windows.

Windows would no longer boot, so I tried many kinds of boot cd's (clone software, ubuntu live CD, etc.) and tried to copy the files to another hard drive. However, this always failed. It seems about one in 20 files are corrupt. When anything tries to read them, they freeze, sometimes reporting errors (bad sector, cyclic redundancy check failed, etc.)

Normally it is a **very** bad idea to connect a hard drive with information that you want on it to another motherboard, but faced with no alternative, I put it in as a slave in my computer running ubuntu. Surprisingly, ubuntu can see and read the files just fine. However, If i try to copy the files from that hard drive onto the ubuntu hard drive, it freezes. I tried using terminal, but it too froze after reaching a corrupted file. (here's the command I used)
```
cp -rv /media/C/Documents\ and\ Settings/Dave/Desktop/ /home/dave/Desktop/old\ comp/
```

So, here is my question. Is there a linux program that can copy files from a corrupt hard drive (and ignore the errors/corruption/problems)? Is there a way to have ubuntu copy the files and skip the corrupt files?

Any ideas are welcome
-Dave

---

### Post by aldenhg on 2007-05-20
This may sound crazy, but try taking the hard drive out, sealing it in a plastic bag and then putting it in the freezer overnight. Take it out and immediately put it back in the computer and commence the copying as you were trying. I've been able to get info off of a few bad drives like that, but if there's a lof of stuff to copy it might warm up as it's going and fail again. In which case toss it back in the freezer and try again.

---

### Post by mdurham on 2007-05-21
I found that putting the bad drive in an external usb was the best for recovering data.
Good luck anyway.

---

### Post by anaconda on 2007-05-21
I would try dd_rescue before putting it to a freezer??!? (sounds dangerous)

[http://www.tivocommunity.com/tivo-vb/showthread.php?t=190306](http://www.tivocommunity.com/tivo-vb/showthread.php?t=190306)
[http://www.garloff.de/kurt/linux/ddrescue/](http://www.garloff.de/kurt/linux/ddrescue/)

ddrescue might be even better..
[http://www.forensicswiki.org/wiki/Ddrescue](http://www.forensicswiki.org/wiki/Ddrescue)
oh and it is available in the ubuntu repositories..

---

### Post by aldenhg on 2007-05-21
Don't worry about the freezer. Cold doesn't hurt had drives. In fact, they rather like it. Well, freezer cold is OK, but something like liquid nitrogen might be overkill. After a bit of reading, it sounds like ddrescue is the way to go. Go ahead and try it pre-freezer and if it doesn't work chill the sucker and try again.

---

### Post by Dave54 on 2007-05-23
Thanks for the replies.

The main worry I have about the freezer is condensation. Also, most people say it works for a "clicking" hard drive, but mine makes no strange sounds. So, I'll try ddrescue before the freezer.

However, I can't figure out how to use ddrescue. When the command is run, does it ask a few questions or just start copying? (I don't want to run it until I get the answer to that question ;) ) How to I tell it where to copy from and to? does it copy by file, partition, sector, or a whole image? Should I take out my ubuntu hard drive, put in the corrupted 10 Gig hard drive and another larger blank hard drive, boot from the live CD, and run the command off that?

I'm just not sure how to go about using ddrescue.

-Dave

---

### Post by Dave54 on 2007-05-26
I need help!

```
dave@ubuntu:~$ ddrescue
ddrescue: both input and output must be specified
Try `ddrescue --help' for more information.
dave@ubuntu:~$ ddrescue --help
GNU ddrescue - Data recovery tool.
Copies data from one file or block device to another,
trying hard to rescue data in case of read errors.

Usage: ddrescue [options] infile outfile [logfile]
Options:
  -h, --help                   display this help and exit
  -V, --version                output version information and exit
  -b, --block-size=<bytes>     hardware block size of input device [512]
  -B, --binary-prefixes        show binary multipliers in numbers [default SI]
  -c, --cluster-size=<blocks>  hardware blocks to copy at a time [128]
  -C, --complete-only          do not read new data beyond logfile limits
  -e, --max-errors=<n>         maximum number of error areas allowed
  -i, --input-position=<pos>   starting position in input file [0]
  -n, --no-split               do not try to split error areas
  -o, --output-position=<pos>  starting position in output file [ipos]
  -q, --quiet                  quiet operation
  -r, --max-retries=<n>        exit after given retries (-1=infinity) [0]
  -s, --max-size=<bytes>       maximum size of data to be copied
  -t, --truncate               truncate output file
  -v, --verbose                verbose operation
Numbers may be followed by a multiplier: b = blocks, k = kB = 10^3 = 1000,
Ki = KiB = 2^10 = 1024, M = 10^6, Mi = 2^20, G = 10^9, Gi = 2^30, etc...

Report bugs to bug-ddrescue@gnu.org
dave@ubuntu:~$ 
```

I want to copy all the files from the slave hard drive to /home/dave/Desktop/old comp2. How do I do this???

---

### Post by ruy_lopez on 2007-05-26
I'd try to use dd directly on the block device. Hook up the drive (but don't mount it), and run "fdisk -l", to see which device its been assigned. Then run this:
```

sudo dd if=/dev/device of=old_drive_backup.dd
```

If you can successfully create a dd file of the entire drive, you can use sleuthkit & autopsy to recover the files:

[http://www.sleuthkit.org/sleuthkit/desc.php](http://www.sleuthkit.org/sleuthkit/desc.php)

From memory, I think ddrescure does the same as dd, but instead of exiting on errors, it writes zeros to the .dd file, in the regions where there was corrupt data.

for ddrescue I think the command would be

```
sudo ddrescue /dev/corrupt_drive backup.dd
```

---

### Post by Dave54 on 2007-05-26
Well, just after my last post, I decided to go with the three hard drive approach. My main hard drive is 250Gig, the corrupted one is 10Gig, and I had a blank 60Gig hanging around. I put all three into my computer and booted up on the 250G.

I didn't know what format ddrescue wanted the 60G in, so I made it half ext3 and half unpartitioned. I then ran "fdisk -l" and found the 10G was named sdb and the 60G was named sdc. Then I ran the command
```
sudo ddrescue /dev/sdb /dev/sdc /home/dave/Desktop/rescue.log
```
The first 9Gig went by in about 10 minutes with no errors. However, that last gig's another story. It has been six hours and it's about half way through, with 473 errors and counting.

Before when I was using windows, the error would tend to be something like "cyclic redundancy check failed." I guess this hard drive error is very hard to ignore.

After this, if I can figure out how to make it only retry the bad sectors, I'm putting it in the freezer and trying again.

PS. Does anyone know whether it's writing to the ext3 partition or the unpartitioned space?

---

### Post by Dave54 on 2007-05-28
It found 2500+ errors.

It took many many many hours, but it finished copying. It went on to split the bad sectors and reverse copy and other things like that, but since only 50MB were missing, I decided to stop it there and leave it at that.

So, I took a look at the 60Gig I copied to and it was all unpartitioned except for the 10Gig ntfs partition it copied over. So it didn't matter what was on the 60Gig, ddrescue deleted it anyway.

So, I went to "Computer" and mounted the 60Gig, and copied all the files to my main 250Gig by "Click and Drag". For some reason it only copied about a fourth of the files. So, I ran this:
```
cp -rv /media/C/ /home/dave/Desktop/old/
```
And that copied everything perfectly!

I have my lost data back! :D

---

### Post by mhuegel on 2008-07-24
I had a similar problem, so here is the story of how I solved it. 

I finally found a good and successful way to recover data on a broken Windows PC's hard disk. There are a few tools under Linux out there that are helpful (given in chronological order).

1) dd (quite old)
2) dd_rescue (an improvement of dd, available as 'ddrescue' in the Adept Manager)
3) dd_rhelp (a script that improves dd_rescue)
4) ddrescue (not related to dd_rescue, completely written anew, and supposedly the fastest and safest program for this purpose. Available as 'gddrescue' in the Adept Manager)

I tried ddrescue ('sudo ddrescue /dev/hda /dev/sda') on the Windows PC with a Kubuntu live CD and an external hard drive. After a few hours it had recovered the data. It went on to split the error parts and tried some fancy things, but these steps are very time-consuming and in most cases are not needed.

So I canceled ddrescue at this point, took out the external hard drive, plugged it into a (working) PC with Windows installed, and ran 'chkdsk E: /r'. After that, most of the data was there again!

What is important is that ddrescue completely overwrites what is on the external hard drive. It essentially copies the whole partition from /dev/hda and puts it into a newly created partition on /dev/sda.

There is also the option to use a log file with ddrescue ('sudo ddrescue /dev/hda /dev/sda /var/ddrescue.log'). If you cancel ddrescue and have used this logfile option, you can resume ddrescue at a later point in time without losing the progress already made.

The extra step with chkdsk under Windows is necessary since fsck (under Linux) cannot deal with NTFS at this point in time. There is, however, an extension planned. This extension is ntfsck (also known as fsck.ntfs) and will be a part of the ntfsprogs package. 

After successfully recovering the data, you probably want to install a new Windows system on your previously broken PC. In that case, you should definitely run 'chkdsk C: /r' after finishing the Windows installation. There might still be some problematic parts on your hard drive: You want to make sure that you will not have the same problems a few days later AGAIN! 

Actually, one would expect Windows to do this step upon installation automatically. However, this seems not to be the case. When I ran 'chkdsk C: /r' it still found and corrected some hard disk errors, even though I was doing this on a PC with a new Windows installation. 

Here are a few links that I found to be useful: 
[Recovery Example]("http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html")
[ddrescue on FreshMeat]("http://freshmeat.net/projects/addrescue/")
[ddrescue on GNU]("http://www.gnu.org/software/ddrescue/ddrescue.html")
[Interview with Antionio Diaz]("http://blue-gnu.biz/content/interview_gnu_ddrescue_039_s_antonio_diaz_diaz")
[Comparison of Tools No. 1]("http://www.toad.com/gnu/sysadmin/index.html#ddrescue")
[Comparison of Tools No. 2]("http://blogs.sun.com/superpat/tags/ddrescue")
[Sleuth Kit]("http://www.sleuthkit.org/sleuthkit/desc.php")

---

