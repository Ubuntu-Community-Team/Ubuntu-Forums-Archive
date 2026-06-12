---
title: "Looking for assurance from somebody familiar with partimage"
date: 2007-03-30
forum: General Help
---

### Post by Smuve on 2007-03-30
Goal:  I am tired of the owner/group/permission issues associated with fat32, so I am reformatting my internal data drive from fat32 to ext3.  

So far, I have used partimage to backup my data drive to an external harddrive.  As far as I can tell all has gone well.  The image is the same size as the data backed up.

I am now at the point where I will reformat the the fat32 drive to ext3.  However, I almost broke a sweat last night and I could not pull the trigger.  You see, I don't care about the music, but I have about 30GB worth of photos I am terribly afraid to delete.

I'm just looking for someone to tell me that partimage is awesome, go ahead and reformat, then restore the image.  

Anybody used partimage enough to tell me to pull the trigger?

---

### Post by aidanr on 2007-03-30
i think partimage will restore the partition as fat32, so you'd be better off just creating a compressed archive of the data rather than an image of the partition

---

### Post by ardchoille42 on 2007-03-30
I don't think partimage will save a fat32 partition and retore it as ext3. I use partimage all the time, but I would not recommend you doing what you have described with partimage. I would rather recommend aidanr's method above.

---

### Post by Smuve on 2007-03-30
Hmm.  I have enough room on the external drive so maybe I'll just copy the contents straight over as well.

Then I'll try a restore with partimage to see what happens.  If everything is fubar'ed, I'll just copy the contents back over.

Thanks for the advice, I'll let you know how it goes.

---

### Post by Smuve on 2007-03-31
Well, I'm glad I asked.  I used rsync to backup my files to the external hard drive, then reformatted the internal disk to ext3.  Next I tried to restore the image made with partimage when the drive was still fat32.

The copy completed, but the files were unreadable because the disk was not able to mount.  So I simply reformatted again and rsync'd the files back.

Thanks guys, you saved me from getting a beat-down by the wife if I had lost all those photos.

---

