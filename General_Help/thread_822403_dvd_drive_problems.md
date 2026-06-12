---
title: "dvd drive problems"
date: 2008-06-08
forum: General Help
---

### Post by bryncoles on 2008-06-08
having issues with random unmounts of the dvd+-rw drive on my packard bell easynote r4360. previously discussed here [http://ge.ubuntuforums.com/showthread.php?t=740129](http://ge.ubuntuforums.com/showthread.php?t=740129). the short and broad of which was the drive seemed to be faulty, and was replaced. now its randomly unmounting again (under hardy). i added to this bug report [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/162474](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/162474), but i want to know why its happening to me, and if i can stop it happening. it'll be very, very irritating if i cant use (or rely upon) my dvd drive on this laptop!

after the drive unmounts, i cant even eject it from the command line or the button on my computer! at least, i cant until i reboot!

any body fancy trying to help me troubleshoot?

```
$ dmesg | tail
[ 2107.478952] VFS: busy inodes on changed media.
[ 2107.479169] cdrom: This disc doesn't have any tracks I recognize!
[ 2107.487505] VFS: busy inodes on changed media.
[ 2107.588181] VFS: busy inodes on changed media.
[ 2107.596281] VFS: busy inodes on changed media.
[ 2107.596490] cdrom: This disc doesn't have any tracks I recognize!
[ 2107.605647] VFS: busy inodes on changed media.
[ 2107.605865] cdrom: This disc doesn't have any tracks I recognize!
[ 2107.688949] VFS: busy inodes on changed media.
[ 2109.141739] VFS: busy inodes on changed media.

```

*edit*

oh yeah, and my laptop has a habit of occasionally unmounting partitions and external hard drives if theres no write-activity to them for a while. they always remount though, the dvd drive will not remount without a restart.

---

### Post by didac on 2008-06-09
Check the power saving settings in your bios. Press DEL or F10 or Backspace, whatever it works in your laptop to access the bios setup

---

### Post by MariusSilverwolf on 2008-06-09
From time to time I get what may be the same issue with my Acer Travelmate 2480.  I think I may have found a semi-viable solution, based on the consistent ease of use I've had over the past few weeks.

See, I came from the old Windows habit of ejecting my just hitting the eject button and letting the OS auto-unmount the disk.  When doing that in Gutsy and Hardy, the next disk would fail to read.  Any attempt to un-mount and re-mount would fail, and I had to restart X, which sometimes still did not work, resulting in me needing to shut down entirely, let the system cool down for a minute, and then powering back up.

What I do now is unmount the disk as soon as I stop using it (ripping, copying files, running a program, etc) and wait until I actively need the disk again before re-inserting.  It's mildly annoying to not be able to let the disk sit idle in the drive, but it's more annoying to have to restart X or reboot when the drive stops responding.

I don't know the root cause, which is bothersome, and I know it's not BIOS power related because the optical drive power settings aren't controlled there, but but my "eject when idle" approach is working for now, and I'll take what I can get.

Hope it helps!

---

### Post by bryncoles on 2008-06-09
hi guys! ill try both those routes. i notice the drive does throw a hissy fit if i just press eject and rely on the auto-unmount. sometimes though it just unmounts while using the dvd - when i posted this thread i had been listening to some mp3's burned onto a dvd when the drive just decided it had had enough!

thanks for the input though guys!

---

### Post by bryncoles on 2008-06-10
darn. all day listening to mp3s on dvds, then at the 11th hour (well, 5:15) the drive unmounts and i get the 

```
dmesg | tail

[27841.750536] VFS: busy inodes on changed media.

```

anyone know what busy inodes means?

---

