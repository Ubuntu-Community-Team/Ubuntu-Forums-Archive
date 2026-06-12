---
title: "Mount NTFS partition ntfs-3g"
date: 2007-04-06
forum: General Help
---

### Post by stchman on 2007-04-06
Hello all, I was messing around with mounting ntfs partitions using ntfs-3g.  I have always had my windows partitions mounted in read only form.

I installed ntfs-3g from synaptic and then did the following in my fstab file:

/dev/hda1       /media/windows ntfs-3g  nls=utf8,umask=0222  0   0

It worked.  I was now able to write to the windows ntfs partition.  My question is, is this bad to do it this way?  I have read some posts and there seems to be folks that do a lot of stuff to be able to mount ntfs partitions with read/write.

Is ntfs-3g safe?  I read that it is now no longer beta.

Thanks

---

### Post by Obor on 2007-04-06
As far as I know its stable now and seems to be working fine for everyone. The way you've done is correct and you should have no problems.

---

### Post by stchman on 2007-04-06
> **Obor said:**
> As far as I know its stable now and seems to be working fine for everyone. The way you've done is correct and you should have no problems.

Thanks, I just saw a lot of people installing a lot of other applications to go with ntfs-3g.  I am now wondering that some posts go on and on about installing ntfs-3g when all you need to do is:

sudo apt-get install ntfs-3g

then edit your fstab file.  Sometimes people over complicate matters.

---

### Post by rabid9797 on 2007-04-06
> **stchman said:**
> Thanks, I just saw a lot of people installing a lot of other applications to go with ntfs-3g.  I am now wondering that some posts go on and on about installing ntfs-3g when all you need to do is:

sudo apt-get install ntfs-3g

then edit your fstab file.  Sometimes people over complicate matters.

this is becuase awhile back ntfs-3g wasn't included in the repos, you had to download it yourself and do a manual install, and sometimes it took a litte but more than just editing an fstab line. way back when(lol) you had to install fuse as a startup item so that ntfs-3g would work correct and mount drives correctly.

now its even easier than editing an fstab line. with feisty(and i think edgy) you can just install nfts-config, which is a gui version of ntfs-3g that does the editing of fstab for you.

---

### Post by stchman on 2007-04-06
> **rabid9797 said:**
> this is becuase awhile back ntfs-3g wasn't included in the repos, you had to download it yourself and do a manual install, and sometimes it took a litte but more than just editing an fstab line. way back when(lol) you had to install fuse as a startup item so that ntfs-3g would work correct and mount drives correctly.

now its even easier than editing an fstab line. with feisty(and i think edgy) you can just install nfts-config, which is a gui version of ntfs-3g that does the editing of fstab for you.

Thanks.  So ntfs-config is a GUI for mounting ntfs hard drivers?

I love the pic of House.  That is my favorite show.

---

