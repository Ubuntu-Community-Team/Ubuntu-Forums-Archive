---
title: "How do i stop auto mount?"
date: 2007-05-04
forum: General Help
---

### Post by TheDoulos on 2007-05-04
Any thoughts on the more interesting situation where I have volumes that I may want to mount manually, I just don't want them automounted at boot time?

I typically use KDE (Kubuntu), and whenever I install a distro, the first thing I do is manually edit the fstab file to restrict the mount options for all of my volumes:

```

# /dev/sda1[COLOR="Red"] - My Windows C drive - even if a user mounts it, make it read-only[/COLOR]
UUID=xxxx  /media/sda1     vfat    user,noauto,ro,utf8,umask=007,gid=46 0       0
# /dev/sdb1[COLOR="Red"] - My Windows D drive - used to share files between Windows and linux[/COLOR]
UUID=xxxx  /media/sdb1     vfat    user,noauto,rw,utf8,umask=007,gid=46 0       0
# /dev/sdb2 [COLOR="Red"]- Another linux distro[/COLOR]
UUID=xxxx /media/sdb2     ext3    user,noauto,rw,errors=remount-ro        0       0
...

```

The odd thing I noticed with Ubuntu is that even after making these changes, the drives still automounted when I booted.  I then went in and changed 'user' to 'nouser' (so now only root can mount the volumes) and this seems to prevent the automounts from occurring.

I can still go in and 'sudo mount /dev/sdb2' whenever I want access to a volume, and 'sudo umount /dev/sdb2' to unmount it.

I was suprised to see such a difference between gnome and KDE with regard to the user/nouser behavior.  With the noauto option, KDE won't mount a volume even if the access is user, but gnome will.

Am I missing something...

---

### Post by aysiu on 2007-05-04
Yes, the *noauto* should mean it doesn't mount at boot time, at least according to [this page](http://www.tuxfiles.org/linuxhelp/fstab.html). In the meantime, a workaround may be commenting it out of the /etc/fstab file altogether and then creating a shell script for mounting them manually with the proper parameters.

Let me know if you need help with that.

---

### Post by Quicksand on 2007-05-07
I'm having exactly the same problem, I think.  Feisty 64-bit.

I have an NTFS partition and I CAN'T get it to stop automounting, no matter what I put in fstab.  And if I try to unmount from the desktop (right click ->Unmount Volume), I get an error: "Cannot unmount the volume.  umount: /mnt/nativewin mount disagrees with the fstab"

Here are my ntfs-3g options for that partition in fstab: defaults,local=en_US.utf8,umask=007,gid=46,user,noexec,noauto

This is driving me crazy.  I don't want it mounted most of the time, because I access that partition via a virtual machine, and that would without question result in corruption.  So I have to sudo umount after every login.

---

### Post by Nythain on 2007-05-07
couldnt you just remove the entry from fstab all together... then just sudo mount /dev/whatever /wherever  when you want to manually mount it???

---

### Post by TheDoulos on 2007-05-07
> **Quicksand said:**
> 
...
I have an NTFS partition and I CAN'T get it to stop automounting, no matter what I put in fstab.  And if I try to unmount from the desktop (right click ->Unmount Volume), I get an error: "Cannot unmount the volume.  umount: /mnt/nativewin mount disagrees with the fstab"

Here are my ntfs-3g options for that partition in fstab: defaults,local=en_US.utf8,umask=007,gid=46,user,noexec,noauto
...


Try changing 'user' to 'nouser'.  That may keep it from automounting, and you can still mount it manually w/ sudo.

---

### Post by aysiu on 2007-05-07
I would file a bug report on it.
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by TheDoulos on 2007-05-07
It looks like this is either a known issue with the gnome volume manager or the hal volume policy.  [See this bug report.]("https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/17158")  I can't really tell from the developer's comments whether it was ever fixed or whether that's just way g-v-m and hal work.

Since I typically use Kubuntu and this is not an issue with KDE, and since I don't mind editing my Ubuntu fstab to add the nouser option and then doing a sudo mount whenever I want to mount a volume, I'll make do.

I really was just curious to know if it was just something with my setup or whether others have seen this issue.  I've often seen posts that mention putting 'noauto' in the fstab line to keep a volume from being automounted.  It seems that this alone won't work with Ubuntu / gnome, but it does work with Kubuntu / KDE.

---

### Post by Quicksand on 2007-05-13
Well, whaddayaknow.  That fixed it.  Thanks for the tip, TheDoulos.

I don't mind requiring sudo to mount it, either, so I'm reasonably satisfied with this outcome.  But it does sound like a bug, unless there's something going on behind the scenes that I'm not aware of.

---

