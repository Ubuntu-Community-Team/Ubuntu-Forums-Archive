---
title: "can't resize lvm volume"
date: 2006-10-27
forum: General Help
---

### Post by cainlevy on 2006-10-27
i've installed edgy eft with an lvm setup. lvm itself is no stranger to me, as i had it running and became comfortable with the general commands during my previous life as a gentoo user.

but now when i try to resize my lvm partitions i run into a couple hard walls. can't figure 'em out. anyone have a good intuition about the problems described below?

`lvdisplay` reveals the following logical volume:
```

--- Logical volume ---
LV Name                 /dev/lvm/home
VG Name                 lvm

```

`grep home /etc/fstab` reveals the following mount:
```

/dev/mapper/lvm-home /home ext3 defaults 0 2

```

and already it looks odd. why is the lv at /dev/lvm, but it's mounted from /dev/mapper?

`ls -R /dev/lvm` makes me wonder where lvdisplay gets its info:
```

/dev/lvm

```

especially since `ls -R /dev/mapper` makes it seem like fstab's take on things is correct
```

control lvm-home lvm-mp3s lvm-opt lvm-tmp lvm-usr lvm-var

```

ok, so i'm confused. but i try and run `lvresize` however i can. first i try to use the info from lvdisplay by running `lvextend --size +5G /dev/lvm/home`:
```

Extending logical volume home to 15.00 GB
/dev/lvm: mkdir failed: File exists
Failed to create symlinks for home
Failed to suspend home

```

well that looked like it almost worked. it's better than the result of `lvextend --size +5G /dev/mapper/lvm-home`:
```

Volue group mapper doesn't exist

```

so ... what's up? anyone?

---

### Post by cainlevy on 2006-10-27
i fixed this problem by logging out, unmounting my /home partition, moving /dev/lvm to /dev/lvm.bak, and running lvextend on /dev/lvm/home. the previous /dev/lvm was i-don't-know-what, but lvextend created a new /dev/lvm directory which now contains only one of my 5 volume groups.

seeing how that worked, i believe that a better resolution may have been to run vgrename, but i'm unwilling to experiment unnecessarily with my hard drive. ;)

---

