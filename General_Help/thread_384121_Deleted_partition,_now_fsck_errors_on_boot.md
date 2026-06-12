---
title: "Deleted partition, now fsck errors on boot"
date: 2007-03-14
forum: General Help
---

### Post by trevorv on 2007-03-14
Hi,

I have deleted the partition /dev/hda8 using fsck, but now I get errors on boot. I assume there is something I need to do to tell it the partition no longer exists, as this seems to be the problem, but I don't know what.

It moans about /dev/hda8 not existing, and /var/log/fsck/checkfs reads

```

Log of fsck -C -R -A -a 
Wed Mar 14 07:21:28 2007

fsck 1.39 (29-May-2006)
/dev/hda7: clean, 5266/2562240 files, 424322/5124727 blocks
fsck.ext3: Unable to resolve 'UUID=3082fcdf-10aa-4b03-a47c-bbb13a4497d2'
fsck died with exit status 8

Wed Mar 14 07:21:28 2007
----------------

```

If you could tell me how to clean this mess up I'd really appreciate it, thanks :)

---

### Post by Kateikyoushi on 2007-03-14
Show us your fstab.

```
cat /etc/fstab
```

What you have to do is remove the /dev/hda8 line or edit it if you have a new partition there.
Just in case show the partition layout as well.
```
sudo fdisk -l
```

---

### Post by trevorv on 2007-03-14
Thanks, I edited my fstab and now it's fine :)

---

