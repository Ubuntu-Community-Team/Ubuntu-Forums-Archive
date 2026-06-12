---
title: "edgy broke after update last night"
date: 2007-01-01
forum: General Help
---

### Post by m.musashi on 2007-01-01
I ran a long overdue update on my kids edgy laptop last night and now I cannot boot - even with recovery. It had been working fine. I copied some wallpapers onto my daughter's /home and they ended up with my permissions. Using ssh, I logged in and chown'd them and then noticed that it was in need of an update so I ran sudo apt-get update, upgrade while still logged in via ssh. There was no noticeable problem until she tried to boot today. A normal boot brings up the ubuntu splash but the progress bar never moves and after a while I get a flashing cursor and a blank screen. With a recovery mode boot it got to something about usb drivers and hung. I disconnected the usb mouse and speakers and rebooted. It went a bit further and then hung on something about orphan cleanup (see attached photo).

I have no idea how to fix this other than to just reinstall. I'd like to avoid that if possible. There aren't a lot of important files on the computer but a few things I'd rather not lose.

Thanks.

Oh, the laptop is a dell latitude d505 with a celeron M, 512 of memory (i.e. nothing fancy) and was running a default edgy install with some automatix enhancements (no beryl, nvidia driver or anything like that).

---

### Post by ahaslam on 2007-01-01
Any idea what the updated packages were?
What's on hda6 & is it supposed to be readonly?

Tony.

---

### Post by m.musashi on 2007-01-01
I didn't really look through the packages but it had been a month or so since the last time I ran an update on that computer. There were a lot of packages including a kernel update (same version numbers though.

hda6 should be the root partition for ubuntu. The computer has a dual boot with hda5 being home (if I remember right) hda6 / and hda7 swap. It should not be read only.

---

### Post by m.musashi on 2007-01-02
I'm trying some other ideas but no luck so far. My thought was to boot a live cd and see if I can track down the problem. I actually had some trouble on my desktop after using chown and it messed up apt-get. In doing some research it sounded like maybe the problem on the lappy was similar. However, after booting the live cd I cannot mount / . When I try, the terminal just hangs. I created a mount point but no luck.

Any reason the partition wouldn't mount? If I can't mount it from a live cd does that basically mean the partition is shot and I need to just start over? If so, can changing user permission really cause this much trouble?

Thanks.

---

### Post by raul_ on 2007-01-02
I have no idea...Anywayz, try booting with the Live CD and do
```

sudo mount /dev/hda6 /mnt

```

or did you run EXACTLY the same command? You can post from the Live CD if it works

---

### Post by m.musashi on 2007-01-02
Thanks for taking a look at this.

I tried that and a couple variations (sudo mount -t ext3 /dev/hda6 /mnt/hda6 (I made a folder called hda6)). None worked. The terminal just gives me a blinking cursor but never returns to a prompt and doesn't mount.

The live cd does boot but if I can't mount / there isn't much I can do.

---

### Post by raul_ on 2007-01-02
you can always try (in the Live CD)
```

fsck /dev/hda6

```

---

### Post by m.musashi on 2007-01-02
The plot thickens. That returned
```
fsck.ext2: Permission denied while trying to open /dev/hda6
You mush have r/w access to the filesystem or be root
```

Oh, wait, maybe I need to use sudo.

Okay, that produced
```
device or resource busy while trying to open /dev/hda6
filesystem mounted or opened exclusively by another program?
```

I'm going to reboot it. Maybe all the mount attempts have left it confused or something.

EDIT:

Okay, after a reboot, fsck returned
```
truncating orphaned inode 127278 (uid=1002, gid=1002, mode=0140755, size=0)
/dev/hda6: clean, 108538/429408 files, 645376/857461 blocks
```

EDIT2:

After the fsch I rebooted normally and no more problems. Cool trick that fsck. I'll have to remember that. Thanks for all the help. It looks like everything is back to normal. I would just like to know what I did and why it caused the problems.

Thanks again.

---

