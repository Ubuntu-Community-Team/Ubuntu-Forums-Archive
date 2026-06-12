---
title: "1tb ntfs hard drive rescue with ddrescue"
date: 2014-05-01
forum: General Help
---

### Post by sleepingsword on 2014-05-01
Hi,

I recently had some bad luck with my pc, 4 drives failed at approx the same time. 2 x USB backup drives, my system drive and a internal storage drive.

The two USB drives and the system drive just suddenly became RAW, now I think I can fix those fairly easily my problem is the slave storage drive.

it's a 1tb single partition NTFs formatted drive, the smart status on boot is warning that it should be backed up, so that is what I am trying to do....

I tried various things in Windows and it was all junk, it gets to a point and bombs out due to read errors.

I am trying a livecd with gnu ddrescue.

All I want to do is copy the data from the dying drive to a good drive. 

I started it going last week, actually about 8 days ago, its managed about 475gb so far but has slowed to a crawl... its doing a few GB a day so we are looking at months for it to finish.

now I think a made a fairly bad mistake as I didn't enable logging at the time, mainly because I was unaware of it...

The command I used: ddrescue -v /dev/sdb to /dev/sda --force

approx 475gb read, 463gb recovered, 12gb errored.

I know there is approx 930gb of data on the drive.


what I would like to know is how can I get the data off this drive in a reasonable amount of time, a week I can live with but months is ridiculous .



any advice would be very welcome, thanks!

---

### Post by HermanAB on 2014-05-01
Ordinary dd or cat?
# cat /dev/sdX > /dev/sdY
# dd if=/dev/sdX of=/dev/sdY bs=64K

However, if the drive is really bad, then it may abort after some time.

---

### Post by sleepingsword on 2014-05-01
I tried ordinary dd at first but as it didn't have any progress indicator, I tried pv to get at least a progress bar with dd, but that bombed on a read error so I went with ddrescue as that is tolerant of read errors.

as far as i understand bad sectors do not get marked on read errors, only on write errors. is there any drive util I can use to mark them all so I can just use a standard copy?  or am I barking up the wrong tree with that one?

---

### Post by sudodus on 2014-05-01
Read the info page ```
info ddrescue
``` very carefully, so that you understand what you will be doing.

Use Example 1 as a template (modify to fit the device letters of your computer).

Boot from one drive. Clone from a second drive (the source) to a third drive (the target). Use a ***log file*** (write the log file to the boot drive if it has write access, otherwise to a fourth drive (for example a pendrive). The log file makes it possible to run ddrescue in [COLOR=#0000ff]two steps[/COLOR]

```
Example 1: Rescue a whole disc with two ext2 partitions in /dev/hda to /dev/hdb.
Note: you do not need to partition /dev/hdb beforehand, but if the
partition table on /dev/hda is damaged, you'll need to recreate it
somehow on /dev/hdb.

[COLOR=#0000ff]     ddrescue -f -n /dev/hda /dev/hdb logfile
     ddrescue -d -f -r3 /dev/hda /dev/hdb logfile
[/COLOR]     fdisk /dev/hdb
     e2fsck -v -f /dev/hdb1    # my comment: only for ext file systems, use Windows tools for NTFS
     e2fsck -v -f /dev/hdb2    # my comment: only for ext file systems, use Windows tools for NTFS

```

---

### Post by HermanAB on 2014-05-01
Hmm, dd does have a progress indicator.

Open a second console and run:  
# kill -USR1 $("pgrep dd")

Then dd will hiccup and give you the progress.

---

### Post by sleepingsword on 2014-05-01
@hermandab
I am not using dd, but gnu ddrescue.

@sudodus
if I stop and restart with logging can I speed up the process, eg:
if it slows to B/s like it is now, resuming ddrescue will be fast again, or just resume at the same slow speed because the drive is faulty?

also the configuration I am using is: my PC with a blank 1tb drive and the suspect 1tb drive hooked to the internal sata (no other drives, incl. no system drive), booting from a Ubuntu livecd on a 16gb USB stick, I assume the log will just save to the USB stick?





I chose ddrescue because it's the only thing I found that keeps going regardless of errors, most other stuff I tried just stops, usually with no error or info message.

I am open to other suggestions if anyone has any?

---

### Post by Mark Phelps on 2014-05-01
>  has slowed to a crawl... 

In my experience, this means that it's trying to read bad sectors and it will attempt those reads over and over until it succeeds or times out.  Unless you can find a way to skip over the bad sectors, it is going to take a very long time to get through them.

---

### Post by sudodus on 2014-05-01
> **sleepingsword said:**
> @hermandab
I am not using dd, but gnu ddrescue.

@sudodus
if I stop and restart with logging can I speed up the process, eg:
if it slows to B/s like it is now, resuming ddrescue will be fast again, or just resume at the same slow speed because the drive is faulty?

also the configuration I am using is: my PC with a blank 1tb drive and the suspect 1tb drive hooked to the internal sata (no other drives, incl. no system drive), booting from a Ubuntu livecd on a 16gb USB stick, I assume the log will just save to the USB stick?

I chose ddrescue because it's the only thing I found that keeps going regardless of errors, most other stuff I tried just stops, usually with no error or info message.

I am open to other suggestions if anyone has any?

> **Mark Phelps said:**
> In my experience, this means that it's trying to read bad sectors and it will attempt those reads over and over until it succeeds or times out.  Unless you can find a way to skip over the bad sectors, it is going to take a very long time to get through them.

The big advantage with the double-pass method is to run the first pass quickly to get all the 'good sectors', using the -n option.

```
`-n'
`--no-split'
     Stop after the trimming pass. Avoids spending a lot of time trying
     to rescue the most difficult parts of the file. This option
     overrides the `--max-retries' option.
```

See post #4

---

### Post by piet3 on 2014-05-02
Hi,

I'm doing a similar excersize and it seems the logfile is the route to go but booting from the Live CD and running ddrescue with the logfile option will only run for about 5min before it says the drive is full. I'll start a thread about this... since it's not nice to hijack. I understood that the logfile options helps a lot in getting as much data back as possible.

Regards
Piet

---

### Post by sudodus on 2014-05-02
> **piet3 said:**
> Hi,

I'm doing a similar excersize and it seems the logfile is the route to go but booting from the Live CD and running ddrescue with the logfile option will only run for about 5min before it says the drive is full. I'll start a thread about this... since it's not nice to hijack. I understood that the logfile options helps a lot in getting as much data back as possible.

Regards
Piet

I'd suggest that you write the log file to a fourth drive, for example a USB pendrive.

Please post a link to your own thread, and let us continue the dialogue 'over there' :-)

---

### Post by piet3 on 2014-05-14
Done:
[http://ubuntuforums.org/showthread.php?t=2221450](http://ubuntuforums.org/showthread.php?t=2221450)

---

