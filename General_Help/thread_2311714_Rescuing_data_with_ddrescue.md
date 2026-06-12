---
title: "Rescuing data with ddrescue"
date: 2016-01-29
forum: General Help
---

### Post by liom101 on 2016-01-29
I don't know if this is the best place to put this, sorry if it's out of place 

My dads 2010 macbook pro failed to boot the other day. After messing around with an ubuntu live usb for a while I came to the conclusion it's dying and put it in another pc running xubuntu. Managed to mount it successfully but ls fails on a lot of the folders on it, with an Input/output error. Gnome-disks says the disk is failing. I have zero access to anything on it and it has a lot of family photos which my dad hasn't backed up since 2013..
I have started running ddrescue with no scrape mode enabled, but it is still going terribly slowly. I wanted to be sure I would be able to read the image afterwards so I paused it, but I can't mount the image.
```
sudo mount -t hfsplus -o ro,loop     recovery.img mountpoint
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
dmesg | tail returns this:
```
13776.678812] hfsplus: unable to find HFS+ superblock
[14000.560778] hfsplus: invalid secondary volume header
```
I've tried various other methods of mounting it after a lot of googling with no success.
I tried using fsck but that didn't help and returned this:
    ```
sudo fsck.hfsplus -y recovery.img
** recovery.img
** Checking HFS Plus volume.
   Invalid number of allocation blocks
```
I'm worried about leaving this going for the next few days, or heck maybe even longer and not even being able to mount the image. I'm also worried about what damage ddrescue is going to do to the hard drive just by accessing it constantly for this length of time, but I don't think I have much choice? Should I let ddrescue complete before I attempt to mount it? Will fsck have modified the image in anyway? I don't want to have to do the whole drive over again because I ran fsck, it's been going about 24 hours now and only done ~18gB out of 750gB

---

### Post by lah-ca on 2016-01-29
Hi,

You could try PhotoRec.  It is in the repository bundled with Testdisk, I believe.  Start Ubuntu Software Center and search for Testdisk.

Ref: [http://www.cgsecurity.org/](http://www.cgsecurity.org/) and more specifically [URL="http://www.cgsecurity.org/wiki/PhotoRec"]http://www.cgsecurity.org/wiki/PhotoRec

[/URL]Also: [URL="http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"]http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step

[/URL]Also: [http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

It does a sector by sector crawl across the hard drive doing a forensic-type of data recovery.  Files are recovered without regard to file names or place in the source's data structure - they are given alphanumeric names and are placed in recovery folders with about 500 files per folder.  It is a command line utility that can be run with flags to select/exclude specific file types I think.

I just used it on my daughter's hard drive.  I have used it many times to recover data from unreadable corrupt/damaged USB keys. It is effective, but the results are messy and thus require a bit of effort in renaming and reorganizing the recovered files.

I recommend it highly as a safety net recovery option before trying any potentially destructive recovery options.

Best of luck.

---

### Post by liom101 on 2016-01-29
I wasn't aware of this tool! thank you! Paused ddrescue and going ahead with this. Just a bit worried as it's still estimating 470 hours.. but it said 26,000 hours a few minutes ago and it's early on so I guess the estimate is really inaccurate. I'll leave it going tonight and see how it does. I like that the results are a bit more instant, recovered 6 files so far, totalling about 400mb but they're .abcdp files, which I didn't even know existed! How long would you expect it to take? Although that's probably really dependent on how much damage has been done.

---

### Post by lah-ca on 2016-01-29
> **liom101 said:**
> I'll leave it going tonight and see how it does. I like that the results are a bit more instant, recovered 6 files so far, totalling about 400mb but they're .abcdp files, which I didn't even know existed! How long would you expect it to take? Although that's probably really dependent on how much damage has been done.

Hi,

The speed of recovery is largely dependent upon the size of the drive.  I believe the utility just crawls across the surface of the hard drive platters, sector by sector, looking for files.  Because it is a forensic-type utility, designed to work even where there is no longer any partition recoverable/repairable, it is methodical and [COLOR=#ff0000]***_slow_***[/COLOR].  For me it took a full 24 hour day or so to process a 1 Tb, 7200 RPM, SATA3 hard drive, one without any "issues" other than a corrupt partition.

One thing that I forgot to mention is that you won't be able to delete any files in the recovery directories, at least not directly, because, if you ran Photorec with sudo, as you should, the recovered files belong to root.  You will have to change ownership of the folders, or you could try launching nautilus or some other file manager from a terminal with sudo.

Note also that recovery results can sometimes be embarrassing.  Files that one assumed were deleted and gone are also recovered if the space they formerly occupied was not overwritten.  :oops: 

Be patient.  It all takes time, and you haven't yet started looking for survivors in the train wreck.

---

### Post by liom101 on 2016-01-29
haha! I like the way you put that. As it's my dads laptop, who knows what I'll find! The drive is 750gB but yea I think the amount of errors is going to slow it down massively, still says 698hours till completion :/ found a hell of a load of files though, about 18k png files, all of which are buttons and stock images etc. But oh well hopefully I'll get a lot back from this!

---

### Post by liom101 on 2016-02-04
would just like to add: It's still going, 150 hours in. 140,000 files found, lots of photos but sadly nothing that wasn't already backed up yet. The estimated time remaining started at 650hours and has just steadily increased to 780 hours now, which is a bit annoying. This is a crazy long time, I now I'm seeing results but is this really the best option? I'm thinking I might even have to run ddrescue after this too if it can't get everything. Scrape mode will be even longer too! I guess I might get some sort of information as to what sectors the newer photos were found on so I could just scrape those sectors?

---

### Post by liom101 on 2016-02-05
well, I feel very stupid now. I was recovering every filetypel, and suddenly had the revelation that it might be quicker if I limited it to what I was interested in. Changed the criteria and resumed from the sector I'd reached before by modifying the new photorec.ses file's offset parameter... 45 hours to go! Much more like it!

---

