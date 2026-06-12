---
title: "rsync backup tips?"
date: 2019-10-30
forum: General Help
---

### Post by dewdrop_world on 2019-10-30
For years, I have been using rsync to backup my data folders. No problem.

Yesterday, on a new HD, I spent about 6 hours to back up about 60-70% of it.

Today, I plugged in the same HD and ran the script to continue where it left off.

The --delete flag *erased almost everything* from the new backup and is going to waste 6 hours redoing what it did yesterday.

I have never seen rsync do this before. Literally 7-8 years of using rsync and --delete has NEVER done this before. Ever.

How do I make it stop doing that?

```
rsync -a --progress --delete --exclude-from=/blahblah/share/excl1204.txt ~/ /media/blah/blah/2017computer/blahblah/
```

Shouldn't be a problem, right?

Even if I use --delete-after, it still somehow thinks the files are different and is going to recopy them anyway?

hjh

---

### Post by HermanAB on 2019-10-30
Maybe you have a clock problem and all files seem to be out of date?

Anyhoo, the CRC option can prevent that.

---

### Post by dewdrop_world on 2019-10-31
> Maybe you have a clock problem and all files seem to be out of date?

But... the timestamps in the source and target directories should be consistent, no?

There's no network involved, just the laptop's internal HDD and the external USB HDD.

Just now, I plugged in the drive to continue the backup and reading was maxing out at about 4 K/sec. So I said "that's crazy," stopped the backup, ejected the drive, plugged it back in, and suddenly it was up to 400-500 K/sec.

Is it maybe that the drive is just defective? Bc that's messed up. Why would performance be so radically different, just minutes apart?

hjh

---

### Post by TheFu on 2019-10-31
Bad cable?
Failing disk?
Check the SMART data to see if there are either issue.

BTW, USB connections that aren't externally powered for spinning disks can be really slow due to lack of power.
If flash storage is involved, it does get really slow before failing.

---

### Post by dewdrop_world on 2019-11-02
> Check the SMART data to see if there are either issue.

Gnome disk utility couldn't access the SMART data.

So...

```
$ smartctl -H /dev/sdb
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-66-lowlatency] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

/dev/sdb: Unknown USB bridge [0x0480:0x0820 (0x315)]
Please specify device type with the -d option.
```

It's not clear to me where I should look to find the device type.

The drive is a Toshiba Canvio Advance. I didn't reformat it for ext4 because I need to use the drive with non-Linux systems as well. I accept that this might make it slower, but I do need the portability.

> BTW, USB connections that aren't externally powered for spinning disks can be really slow due to lack of power.

It is indeed a USB-powered spinning disk. I had read that, for non-sequential writes, 1 MB/sec is about what I can expect. Usually I'm getting that, except that one time a couple of days ago when it seemed to be freaking out about something.

I had hoped for better speed with USB3, but if that's normal, then I can accept it, as long as it's consistent. When it isn't consistent, then I get nervous.

Thanks,
hjh

---

### Post by The Cog on 2019-11-02
Are you using NTFS?
I think I read somewhere that NTFS only has a time resolution of 2 seconds. Man rsync only mentions FAT though, so I could be remembering wrong. From man rsync:
>        -@, --modify-window
              When  comparing  two timestamps, rsync treats the timestamps as being equal if they differ by no more than the modify-window value.  The default is 0,
              which matches just integer seconds.  If you specify a negative value (and the receiver is at least version 3.1.3) then nanoseconds will also be  taken
              into account.  Specifying 1 is useful for copies to/from MS Windows FAT filesystems, because FAT represents times with a 2-second resolution (allowing
              times to differ from the original by up to 1 second).

              If you want all your transfers to default to comparing nanoseconds, you can create a ~/.popt file and put these lines in it:

              rsync alias -a -a@-1
              rsync alias -t -t@-1

              With that as the default, you&#8217;d need to specify --modify-window=0 (aka -@0) to override it and ignore nanoseconds, e.g. if you&#8217;re copying between ext3
              and ext4, or if the receiving rsync is older than 3.1.3.


---

### Post by dewdrop_world on 2019-11-02
> Are you using NTFS? I think I read somewhere that NTFS only has a time resolution of 2  seconds. Man rsync only mentions FAT though, so I could be remembering  wrong. From man rsync:

That's good to know. I never had a problem with it before because typically I would run a backup as the last thing in a session, and then go do other things for a while, and then come back some hours later and do things that would modify files. So any changed files' timestamps would differ between the local HD and the backup by several hours/days.

But the specific case I mentioned was backup disk A (source) and backup disk B (target), where neither of the timestamps should have changed.

It turns out that rsync might simply not have completed successfully the first time. That first day when I was running rsync for about 6 hours, it got quite far into the directory structure. But when I ran it again (and it was doing work I thought it had done before), in the same amount of time it didn't get nearly as far through the directories. So I think somehow rsync, the first time, just skipped over a lot of it.

hjh

---

### Post by TheFu on 2019-11-02
I use rsync to clone media files to backup storage - 12+TB worth - a few times a week.  
The backup storage is USB3 connected.  The source storage is SATA connected.
All the storage is EXT4 with LVM to manage it.

Let me run and time that clone now, it has been a few days since the last time.  There are 3 commands that basically look like this:
```
ionice rsync -av --stats --progress $EXCLUDES --delete /D/ /misc/b-D3/
```
The USB3 mounts are handled via autofs. There were a little over 12GB of updates this time and 150K total files compared.

```
real    3m9.543s
user    0m48.392s
sys     0m15.360s
```
A little over 3 minutes clock time.

File size seems to matter for the transfer speeds.  174.60MB/s  was the highest for one file. Most were in the 65MB/s area. Thousands of tiny files really drop the throughput due to the rsync protocol overhead.

The system is a dual core Pentium G3258, so not high-powered at all. No SSDs in the setup at all.
My main point is that good performance is determined by the file system, disks, connection method, mount options, and rsync.  Avoid FAT-whatever and if you use NTFS, it will always be a little slower, but there are some mount options which can help by about 30%.

Please check the SMART data. A failing disk isn't going to get any better. You need to figure out the correct device type to be used. Look at the storage controller, not the HDD.

---

### Post by dewdrop_world on 2019-11-03
> You need to figure out the correct device type to be used. Look at the storage controller, not the HDD.

Thanks.

Assume I'm an idiot here. I'm not an idiot about other things, but about this, I am. I'm really not sure where to look for this.

hjh

---

### Post by TheFu on 2019-11-03
There is a table on the internet (a little googling should find it) which lists storage controllers and the device type that is compatible.
Mine happened to use SAT, so
```
sudo smartctl -d sat --test=long   /dev/sdf
```
But you should find the table, with the disk controller your HDD uses.

The smartclt manpage has a section on device types. I suppose you could try them all, but some require specific port number to be entered.  Only you can figure this stuff out.

And there are some storage controllers that don't support SMART, so either using a different controller or a different computer is needed. Again, only you will be able to figure it out.

---

### Post by The Cog on 2019-11-04
> So any changed files' timestamps would differ between the local HD and the backup by several hours/days.
I had always assumed that the timestamp comparison was significant when asking rsync to preserve timestamps - it can't preserve them accurately when the destination filesystem is only accurate to 2 seconds. In which case, the next rsync run will see differences (up to 2 seconds I guess, but that might be +/- 1 Sec. That could leave your backup files looking slightly older than the next backup run.

---

