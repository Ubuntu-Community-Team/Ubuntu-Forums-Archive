---
title: "2nd hdd, format as what?"
date: 2013-06-24
forum: General Help
---

### Post by mathiflip on 2013-06-24
Hi,

I recently upgraded my laptop with an ssd. I have a dual boot on the ssd with ubuntu 13.04 en win7. I have a 2nd hdd caddy for my old hardrive and want to use this for documents because of the bigger storage room on the hdd.
So it should be accessible from both OSs. What is the right way to format the second hdd?
I guess I have to go with NFTS so it's readable for windows, is this correct?
Also is it better to put /home on the second hdd instead of on the ssd?


All tips are welcome!

---

### Post by dshgna on 2013-06-24
NTFS is a good choice as its readable by both windows and linux. To make ntfs readable on linux, you'll have to have fuse and ntfs 3g, both available through the synaptic package manager. You'll then have to mount the ntfs partition on ubuntu. Here's the link to the article I used to figure it out :

[http://linuxconfig.org/how-to-mount-partition-with-ntfs-file-system-and-read-write-access](http://linuxconfig.org/how-to-mount-partition-with-ntfs-file-system-and-read-write-access)

I'm not sure of the placement of the /home partition. I think there may be a small performance improvement as it will be quicker to access files on the storage media, but leave it up to an expert to answer :).

Good luck!

---

### Post by CatKiller on 2013-06-24
The only (*) reason not to use an SSD for everything is because an SSD that can hold all your stuff might be prohibitively expensive. In that case, you prioritise flat bulk data to your spinning disk and stuff that's read often to your SSD where the performance improvements will be more effective. This means that if you keep music & videos and other bulky sequential things in your Home folder, that would be the sort of thing that you would put on the HDD. If you're happier with a more complicated partitioning setup, however, you can have your Home folder on the SSD for the performance boost when reading configuration files (which is pretty tiny, tbh, but can mount up) and the directories with bulky stuff in on the HDD, but symlinked into the appropriate place in your Home folder. ~/Documents, ~/Music & ~/Videos, for example.

EDIT: Also, if you've formatted the partition on your HDD as NTFS, you really don't want /home there; NTFS can't handle the permissions that you'd want for your Home folder as a whole.

* SSDs have a finite number of writes, but normal usage would have you running out of writes at the same sort of time that you'd expect a spinning disk to fail. Some applications have a much higher number of writes and will shorten the life of your SSD. Swap and /tmp would be examples of something that you probably wouldn't want on an SSD if there was an alternative.

---

