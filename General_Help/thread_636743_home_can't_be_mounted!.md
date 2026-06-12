---
title: "/home can't be mounted!"
date: 2007-12-10
forum: General Help
---

### Post by Christoph Bier on 2007-12-10
My home directory of my office PC is located on an external USB disk, identified by its UUID. From /etc/fstab:

```
UUID=5e6531ed-d85e-4300-b713-a61d9496a6e6    /home  ext3        defaults,user,errors=remount-ro      0  1
```

Everything worked fine for about six weeks. But today it just fails and I don't have any glue what's going wrong. I'm at my office but I can't work :mad:. So I really appreciate any help! I created a dummy account with $HOME on the internal disk to post this message.

When I try to mount /home I get the following:

```
sudo mount /home
mount: special device /dev/disk/by-uuid/5e6531ed-d85e-4300-b713-a61d9496a6e6 does not exist
```

But the UUID is correct:

```
$ tune2fs -l /dev/sdb1 | grep 5e
Filesystem UUID:          5e6531ed-d85e-4300-b713-a61d9496a6e6
```

So I try to mount the disk by its block device name:

```

$ sudo mount /dev/sdb1 /home/
mount: unknown filesystem type 'jmicron_raid_member'
```

I never read this message before and the disk has an ext3 filesystem! 

```
$ parted /dev/sdb print | grep -1 'File system'

Anzahl  Beginn  End     Size    Type    File system  Flags
 1      32,3kB  25,0GB  25,0GB  primär  ext3
```

I already asked Google about it but didn't find anything. fsck.ext3 ends up without any errors or warnings. 

It's quite strange since nobody has access to my office PC and everything worked just fine till today. I didn't change anything ... 

Because I have a lot of work to do I hope somebody can help me!

Best regards
Christoph

---

### Post by Christoph Bier on 2007-12-10
> **Christoph Bier said:**
> 

[...]

```

$ sudo mount /dev/sdb1 /home/
mount: unknown filesystem type 'jmicron_raid_member'
```

[...]



Stress and mental pressure make me blind. Now at home in the shower I had an idea ... Telling mount via the -t option that the filesystem to be mounted is an ext3 filesystem works :). Though this is a clean workaround (at least at home---I will try it tomorrow at office) I still wonder why

mount /dev/sdb1 /home

suddenly stopped working.

Best
Christoph

PS: I also asked my question on the Ubuntu users mailing list. Sorry for my impatience but it's a severe problem for me if I can't work at my office PC.

---

