---
title: "Boot failing due to disk read error"
date: 2016-03-17
forum: General Help
---

### Post by neela on 2016-03-17
When I am booting into 14.04 I am getting a Add. sense unrecovered read error -  auto reallocate failed.  Is there a way to get around this problem to boot into the laptop,  or do I need to first backup,  reformat and reinstall? Thank you.

---

### Post by kc1di on 2016-03-17
It sounds like your Hardrive may be failing.  I would check that out first and yes back up all that you can. 
The reallocate error often means it's trying to reallocate bad sectors on the H.D.

---

### Post by howefield on 2016-03-17
Try booting from a Live medium, open a terminal and run the fsck command on the affected drive/partition, eg

```
sudo fsck /dev/sda1
```

change the path to suit your set up.

Don't try this on a mounted file system, use a Live DVD/USB

---

### Post by neela on 2016-03-17
Thank you.  Will try.

---

### Post by neela on 2016-03-17
If I have email on evolution,  would I be able rto get it off when I log in through  a live CD?  In order to be able to export the email to a transferable form,  I need to log in to the hard drive right?  This I cannot do.. 
Would appreciate any suggestions. 

Thanks.

---

### Post by Bashing-om on 2016-03-17
neela; Sure,

Depending on the hard drive health - howefield's post #3 - should be possible to mount that hard drive from the liveDVD and copy off your files.
To give explicit direction, we will need to know what we are working with,
Post back - from that liveDVD(USB) the output - Between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
such that we have the target identified. Then we mount the installed file system and access it to copy off the data to some external ( another USB thumb drive ?) media.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by neela on 2016-03-20
I was able to move stuff off of the hard disk. Thanks for the suggestions. I have had trouble with some of the email data. I think this is a separate issue, which I will post as a different thread.

---

