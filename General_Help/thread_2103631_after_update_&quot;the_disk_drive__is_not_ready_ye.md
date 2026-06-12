---
title: "after update &quot;the disk drive / is not ready yet or not present?&quot;"
date: 2013-01-10
forum: General Help
---

### Post by hortstu on 2013-01-10
I'm hoping that this update just takes many hours to take effect?

Can anyone reassure me or let me know there is a problem so I can start looking into fixing it? I'm starting to regret updating.  I've never done it through the update manager.  I was putting it off, I was unsure of it, then I finally broke down and did it.  Now here I am.

---

### Post by hortstu on 2013-01-10
Hey,

googled the error.  searched the forums. Still having a problem here.  The only thing I can get to boot is an old version of hardy heron.  I can't even access the other partitions.  Gparted says they're still there but I'm really at a loss.  Can anyone help me?

---

### Post by hortstu on 2013-01-10
So here's what I've done so far.

```
# mount -o remount,rw /
# dpkg --configure -a
```

Then I got,

```
#dpkg: error: parsing file '/var/lib/dpkg/status' near line 13532 package 'xmind' blank line in value of field 'Description'
```

I tried,

```
sudo dpkg --clear-status
```

It replied,

```
dpkg: error: unknown option --clear-status
```

Then a lot more that I don't want to type unless someone insists

I'm under the impression that I'm trying to delete the file dpkg and then replace it with an update but I don't know the code.

Can anyone help?

---

