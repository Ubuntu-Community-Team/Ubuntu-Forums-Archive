---
title: "Recover data from formatted hard drive"
date: 2007-03-08
forum: General Help
---

### Post by zachninme on 2007-03-08
I had been running Ubuntu Desktop Edgy Eft on my server, as I was just getting into Linux and was terrible at the CLI.

I switched to the Server edition of Ubuntu, but the backup of my server hadn't finished. 
Since I have no files on it yet, my old data shouldn't be overwritten, so I should be able to recover it.

What software do you think would work for this? All programs found on Google only run on Windows. I can run Desktop Ubuntu from a Live CD, if necessary :-)

Thanks.

Serverless,
zachninme

---

### Post by az on 2007-03-08
Foremost is a command-line tool which can recover files from a number of filesystems, including fat, ext3 and NTFS.  It can be installed and run from the live cd.

Enable the universe repository and install foremost:

sudo apt-get install foremost

Assuming the lost files are on a USB drive (sda), you need to create a writeable directory on another drive where you can put the recovered files

sudo mount /dev/sdb1 /recovery
sudo mkdir /recovery/foremost

And then run foremost:
sudo foremost -i /dev/sda -o /recovery/foremost

The recovered files will then be owned by root.  Change their ownership so that you can use them:
sudo chown -R youruser:youruser /recovery/foremost

---

### Post by etienne.navarro on 2007-03-13
How would you do this on a formatted partition that was formerly encrypted using LUKS?

---

### Post by peabody on 2007-03-14
Hate to say it, but you're probably screwed in that case.  With the increased security of filesystem encryption comes increased data volatility.

---

### Post by etienne.navarro on 2007-03-14
I thought so. :mad:
I do have a backup of a month ago but a month is quite a while. I guess I really should implement a daily rsync backup.

---

