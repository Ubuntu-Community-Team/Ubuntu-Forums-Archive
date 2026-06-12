---
title: "Data drive mounts every boot when I do not want it to mount"
date: 2019-05-16
forum: General Help
---

### Post by crazybear on 2019-05-16
I have a large computer with many HDDs. One is the Ubuntu drive, and the others are data drives I do NOT want mounted unless I specifically mount [need] them. However, one always is now mounted - yet is not listed in fstab. I can't figure out how to stop it from automounting. It seems to be seen as a removable drive as the option to 'eject' it is also listed. It is a 2TB HDD, not a thumbdrive. Help would be appreciated. Thanks. The collateral question would be how do I chown a drive so that this doesn't happen again? I thought I did chown the same way as with other similar data drives [which do not mount automatically], but obviously not..... I fairly often format and then chown a new data drive and now I'm not sure how/what options or switches are best for me. If I wanted to have something mount on boot, I'd put it in fstab. the /mnt folder and what that does is a mystery to me. I looked at it and only got confused - it didn't seem to provide any answer to my problem.

---

### Post by Impavidus on 2019-05-16
If the file manager shows the option to eject the drive, it was mounted through the file manager. The file manager shows this option for all filesystems it has mounted, internal or external doesn't matter (and there are also 2TB removable HDDs). It normally does so in /media/username/.

chowning a drive doesn't make sense. You can chown the mountpoint, provided the filesystem supports Unix-style permissions, which has the desired effect. If the filesystem doesn't support Unix-style permissions, you can only change ownership by using the right mount options. Anyway, chown has nothing to do with automounting.

If you put a filesystem in your /etc/fstab with the noauto option, it won't be mounted automatically at boot and the file manager should no longer offer to mount it. The root user can still mount it, and if you add the user option all users can do so.

---

### Post by crazybear on 2019-05-17
There are NO other users. For security reasons only I use this computer ever. All Data Drives are ext4 with no OS. What confuses me are all the different ways to get the 'name/designation' of a disk/partition - from the name I have given it, to the drive letter to the UUID and which to use when. I also thought I had done the same as with other data drives, yet got a totally different result.  All Data drives also have only ONE partition.
I tried a few things but nothing changed. I'll try to add this 'negative' entry in fstab, but none of the other data drives have this and they do not mount. Additional question: does a disk spin up even if not mounted - or only when mounted? If ejected? The reason I don't mount all the data drives is [hopefully] to prolong their life - and in fact I don't need to look inside them very often. Can't seem to find that information. Thanks.

---

### Post by Impavidus on 2019-05-17
There are plenty of other users. Maybe not carbon/water based users mechanically interacting with the keyboard, but silicon based users living inside the computer.

There are basically three ways to refer to a particular partition: device name, label and UUID. Device names (like /dev/sda1) are easy and the classic way, but may change when rebooting a computer with multiple hard drives or when removing/replugging a removable drive. Labels don't change and are easy to memorise, but duplicates are likely. UUIDs are quite robust (although duplicates are not impossible), but hard to memorise. Use the one that's most appropriate for your case.

Maybe you inadvertently used the file manager of some other gui tool to mount the partition automatically?

I guess that most hard drives would at least spin up once after booting the computer, so that the OS (and before that the UEFI/BIOS) can read what partitions are present on that drive. When not used, it may spin down, even when mounted, but may require some configuration to do so. You may be able to find more information concerning this if you search for power saving.

---

### Post by TheFu on 2019-05-17
The jury is out as to whether stopping spinning disks is helpful for lifespan or not. 
I'm firmly in the 'have it spin always' camp, to avoid the stop and start jults on the disk hardware.  Unsure if this helps you, but I have disks that are over 10 yrs old following this exact method which SMART data says have no issues at all.  I go out of my way to change firmware settings in HDDs to prevent sleep modes.

There are a few other ways to safely access partitions in a unique way.  All are under:
```
/dev/disk$ ls
by-id/  by-label/  by-partlabel/  by-partuuid/  by-path/  by-uuid/

```
Your system will have the same directories. If you look inside, you'll see the symbolic links back to the device names.  For systems with lots of disks and multiple HBAs, the by-path/ method is excellent. The names only change when a physical is moved.

BTW, the more disks you have, the more a volume manager like LVM or ZFS makes sense.  Just be certain you have excellent backups regardless.  If the data is worth putting on a $200 HDD, it is worth having backed up, right?

---

### Post by crazybear on 2019-05-18
> **TheFu said:**
> The jury is out as to whether stopping spinning disks is helpful for lifespan or not. 
I'm firmly in the 'have it spin always' camp, to avoid the stop and start jults on the disk hardware.  Unsure if this helps you, but I have disks that are over 10 yrs old following this exact method which SMART data says have no issues at all.  I go out of my way to change firmware settings in HDDs to prevent sleep modes.

There are a few other ways to safely access partitions in a unique way.  All are under:
```
/dev/disk$ ls
by-id/  by-label/  by-partlabel/  by-partuuid/  by-path/  by-uuid/

```
Your system will have the same directories. If you look inside, you'll see the symbolic links back to the device names.  For systems with lots of disks and multiple HBAs, the by-path/ method is excellent. The names only change when a physical is moved.

BTW, the more disks you have, the more a volume manager like LVM or ZFS makes sense.  Just be certain you have excellent backups regardless.  If the data is worth putting on a $200 HDD, it is worth having backed up, right?

Thanks for the thoughts on drive life. I guess the spindle motor these days is rarely the problem, but head crash or something with the arms etc. I buy top-notch and top dollar drives and have lately not had any problems....but just in case, yes, they are backed up. My computer is entirely hot swap and I do change drives around so what is which drive letter changes endlessly...so will never use that method. I have some Ubuntu Gnome manager for drives, but I'll look into the ones you suggested.

---

### Post by crazybear on 2019-05-18
> **Impavidus said:**
> If the file manager shows the option to eject the drive, it was mounted through the file manager. The file manager shows this option for all filesystems it has mounted, internal or external doesn't matter (and there are also 2TB removable HDDs). It normally does so in /media/username/.

chowning a drive doesn't make sense. You can chown the mountpoint, provided the filesystem supports Unix-style permissions, which has the desired effect. If the filesystem doesn't support Unix-style permissions, you can only change ownership by using the right mount options. Anyway, chown has nothing to do with automounting.

If you put a filesystem in your /etc/fstab with the noauto option, it won't be mounted automatically at boot and the file manager should no longer offer to mount it. The root user can still mount it, and if you add the user option all users can do so.

OK, so I found the UUID of the drive and put it into the fstab. I put noauto, but it still mounts and still shows eject as an option. What is wrong - more likely what am I doing or not doing. Need I remove some entry from /mnt and how does one do that? Stranger still, I can open it, BUT NOW I CAN NOT UNMOUNT IT! Was assigning it a mount point the problem? I'm confused.....as often. I've never listed any drives in fstab other than my Ubuntu OS drive and the swap space on that same drive. All other drives are data drives...and maybe I don't know what to put in each of the columns or if to leave them blank...or....

---

### Post by TheFu on 2019-05-18
Linux doesn't have drive letters. No idea what you are describing there.
There is an option for gvfs to hide partitions from GUIs.  I don't use GUIs to mount storage, so I have no idea what it is.  The gvfs documentation might have that info.  Google found this: [https://askubuntu.com/questions/122783/how-do-i-hide-remove-a-partition-from-the-nautilus-left-panel](https://askubuntu.com/questions/122783/how-do-i-hide-remove-a-partition-from-the-nautilus-left-panel)  I've never used it.  "gvfs options hide" was the search terms.  Obviously, if you don't know about gvfs, you'd never find it. ;(

---

### Post by Morbius1 on 2019-05-18
If I might make a suggestion. Why not post the output of the following commands so the folks here can work with something definable:

```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```

---

### Post by crazybear on 2019-05-19
$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/sda1: LABEL="XXXXX" UUID="5658d31c-d367-4eec-9c41-99d79307e8cC" TYPE="ext4" PTTYPE="dos" PARTUUID="70405148-02"
/dev/sda2: LABEL="16.04swap" UUID="7da95bc8-ab6d-4d3a-a7eb-510e06b50378" TYPE="swap" PARTUUID="70405148-03"
[COLOR=#0000ff]/dev/sdb1: LABEL="YYYYY" UUID="e262cf2d-7816-4b40-b24b-72aa05c02d83" TYPE="ext4" PARTUUID="5eb201c3-02"[/COLOR]
/dev/sdc1: LABEL="ZZZZZ" UUID="9b1d11ca-7255-4645-adb9-5c9a915dcbc1" TYPE="ext4" PARTUUID="80269eb9-2c1c-4f1a-86f8-ba7d987bf8fe"
/dev/sdd1: LABEL="AAAAA" UUID="0d8be9c9-49bb-558e-8633-5a5ebe6deab6" TYPE="ext4" PARTUUID="0c73caa7-4864-4666-ad53-681227926a65"

$ cat /etc/fstab
# <file system>                  <mount point>           <type>    <options>    <dump>  <pass>
UUID=5658d31c-d367-4eec-9c41-99d79307e8cC /           ext4    relatime,rw     0       1
UUID=7da95bc8-ab6d-4d3a-a7eb-510e06b50378      none        swap    sw              0       0
[COLOR=#0000ff]UUID=e262cf2d-7816-4b40-b24b-72aa05c02d83 /media/YYYYY ext4       noauto       0       1[/COLOR]

$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=12243368k,nr_inodes=3060842,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=2454916k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,stripe=32750,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma,release_agent=/run/cgmanager/agents/cgm-release-agent.rdma)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=24230)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/var/lib/snapd/snaps/shotcut_45.snap on /snap/shotcut/45 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_6673.snap on /snap/core/6673 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/shotcut_43.snap on /snap/shotcut/43 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_6818.snap on /snap/core/6818 type squashfs (ro,nodev,relatime)
[COLOR=#0000ff]/dev/sdb1 on /media/YYYYY type ext4 (rw,relatime,data=ordered)[/COLOR]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/125 type tmpfs (rw,nosuid,nodev,relatime,size=2454916k,mode=700,uid=125,gid=136)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=2454916k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)

---

### Post by crazybear on 2019-05-19
> **TheFu said:**
> Linux doesn't have drive letters. No idea what you are describing there.
There is an option for gvfs to hide partitions from GUIs.  I don't use GUIs to mount storage, so I have no idea what it is.  The gvfs documentation might have that info.  Google found this: [https://askubuntu.com/questions/122783/how-do-i-hide-remove-a-partition-from-the-nautilus-left-panel](https://askubuntu.com/questions/122783/how-do-i-hide-remove-a-partition-from-the-nautilus-left-panel)  I've never used it.  "gvfs options hide" was the search terms.  Obviously, if you don't know about gvfs, you'd never find it. ;(

I meant sd(*x*) as 'drive letter'
don't use nor understand gvfs or hiding partitions - or why one would even want to ever do that.....

---

### Post by dino99 on 2019-05-19
you said using 'hot swap' devices, but your fstab use uuid :o

every time you plug/unplug a device, a new uuid is generated, but fstab will ignore it

---

### Post by crazybear on 2019-05-19
> **dino99 said:**
> you said using 'hot swap' devices, but your fstab use uuid :o

every time you plug/unplug a device, a new uuid is generated, but fstab will ignore it

With a HDD? Really? I never heard that. I thought the UUID stayed with the HDD until reformatted! Is this true? If so, why would anyone ever use a UUID to identify a disk in fstab or any other place in the computer. In fact, I think I have proof the above it not true. I clone [using clonezilla] drives to 'archive' them...but if I have the two [original and clone] in the hot swap bays at the same time, it will not 'see' the last one put in....I always assumed because it saw the exact same UUID. A quick check on internet did not confirm your claim, but I might not have used proper search terms. While I usually remove the drives when the computer is off, I do sometimes put in a disk when it is on. In this case, I neither removed nor put in the drive in question when the computer was on. I can see clearly that the noauto is in the fstab but comes up without it after the mount command. The blue lines are the drive in question.

---

### Post by TheFu on 2019-05-19
> **crazybear said:**
> I meant sd(*x*) as 'drive letter'
don't use nor understand gvfs or hiding partitions - or why one would even want to ever do that.....

Ah - my mistake.  I was thinking "Windows" C:, D:, E:, .... and that had me thinking NTFS or exFAT and all sorts of other mount considerations.  Thanks for the clarification.  See how 1 little thing, misinterpreted wildly changes the responses?  No error by either of us. 100% honest communications issue.

gvfs is used by GUI tools like nautilus, caja, thunar ... to provide easier access to local and remote storage, so that mounting it via /etc/fstab isn't required.  As for the hiding - it only hides partitions to the GUI tools, since people don't want to see some of their storage there or have it with an eject button. At least I think that is the reason.

I carefully re-read your OP (original post) where you asked about the /mnt folder.  It is really simple.  According to the _Linux File System Hierarchy standards_, which all major Linux distros follow, /mnt is a temporary directory to be used by system admins for mounting storage for temporary use.  That's it. You can google, if you like. The wikipedia article has a good table and that's really all most people need - 15 seconds skimming that is highly useful. You'll see people choose to mount all sorts of stuff under their because it became habit or they saw a trained admin to it.  I use it for temporary storage, things that mounted less than 8 hrs.  Old backup scripts would specifically exclude this area from backups.  Locate DBs (updatedb) can ignore it too.  

I don't think a new UUID is created just by disconnecting a partition. That isn't something I've seen.
I swap drives daily, while the system is running. I simply make certain all the partitions on it are not mounted. For portable devices, I use autofs to handle the mounts.  After some period of not being used and prior to the first access request, the partitions aren't actually mounted.  By default they don't show up on the real file system anywhere until accessed.  There is an option to force a "ghost" directory for the partition to be displayed, which is helpful for GUI programs, since they can't access a directory that isn't there to be clicked.

I'll try to take some time to go through the rest of the posts to see what I can gleam that might be helpful.

I see the  _noauto_ option in the fstab. I don't use that because I use autofs for those disks. Hummmm. The fstab manpage says:
```
              noauto do not mount when "mount -a"  is  given  (e.g.,  at  boot time)
```
and nothing else about it.  There was a bug, long, long, ago about that option being ignored. [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/120829](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/120829) that was traced back to some Gnome settings.
> Well, I have finally found the problem... It very simply involves the single setting [system>preferences>removable drives and media>storage>mount removable media when inserted]. Deselecting this makes noauto work as usual. I also managed to remove the desktop drive icons; open terminal and type "gconf-editor" and deselect [/apps/nautilus/desktop/volumes_visible].
That's from 2007, so if it is related, it would be something to check in the GUI and gconf.

---

### Post by mc4man on 2019-05-19
I've only one additional internal drive, when mounted thru file manager it only gets an unmount option, never eject which is only seen on removable/external devices
When you mount any of your other drives what option is presented?

For  comparative info you could remove that fstab entry, reboot, mount some or all your drives and run this
```
mount |grep /dev/sd
```

Have you tried swapping internal connections with one of your other drives with the misbehaving one?

---

### Post by Morbius1 on 2019-05-19
> **mc4man said:**
> I've only one additional internal drive, when mounted thru file manager it only gets an unmount option, never eject which is only seen on removable/external devices
What's complicating this topic - I think - is that the drive in question in not an internal one. The OP mentions this in passing:
> My computer is entirely hot swap and I do change drives around so what  is which drive letter changes endlessly...so will never use that method.
Never used anything like that myself so I don't know how Linux handles them. As just another partition as if it was an internal one or more like USB.

Maybe TheFu's idea is the solution - dconf-editor:
[ATTACH=CONFIG]283281[/ATTACH]
It's easily reversed if not the solution.

---

### Post by crazybear on 2019-05-20
> **Morbius1 said:**
> What's complicating this topic - I think - is that the drive in question in not an internal one. The OP mentions this in passing:

Never used anything like that myself so I don't know how Linux handles them. As just another partition as if it was an internal one or more like USB.

Maybe TheFu's idea is the solution - dconf-editor:
[ATTACH=CONFIG]283281[/ATTACH]
It's easily reversed if not the solution.

Your interpretation of my statements is dead wrong. I have no external drives. All are in a huge desktop with three hot swap bays for four drives each.

---

### Post by crazybear on 2019-05-20
Look, folks, thanks for all the suggestions, but nothing so far suggested has worked. I think some replies were incomplete or assumed I'd 'know what to do about the obviously missing details', when I did not. My best guess [and only that] is that what I put in fstab is countermanded by /mnt and no one has told me how to remove anything from /mnt. When I had noauto for this drive in fstab, it showed that /mnt was telling it relatime and for reasons I don't know, that took president. I also tried  a program [storage device manager] and that too did not put into effect what I asked it to do...so all of these different areas must have a heirarchy and I don't know what it is. I was asked what other [well behaved] data disks had as options - the answer is to mount/unmount and open/close - no 'eject' is listed. I wouldn't even mind the eject, but it seems to come with automatic loading on boot..... No one has mentioned about rw being  or not being in fstab and what the two last columns with 0 or 1 in them means and should be set at for a data disk. Lastly, there are many ways to state a mount point and I sense this too could be part or all of the problem. With all of this messing around now two data disks show as thumbdrives and have the eject option - and mount on boot...so at the moment things are getting worse. One problem disk is now two. Frustrating.

---

### Post by TheFu on 2019-05-20
At this point, I'm not sure that anything I've written has been helpful or just confusing. I'll try on some simple things:

The fstab has a manpage.  It is pretty good at explaining what each column means.  The last two columns included.  **man fstab** will access it.

I'm confused by the use of "/mnt" in the last post.  That is just a directory the way we use it.  It is not an abbreviation for spelling out "mount".

---

### Post by rbmorse on 2019-05-20
I got confused long before TheFu did.  

How do your hotswap bays interface to the motherboard?

---

### Post by crazybear on 2019-05-22
> **rbmorse said:**
> I got confused long before TheFu did.  

How do your hotswap bays interface to the motherboard?

I don't think this is the problem. In fact, I'm sure it is not. They are not new. When I built the computer, I put in the hot swap bays. They simply allow for a drive to be inserted or removed while the computer is on. They have a standard cable to the MB, which has the capability for many drives to be connected. BIOS is set up to be happy with the arrangement and in fact it has been until recently. I have used this set up for many years and never had this problem before. Recently I decided to make my OS drive smaller, and had to move data to a new data drive - and this happened when I chown'd the drive. Was there a switch I needed to add at the end of the chown line that did this? I have no idea how to remove or change lines in the mnt file - there IS an entry for this drive and I did not put it in.

The fstab manpage seems to indicate I set it up correctly when I did have an entry [now #-out]. At the moment there is no entry for the drive. Either way it mounts. Something else is telling it to mount and be mounted in such a way I can not unmount it......

Very strange and annoying.

---

### Post by Morbius1 on 2019-05-22
Wow.

Some of these questions have been asked before by others but I'll ask them again.
> **crazybear said:**
>  I have no idea how to remove or change lines in the mnt file - there IS an entry for this drive and I did not put it in.
[1] What is this [COLOR=#0000cd]**mnt**[/COLOR] file you speak of? Are you talking about /etc/fstab?

[2] If it is not fstab can you tell us the path to and the contents of this mnt file?
>  The fstab manpage seems to indicate I set it up correctly when I did have an entry [now #-out]. At the moment there is no entry for the drive. Either way it mounts. 
With no entry for this "drive" ( partition ) where does it mount? Is it at /media/your-username/XXX?
> Something else is telling it to mount and be mounted in such a way [COLOR=#0000cd]**I can not unmount it**[/COLOR]...... 
[3] OK, um ... I think that's a new symptom or did you mention this before?

[4] And just to be clear did you install dconf-editor and set the "use default value" to off as I suggested above? Or did you just assume it wouldn't work because ... um ... of my typo where I used the word "external"  when I meant to say hot-swapable ?

---

### Post by crazybear on 2019-05-25
> **Morbius1 said:**
> Wow.

Some of these questions have been asked before by others but I'll ask them again.

[1] What is this [COLOR=#0000cd]**mnt**[/COLOR] file you speak of? Are you talking about /etc/fstab?

[2] If it is not fstab can you tell us the path to and the contents of this mnt file?

With no entry for this "drive" ( partition ) where does it mount? Is it at /media/your-username/XXX?

[3] OK, um ... I think that's a new symptom or did you mention this before?

[4] And just to be clear did you install dconf-editor and set the "use default value" to off as I suggested above? Or did you just assume it wouldn't work because ... um ... of my typo where I used the word "external"  when I meant to say hot-swapable ?

Sorry for the delay...for some reason no email was sent to me to inform me of a new reply. I was just coming here to ask for help again, as I'm not making any progress. The 'mnt' I'm talking about is /mnt folder which I have never knowingly done anything with, but I see there is a folder for the drive giving me a problem, when I try to delete it, I'm told I don't have permission to do so - and I don't know the command language to do so or its effect.

Whenever the drive is listed in fstab NO MATTER how it is listed [as far as I can tell - noauto or relatime - but I want noauto!], then it mounts and CAN NOT BE UNMOUNTED at all, ever. So, yes that is new and I've tried several variations in fstab. I have also used a program called Storage Device Manager that puts very strange [to me] entries into fstab. Again, I have tried many variations, but none work. I suspect the entry  in /mnt is the problem. I do not know how it was created nor how to remove it.

It mounts at /media/correct-disk-name

I just looked at the reply in terminal to mount command and it is listed as relatime, but I typed in noauto in fstab?!?!..... My computer has ghosts and obviously various programs are doing different things. Another data drive I rarely use also shows up with the eject option and automatically mounts - even though there is NO entry for it in fstab. However, as annoying as that one is, I can unmount it. I still think it was how I chown(ed) these two was not proper for what I wanted, and that somehow caused entries in /mnt - but how do I remove those entries or correctly (re)chown the drives?

I can't get a clear idea of what deconf-editor is or if it has another name and is already in my 16.04.3. Why would I want it and what advantage would it be? No, I do not remember adding it but that doesn't mean it is not there under some other name. Please know [since some entries on deconf-editor refer to Unity] I do not use unity and dislike it with a passion. I have a Ubuntu Gnome version of 16.04.3. I finally found it on the internet to download and open in package manager and package manager tells me it is installed but not where nor under what name. Further investigation seems to indicate it is installed but not working as it conflicts with Gnome. I need to know what something is, what it does and if it will conflict with my system before I mess with it or even install it. It is installed, but apparently not working due to some conflicts. Package manager says it can re-install but only if it removes Gnome desktop - my most important program...no way! I did find it in Synaptic and version 3.18.2-1 is installed and the latest version..but how does one invoke it?

---

### Post by mc4man on 2019-05-26
If you list the drive in fstab it'll be auto mounted by root so to un-mount you need to do so as root.

Based on your orig. post it leads to these orig. assumptions
1. Orig. none of the data drives are  in fstab.
2. One drive out of all of them  automounted, the rest don't.

 Are the above true true to the orig. issue? If so then maybe consider , if not ignore below- 

In default Ubuntu/Gnome there are 2 ways a volume would be auto mounted. 
Either at boot thru an fstab entry or at boot/login if the block device is detected as and set  'removable'

A small section of the kernel code seems to  suggests  how scsi drives are set,  i.e
> /* set scsi removable (RMB) bit per ata bit, or if the
	 * AHCI port says it's external (Hotplug-capable, eSATA).
	 */

You can check the removable attribute of any block device in /sys/block/sd*/removable, a value of 0 represents removable=no, 1 represents removable=yes
Ex. /dev/sdc
```
cat /sys/block/sdc/removable
```
or use udevadm to ck. attributes of your device(s)

full info, ex. /dev/sdc - 
```
udevadm info -a -n /dev/sdc
```
or to ck. just the removable attribute
```
udevadm info -a -n /dev/sda1 |grep removable
```

So compare devices that don't automount vs. the problem one(s)

---

### Post by crazybear on 2019-05-27
> **mc4man said:**
> If you list the drive in fstab it'll be auto mounted by root so to un-mount you need to do so as root.

Based on your orig. post it leads to these orig. assumptions
1. Orig. none of the data drives are  in fstab.
2. One drive out of all of them  automounted, the rest don't.

 Are the above true true to the orig. issue? If so then maybe consider , if not ignore below- 

In default Ubuntu/Gnome there are 2 ways a volume would be auto mounted. 
Either at boot thru an fstab entry or at boot/login if the block device is detected as and set  'removable'

A small section of the kernel code seems to  suggests  how scsi drives are set,  i.e


You can check the removable attribute of any block device in /sys/block/sd*/removable, a value of 0 represents removable=no, 1 represents removable=yes
Ex. /dev/sdc
```
cat /sys/block/sdc/removable
```
or use udevadm to ck. attributes of your device(s)

full info, ex. /dev/sdc - 
```
udevadm info -a -n /dev/sdc
```
or to ck. just the removable attribute
```
udevadm info -a -n /dev/sda1 |grep removable
```

So compare devices that don't automount vs. the problem one(s)

Yes, originally no data drives were in fstab and there were no problems. Now two are a problem and the present slightly differently as problems. One can be unmounted, the other I can not find any way to unmount!

Those commands you gave a fine, but what do I do to correct the drives listed incorrectly? Why did my earlier [and still used] data drives not misbehave and the two latest not behave...one really being crazy in that it can never be unmounted - even though and option to unmount and eject shows...but does not effect those events?!?!?

---

### Post by mc4man on 2019-05-27
> **crazybear said:**
> Yes, originally no data drives were in fstab and there were no problems. Now two are a problem and the present slightly differently as problems. One can be unmounted, the other I can not find any way to unmount!

Those commands you gave a fine, but what do I do to correct the drives listed incorrectly? Why did my earlier [and still used] data drives not misbehave and the two latest not behave...one really being crazy in that it can never be unmounted - even though and option to unmount and eject shows...but does not effect those events?!?!?

The whole point of above commands was to see if  'good' drives have attribute removable 0 and the 'bad' drives removable 1. If so then see if there is a way to alter that attribute, maybe thru a udev rule??
"a(re) fine" means nothing to me...

---

### Post by crazybear on 2019-05-28
$ udevadm info -a -n /dev/sda1 |grep removable
    ATTRS{removable}=="0"
$ udevadm info -a -n /dev/sdb1 |grep removable
    ATTRS{removable}=="0"
$ udevadm info -a -n /dev/sdc1 |grep removable
    ATTRS{removable}=="1"
$ udevadm info -a -n /dev/sdd1 |grep removable
    ATTRS{removable}=="0"
$ udevadm info -a -n /dev/sde1 |grep removable
    ATTRS{removable}=="0"
sda = OK data drive [no problems, not listed in fstab ever nor in /mnt]
sdb = OS drive and swap file [sdb2]
sdc = Data drive that gets mounted, though not listed in fstab, but can be unmounted
sdd = Data drive that doesn't get mounted, but can be and can also be unmounted
sde = Data drive that can not be unmounted

---

### Post by mc4man on 2019-05-31
Well /dev/sdc shows the removable attribute 1 (true) so that's why it's automounted and why it gets the eject option.
How to change this, i.e edit the attributes of a block device?, not sure. (I suspect the initial info comes from the kernel, then udisks2 (udev) acts on it.

A quick search didn't show anything short of recompiling the kernel but did see this page on the archlinux wiki. There is a section near bottom on the page concerning the opposite of your issue. Maybe try the solution but use the opposite values. Shouldn't cause any harm to try. 
[https://wiki.archlinux.org/index.php/Udev](https://wiki.archlinux.org/index.php/Udev)

Example in screen 2 of the created rule using the short id and opposite values as in the wiki.. Create file, reboot, see..

---

### Post by crazybear on 2019-06-04
> **mc4man said:**
> Well /dev/sdc shows the removable attribute 1 (true) so that's why it's automounted and why it gets the eject option.
How to change this, i.e edit the attributes of a block device?, not sure. (I suspect the initial info comes from the kernel, then udisks2 (udev) acts on it.

A quick search didn't show anything short of recompiling the kernel but did see this page on the archlinux wiki. There is a section near bottom on the page concerning the opposite of your issue. Maybe try the solution but use the opposite values. Shouldn't cause any harm to try. 
[https://wiki.archlinux.org/index.php/Udev](https://wiki.archlinux.org/index.php/Udev)

Example in screen 2 of the created rule using the short id and opposite values as in the wiki.. Create file, reboot, see..

Thanks, but sorry, my /etc/udev/rules.d contains NOTHING related to disks [only other things like printers, etc.]!....... and I don't see where creating one would not just make things more complex. Obviously something else somewhere is telling [against my will and planning] which drives to mount and which not to. Even my disk mount program when 'set correctly' doesn't do the thing I set them to do [the disks]. There are also many lines of caution to not use udev or udisk for drives....which are not very clear - but enough to make me stay away from this. Your suggestion ignores the most problematic disk sde which has attribute 0.

---

### Post by mc4man on 2019-06-05
> **crazybear said:**
> Thanks, but sorry, my /etc/udev/rules.d contains NOTHING related to disks [only other things like printers, etc.]!....... and I don't see where creating one would not just make things more complex. Obviously something else somewhere is telling [against my will and planning] which drives to mount and which not to. Even my disk mount program when 'set correctly' doesn't do the thing I set them to do [the disks]. There are also many lines of caution to not use udev or udisk for drives....which are not very clear - but enough to make me stay away from this. Your suggestion ignores the most problematic disk sde which has attribute 0.

I never suggested using udev to mount a drive, only to change one of it's attributes (dev/sdc
As far as /dev/sde, that was not part of your orig. issue so you caused it's current behavior. It's likely mounted by root, that's why you can't unmount it.  Why? maybe an fstab entry or something else you did, at this point don't know.
Good luck..

---

### Post by crazybear on 2019-06-09
> **mc4man said:**
> I never suggested using udev to mount a drive, only to change one of it's attributes (dev/sdc
As far as /dev/sde, that was not part of your orig. issue so you caused it's current behavior. It's likely mounted by root, that's why you can't unmount it.  Why? maybe an fstab entry or something else you did, at this point don't know.
Good luck..


When one has hot swap, the letter [sd***X***] can change and I don't use them formally. They only work for a fixed system. I use names I give the drive and sometimes the UUID - which don't change. What is now sde was always the original problem drive even it the letter after sd changed - that just means I put it in a different swap bay. Now neither it nor the other drive that mounts [but can be removed] are listed in fstab. In fstab are only listed the two partitions of the OS drive. Whenever I put an entry for a drive in fstab, even if I put noauto, it mounts and can not be unmounted...very strange and I'm sort of without a solution. There has to be something somewhere overriding this.

---

