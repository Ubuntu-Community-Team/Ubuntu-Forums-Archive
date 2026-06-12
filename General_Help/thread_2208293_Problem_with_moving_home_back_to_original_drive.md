---
title: "Problem with moving /home back to original drive"
date: 2014-02-27
forum: General Help
---

### Post by samwillc on 2014-02-27
Hi everyone,

I moved my /home onto a second internal drive. However, I wish to use this other drive for something else so for the meantime, I want to move /home back to its original place. I found the guide here:

[http://askubuntu.com/questions/122464/move-the-home-directory-back-to-single-partition](http://askubuntu.com/questions/122464/move-the-home-directory-back-to-single-partition)

However, I am stuck on it. I go to recovery and unmount home, then mount the second disk as /media/whatever, then copy. This is what I'm stuck at, how do you specify the destination?

```

1) umount /home
2) mount /dev/sdb1 /media/disk
3) COPY, HOW? i.e. [COLOR=#c20cb9]**sudo**[/COLOR] rsync [COLOR=#660033]-aXS[/COLOR] [COLOR=#000000]**/**[/COLOR]home[COLOR=#000000]**/**[/COLOR]. [COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]home[COLOR=#000000]**/**[/COLOR].

```

Do I just reverse that last line? i.e.

```

sudo rsync -aXs /media/whatever/. /home/.

```

This is the current setup:

```

/dev/sda1: UUID="a36304b8-a3f0-42fb-8f42-5fa8d52eed6d" TYPE="ext4" 
/dev/sda5: UUID="118fdd3b-914a-4b5f-8a19-e55b12d9604b" TYPE="swap" 
/dev/sdb1: LABEL="500GB HDD" UUID="4d8990d8-8716-49a6-ace4-3d558127e431" TYPE="ext4"

```

with fstab like this:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a36304b8-a3f0-42fb-8f42-5fa8d52eed6d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=118fdd3b-914a-4b5f-8a19-e55b12d9604b none            swap    sw              0       0
UUID=4d8990d8-8716-49a6-ace4-3d558127e431 /home ext4 nodev,nosuid 0 2

```

I had to manually add in the last line for UUID=4d8990d8-8716-49a6-ace4-3d558127e431.

After I've copied everything, do I then have to modify this line?

```

# / was on /dev/sda1 during installation
UUID=a36304b8-a3f0-42fb-8f42-5fa8d52eed6d /               ext4    errors=remount-ro 0       1

```

...to point it to /home?

Any extra help would be very much appreciated, thanks. Just a bit stuck on the details.

Sam.

---

### Post by dragonfly41 on 2014-02-27
By coincidence today I've been reading up on relocating /home from a rapidly filling partition .. but I've been able to gain a reprieve by relocating some large folders to another partition.

However .. for your own problem you might pickup some tips from this article I found ..

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by SeijiSensei on 2014-02-27
Yes, just restore to /home.  Once the drive is unmounted, /home is just another directory in the root filesystem tree.  However, after you've unmounted the device, check to see that /home is empty. When a device is mounted onto a directory with existing files, those files become invisible to the operating system.  So there could be some junk lying around in the original /home directory.  Archive anything you might want to keep outside the /home directory, then delete whatever else remains so /home is empty.  Now run rsync in the manner you propose.

---

### Post by samwillc on 2014-02-28
Thanks everyone. After unmounting home and mounting at /media/home/ when I ran:

```
sudo rsync -aXs /media/home/. /home/.
```

...in recovery after unmounting home, I got a bunch of errors like file system is read only or something. I couldn't get it to work. Backed up everything on external and did clean install. Not ideal but a good chance to clear the rubbish out. I must work out how to do this operation though for the future. Not sure whether I had to do ALL of the above in recovery or do the copying once logged back in.

---

### Post by jeanjd63 on 2014-02-28
The good command are (in root)  :
[B]mount /dev/sdb1 /media
[/B]**cp  -a  /media/.  /home**

---

### Post by oldfred on 2014-02-28
You should also have in fstab you mount of /home or sdb1 and need to remove that before rebooting. Or you will have your old /home mounted with the old data partition not the internal to / (root) partition data.
You can delete line or edit out as comment out just by making first character # (like some of the other lines).

---

