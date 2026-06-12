---
title: "External HDD connected via USB to SATA not bring recognised...help needed please!"
date: 2019-06-30
forum: General Help
---

### Post by darrenkarp2 on 2019-06-30
Hi All,

Long story short. My Buffalo NAS drive had problems. I removed the HDD (it's 500GB) and connected it to my Windows 10 PC to see if I could recover the files from it. I've tried quite a few software apps that display the data I need but they all require a licence fee. I've installed the latest version of Ubuntu on VirtualBox and it doesn't show me the drive. I should add that all the recovery program I've used so far say it's a RAW HDD as the partition seems to have been screwed up.

Can anyone offer any advice on how I can get access to the files?

Thanks
Darren

---

### Post by HermanAB on 2019-06-30
Try booting the working machine with a Linux install disc/USB widget (but don't install!). You may then be able to access the faulty HDD - provided that there is some life left in it, with ddrescue.

---

### Post by darrenkarp2 on 2019-06-30
Thanks for the reply Herman. Remember I'm using Ubuntu on VirtualBox on my W10 PC. Are you saying I should try running it differently. I'm new to Linux so would need some baby steps!

---

### Post by HermanAB on 2019-06-30
All the tools you need are in the Linux install image.  So boot the installer to the desktop, then you can do the needed with the HDD without making any actual changes to the Windows machine.  Google ddrescue for details.

---

### Post by darrenkarp2 on 2019-07-01
So burn a copy of Ubuntu on a bootable USB stick and run it without installation then get and install ddrescue (not sure yet where I download that from), correct so far?

---

### Post by darrenkarp2 on 2019-07-01
Hi,

I have an update following Herman's suggestion. I booted Ubuntu Live and the desktop showed the drive I need to recover, I saw the correct folder where all the data is in (called Share) but it was empty so I then installed ddsrecue-gui (after a little fun with repos, etc.) but I have no idea what device to select as it's input source as many appeared. How do I know the correct device to select?

---

### Post by darrenkarp2 on 2019-07-02
Anyone?

---

### Post by SeijiSensei on 2019-07-02
If there's only one drive, you should just see the partitions.  /dev/sda1, /dev/sda2, etc.  If you have multiple drives, they'll have different letters, like /dev/sdb1, /dev/sdc1, etc.

Last time I used ddrescue I cloned the entire device (/dev/sda), so I'm not sure what you'll be seeing. Plus I ran it from the command prompt.

```

GNU ddrescue - Data recovery tool.
Copies data from one file or block device to another,
trying to rescue the good parts first in case of read errors.

Usage: ddrescue [options] infile outfile [mapfile]

```

The options list is long (see "man ddrescue") though I don't recall needing anything fancy.

---

