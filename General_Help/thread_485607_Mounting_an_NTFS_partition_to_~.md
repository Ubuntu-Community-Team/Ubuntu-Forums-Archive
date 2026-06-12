---
title: "Mounting an NTFS partition to ~"
date: 2007-06-27
forum: General Help
---

### Post by agent154 on 2007-06-27
I have an NTFS partition on /dev/hda5 and I would like it to be perminantly mounted to my homedir. Is this a bad idea? If not, what would I put in my /etc/fstab to make it so? I've fooled around and I can't seem to get it to work, I can only get it to mount to a folder in my homedir...

Basically, this partition serves as my "My Documents" when i'm in Windows.. I want it to be the same thing in linux

---

### Post by merlinus on 2007-06-27
Is this what you are after?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

-merlin

---

### Post by mikewhatever on 2007-06-27
I believe Merlin had another link in mind from psychocats
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

If /dev/hda is mounted elsewhere, all you need to do is:
create the directory to mount it in
change the mount point in fstab to that directory

---

### Post by agent154 on 2007-06-27
Thanks, but those don't quite help... I already know HOW to mount NTFS, Ihave it mounted right now... but I want it to be my /home dir. My only concern is whether or not it's good to have anything but a linux based FS as my homedir due to the differences in security measures.

I've tried mounting it to /home/chris but when I load up Ubuntu, it didn't seem to work, I still had my old home dir.. Maybe I just set some settings wrong, dunno.

---

### Post by Qu4k3R on 2007-06-28
have you tried to change from /media/hdX to ~/hdX (your partition) into the mount options?
Maybe you should give it a try.

Changing:

> sudo nano /etc/fstab

This:
```

/dev/hdax /media/hdax ntfs <options>

```
to
```

/dev/hdax /home/<your_username>/<partition_name> ntfs <options>

```

---

### Post by mikewhatever on 2007-06-28
> I've tried mounting it to /home/chris but when I load up Ubuntu, it didn't seem to work, I still had my old home dir.. Maybe I just set some settings wrong, dunno.
Why would you do that? It would make a terrible mess C:\ with all the config files, besides, I do not know if /home can be ntfs. I thought you wanted to mount it inside your home, something like /home/chris/windows, which should be possible. Anyway, if you really want to move your home partition, the link Merlin posted was the direction to go.

---

### Post by Qu4k3R on 2007-06-28
You can make a link to /media/<ntfs_drive>

It would be easier.
And it would work also.

---

