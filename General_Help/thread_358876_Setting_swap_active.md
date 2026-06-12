---
title: "Setting swap active"
date: 2007-02-11
forum: General Help
---

### Post by Patrick K on 2007-02-11
After the recent upgrade to -11, the system starts without SWAP being activated. I can set it active with gparted but have to do that every time I log in. How can I set it to automatically activate?

---

### Post by moshuptrail on 2007-02-11
How do you know it's not activated? What are you looking at?

Is there an entry in your /etc/fstab for a swap partition?

---

### Post by llamakc on 2007-02-11
Your fstab is messed up. Many people are having this problem.

You can either wait for them to fix the kernel issues, or edit your /etc/fstab so it points to your swap partition. I strongly recommend making a backup of your fstab BEFORE editing.

Also, you can turn swap on with the command:

sudo swapon /dev/hdX#

where X# is your drive/partition number. No reason to fire up GParted.

---

### Post by llamakc on 2007-02-11
Good point: you can check it with the command:

cat /proc/swaps

---

### Post by taurus on 2007-02-11
```
free
cat /etc/fstab
```

---

### Post by Patrick K on 2007-02-11
It is shown inactive in both gparted and system monitor. 

I've posted about editing fstab here:
[http://www.ubuntuforums.org/showthread.php?t=358602](http://www.ubuntuforums.org/showthread.php?t=358602)

There are several other issues with fstab. It seems the upgrade renamed all the EXT3 partitions and swap. And now there are some incorrect mount points. It took quite a while to get grub running correctly.

Thanks for the command. Gparted is not a problem to fire up since I have it installed.

---

### Post by taurus on 2007-02-11
I just answered your other post so please do not double post.

---

### Post by moshuptrail on 2007-02-11
Your fdisk -l output is showing hda8 as your swap.  Is that right?

```
/dev/hda8 19327 19457 1052226 82 Linux swap / Solaris
```

But your fstab has the following for hda8:  (I can't even be sure it's hda8 because your fstab is using UUID instead of device path.  The line with hda8 is actually a comment.  No guarantee the line below is really hda8!
```

# /dev/hda8
UUID=9f8d6e0b-f3b0-40e3-9e26-b3dcc3f84410 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
```

That doesn't look anything like my fstab entry for a swap, but I'm using Dapper, I'm guessing you're using Edgy.
Here's mine:

```
/dev/hda2       none            swap    sw              0       0 
```

---

### Post by Patrick K on 2007-02-11
Thanks for the reply. Thanks to Taurus, swap is now active and seems to be working correctly.

---

