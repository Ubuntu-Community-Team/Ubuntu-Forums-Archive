---
title: "Best way to recover image file"
date: 2018-05-05
forum: General Help
---

### Post by 5circles on 2018-05-05
I'm hoping someone can suggest strategies to recover an image file that I lost in process of setting up a Ubuntu 18.04 system.  I don't think the fact that 18.04 is involved, or even that it's Ubuntu makes much difference.  Sorry if the background is too long.  The ultimate question is at the bottom - are there better tools than [FONT=Courier New]foremost [/FONT]to recover image files.

I created images of partitions on the existing drive using partclone.  The images of previous Ubuntu versions were intended for safety and to pull off previous configurations if needed to get a solid 18.04 system.  One more image was from a earlier clone of a NAS system, also on the existing drive.  It was larger (about 450G) and in a sense more precious because of issues with the NAS and my desire to get the most up-to-date files through consolidation.  All the images except the NAS have copies on a external drive - because of speed creating, and expected need for speed in consolidation.  There is also an internal 4TB drive that just had one partition with all the images - the last being the NAS clone image.


I repartitioned the original drive by deleting the oldest Ubuntu partition (which was after the Windows partitions), deleting the NAS clone partition, and creating a new partition overlapping the spaces.  The Ubuntu 18.04 installation went OK - after the usual false starts and redos - so I was ready to start consolidation.

I resized the single partition on the 4TB drive to allow space at the end of the drive for a partition to restore the image of the oldest OS partition from the original system  - **/dev/sdb2**.  I made a mistake in the partclone restore command and restored to **/dev/sdb1**.  So now I had made the 3 OS partition images and the NAS clone image too - all inaccessible.  Before I thought that the image files might be restored with forensic tools, I restored a different image to **/dev/sdb2**.  Then I thought about data recovery.

From reading [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery") it looked like [FONT=Courier New]foremost [/FONT] was the place to start.  The 4TB drive had no hardware problems, and hopefully the image files after the space occupied by the partclone restore would able to be found.  There is 114G used according to Nautilus.

I started foremost yesterday using a second fresh 4TB as the recovery target, and it's still going, showing currently well over 350G recovered.  That's much bigger than the images that were on the first 4TB (excluding the NAS clone) .  And, since it's recovering individual files (no .img files yet), I'm guessing it is pulling the contents of the image files or at least recovering files directly from the drive.

So, my question again - is there a better tool than [FONT=Courier New]foremost [/FONT] to recover image files?  I know what the name of the file is if that makes a difference.  

Thanks
Mike

---

### Post by dragonfly41 on 2018-05-05
You are on the right path by trying foremost from that link.
But there are other tools to try.

[https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

In that article are mentioned testdisk, photorec, scalpel ..

In google searching around for tips use "ubuntu forensic data recovery" (the emphasis on "forensic").

Have you considered making a clone of your image so that your recovery experiments are on the clone and not the original?

Other tools I have tried are R-linux and I had read good reports about SpinRite at GRC website (I have never used it though).

**[COLOR=#b22222][Later edit][/COLOR]** Another link from my bookmarks.

[https://forensicswiki.org/]("https://forensicswiki.org/wiki/Tools:Data_Recovery")

---

