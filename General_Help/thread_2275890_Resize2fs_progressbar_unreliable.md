---
title: "Resize2fs progressbar unreliable"
date: 2015-04-29
forum: General Help
---

### Post by posterberg on 2015-04-29
Does anyone have experience with shrinking large (13TB) partitions?

I have after having three crashed disks within three months in my raid5 set decided to replace all the disks with newer and larger disks. Current raid5 set is 7 3TB disks which resulted in a 13TB. The 8th disk on the motherboard is the system disk.

First disk crashed three months ago and was replaced during warranty for free. No problems at all, just remove and replace...

Last week the second disk failed and I though that it might be a great idea to replace all disks so I ordered 5 new 6TB disks. Another disk semi-failed on the night to the day when I was supposed to pick up the disks. And I was terrified that everything was gone since I was now living with two failed disks in the raid5 set. I was however able to dd the semi-failed disk to a file on one of the new disks. It was surprisingly then possible to mount the assemble the set with one of the disks being a loopback device. Nervousness beyond recommendation up to this point... ;-)

The two old failed disks were removed and two new disks are installed in the box but only as normal single disks, that currently have been used to offload the old raid5 set to be able to shrink it. Main reason is that I don't have any other computer where I can fit all 6 disks and mount them. So I have to do this using the same computer and I need three free connections to the SATA controller before I can start creating the new raid5 set. I need to shrink the old set before I can remove more disks and get the new disks in...

I have now manage to free up so I have 8TB of free space on the current filesystem, currently being 13TB in total. I am hoping that shrinking it will allow me to remove another two disks so that I can get new disks in for the new raid5 set.

I have started up resize2fs (disk checks are performed and have corrected a few issues but disks are now clean).

resize2fs -p /dev/md0 7990GB

This has been running for 48 hours now, disks are working and I can see about 4% CPU utilization on the resize2fs process and about 6-12% on the md0_raid5 process. Everything seem to  be working just fine......

There's just one thing, the resize2fs progress bar behavior is weird. It has restarted probably 5 times now, it has never reached more than XXXX and it looks like it should reach 30* X in total.

Has anyone else experienced the progress bar restarting? I am starting to be concerned that I have told resize2fs to create a too small partition since I have read somewhere that it sometimes miss-calculates the minimum possible partition size. Could this be a reason?

Any help appritiated, also if anyone has any guesstimation on the total time needed to resize this filesystem.

BR,
Peter

---

