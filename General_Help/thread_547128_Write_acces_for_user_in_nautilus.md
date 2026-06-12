---
title: "Write acces for user in nautilus"
date: 2007-09-09
forum: General Help
---

### Post by Joje on 2007-09-09
I have a few additional hard drives in my computer, well, four actually. What I would like to do is give myself automatic read and write priviligies to these when I mount them from the "Places"-bar (I think that is the correct name, I'm not using the English-language settings) in Nautilus. If I gksudo nautilus they don't appear at the "Places"-bar and it seems I have to take the long road to mount the drives and then gksudo nautilus all the time. Anyway, it seems to me that there should be some way to treat mounted drives as extensions to my home directory or something like that. Some way to easily, or preferably automaticly, give me read and write access to mounted hard drives in nautilus. Is there a way to do this?

Sorry 'bout the language, English is my second language and I'm sick (the flu or something like that) and tired.

---

### Post by merlinus on 2007-09-09
What are the filesystems and mountpoints?

---

### Post by Joje on 2007-09-09
I've got 2 partitions with ext3, 2 with ext2.

The mount points are:

/media/SATA250A               ext3
/media/SATA250B               ext2
/media/SATA200                 ext2
/media/IDE160                     ext3

---

### Post by merlinus on 2007-09-09
Try this:

```

sudo chown -R username:username /media/x

```

where username is your login id and x is the folder in /media.

---

### Post by Joje on 2007-09-09
I think that worked. Thanks a lot!

---

### Post by merlinus on 2007-09-09
Excellent!  Glad to help.

---

