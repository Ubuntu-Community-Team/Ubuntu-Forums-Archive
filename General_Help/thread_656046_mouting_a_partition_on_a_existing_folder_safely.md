---
title: "mouting a partition on a existing folder safely"
date: 2008-01-02
forum: General Help
---

### Post by radradrobotanks on 2008-01-02
Hello,

I just installed myth tv on a old installation (still 7.10). I have created a new logical volume called recording and have formatted it with the xfs filesystem. At the moment /var/lib is just a folder in a partition mounted at /. I am now wanting to mount my new logical volume partition at /var/lib as recommended by mythtv documentation. I tried adding
/dev/vg/recordings  /var/lib      xfs     defaults 0      0
to my fstab. This hid the old /var/lib contents. How would i do this without losing the old content of /var/lib. I would just do:

mkdir /tmp/old (will use sudo if required)
sudo cp -r /var/lib/* /tmp/old
# add above fstab line to /etc/fstab
sudo mount /var/lib
sudo cp -r /tmp/old* /var/lib

and hope it works but i want to be safe and make sure there will not be any nasty side effects.

Thanks Louis

---

### Post by ~LoKe on 2008-01-02
I don't see why that wouldn't work, so long as you're not overwriting files which are not the same.  Make sure to have backups of both directories just to be safe.

---

### Post by radradrobotanks on 2008-01-02
Unfortunately sudo cp changes who owns the files to root. Probably should have seen this coming. To late now. Do I have to re install this seems to be causing problems?

*edit: fortunately when i unmouted /var/lib the existing files were there untouched. So how do I do this without problems?

*edit 2: Ive used cp --archive or cp -a preserves timestamps, ownership of file and all the rest i think. Ive also noticed that if i umount the new partition the old data is still there. I imagine i need to remove this old redundant copy to free up space. Still so much to learn about the linux filesystem!!!

---

