---
title: "Gusty Locks Up (32bit)"
date: 2008-01-04
forum: General Help
---

### Post by HDave on 2008-01-04
For the part couple months, I've been having this problem with Gusty locking up every couple of hours during heavy use.  I am running a Dell XPS M1210 laptop with a core 2 duo in it and an nVidia GeForce Go 7400 graphics card.

By locking up, I mean:

1) screen just freezes
2) unresponsive to mouse & keyboard
3) ctrl-alt-backspace, f1, f2, etc. - nothing happens.
4) I am forced to hit the power button to restart

I am always using it at the times when this happens (i.e. this is not the screensaver problem, which I have encountered).  FYI -- The system has never locked up when it is just "sitting there."  I am typically running:

compiz-fusion
VMWare (not in full-screen mode)
Pidgin
Firefox
Rythymbox
Openoffice
Thunderbird
[edit] Conky

Any help on diagnosis is much appreciated!!

---

### Post by markharding557 on 2008-01-04
your're going to have to do a little watching
first try running without compiz to see if it still freezes and then if it does work your way down the list.
compiz or vmware are likely culprits,you can observe how things are running using system monitor watch how much memory and cpu they are using,if a process locks cpu at 100% this can cause lockups
finally check your cpu temp under load,this can cause freezing too

---

### Post by cheahk on 2008-01-04
Does this happen with the AC on?  Maybe the power stepping has something to do with it on battery mode.

-K

---

### Post by HDave on 2008-01-04
It is happening with the AC on -- haven't run my laptop on batteries much in a while.

This coming week, I'll try running some experiments and report back.  I'll start by turning off compiz as it is the least important...painful as it will be to work without rotating the cube!!!  :-(

---

### Post by anthonyJC on 2008-01-05
Your software list was useful, TY for the effort put into providing.
Don't hit the reset button : hold down alt and prtscn and while these are held down type RSEIUB. It will then flush the disc write cache - hitting reset means you don't get to find out the cause in syslog.

My only suggested resolution is disabling ACPI with a kernel switch.  I suggest using Wine instead of Vmware because it doesn't taint.  Use the OSS Nvidia driver ( nv / Nouveau ) instead of the proprietory blob because it does'nt taint.

---

### Post by HDave on 2008-01-07
Thanks for the great tip on the alt-prtscr R S E I U B  -- thats way cool.  I tested it prior to locking up just make sure it works and it did.

However, when I locked-up today, it had no effect.  Nonetheless here is my log from right after booting to right after the freeze.  The only test I ran today was leaving out rhythmbox.  Will try turning of compiz tomorrow.  :(

```
Jan  7 14:38:28 dwv-linux ntfs-3g[6929]: Version 1.913 
Jan  7 14:38:28 dwv-linux ntfs-3g[6929]: Mounted /dev/mapper/truecrypt1 (Read-Write, label "", NTFS 3.1) 
Jan  7 14:38:28 dwv-linux ntfs-3g[6929]: Cmdline options: rw,uid=1000,gid=1000,umask=077 
Jan  7 14:38:28 dwv-linux ntfs-3g[6929]: Mount options: noatime,rw,silent,allow_other,nonempty,default_permissions,fsname=/dev/mapper/truecrypt1,blkdev,blksize=4096 
Jan  7 14:38:41 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 31 C
Jan  7 14:39:03 dwv-linux ntfs-3g[6972]: Version 1.913 
Jan  7 14:39:03 dwv-linux ntfs-3g[6972]: Mounted /dev/mapper/truecrypt2 (Read-Write, label "", NTFS 3.1) 
Jan  7 14:39:03 dwv-linux ntfs-3g[6972]: Cmdline options: rw,uid=1000,gid=1000,umask=077 
Jan  7 14:39:03 dwv-linux ntfs-3g[6972]: Mount options: noatime,rw,silent,allow_other,nonempty,default_permissions,fsname=/dev/mapper/truecrypt2,blkdev,blksize=4096 
Jan  7 14:43:41 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 33 C
Jan  7 14:47:03 dwv-linux kernel: [  821.356000] /dev/vmmon[7559]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
Jan  7 14:47:03 dwv-linux last message repeated 70 times
Jan  7 14:47:03 dwv-linux kernel: [  821.360000] /dev/vmmon[7559]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
Jan  7 14:47:03 dwv-linux last message repeated 9 times
Jan  7 14:47:05 dwv-linux kernel: [  823.336000] /dev/vmnet: open called by PID 7559 (vmware-vmx)
Jan  7 14:47:05 dwv-linux kernel: [  823.336000] device eth1 entered promiscuous mode
Jan  7 14:47:05 dwv-linux kernel: [  823.336000] audit(1199735225.530:4): dev=eth1 prom=256 old_prom=0 auid=4294967295
Jan  7 14:47:05 dwv-linux kernel: [  823.336000] bridge-eth1: enabled promiscuous mode
Jan  7 14:47:05 dwv-linux kernel: [  823.336000] /dev/vmnet: port on hub 3 successfully opened
Jan  7 14:47:05 dwv-linux kernel: [  823.384000] /dev/vmmon[7562]: host clock rate change request 0 -> 19
Jan  7 14:47:08 dwv-linux kernel: [  825.908000] /dev/vmmon[7562]: host clock rate change request 19 -> 83
Jan  7 14:47:21 dwv-linux kernel: [  838.944000] device eth1 left promiscuous mode
Jan  7 14:47:21 dwv-linux kernel: [  838.944000] audit(1199735241.031:5): dev=eth1 prom=0 old_prom=256 auid=4294967295
Jan  7 14:47:21 dwv-linux kernel: [  838.944000] bridge-eth1: disabled promiscuous mode
Jan  7 14:47:21 dwv-linux kernel: [  838.944000] /dev/vmnet: open called by PID 7562 (vmware-vmx)
Jan  7 14:47:21 dwv-linux kernel: [  838.944000] device eth1 entered promiscuous mode
Jan  7 14:47:21 dwv-linux kernel: [  838.944000] audit(1199735241.031:6): dev=eth1 prom=256 old_prom=0 auid=4294967295
Jan  7 14:47:21 dwv-linux kernel: [  838.944000] bridge-eth1: enabled promiscuous mode
Jan  7 14:47:21 dwv-linux kernel: [  838.944000] /dev/vmnet: port on hub 3 successfully opened
Jan  7 14:48:41 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 35 C
Jan  7 14:53:41 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 37 C
Jan  7 14:58:41 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 38 C
Jan  7 15:03:35 dwv-linux kernel: [ 1813.316000] device eth1 left promiscuous mode
Jan  7 15:03:35 dwv-linux kernel: [ 1813.316000] audit(1199736215.587:7): dev=eth1 prom=0 old_prom=256 auid=4294967295
Jan  7 15:03:35 dwv-linux kernel: [ 1813.316000] bridge-eth1: disabled promiscuous mode
Jan  7 15:03:35 dwv-linux kernel: [ 1813.316000] /dev/vmnet: open called by PID 7562 (vmware-vmx)
Jan  7 15:03:35 dwv-linux kernel: [ 1813.316000] device eth1 entered promiscuous mode
Jan  7 15:03:35 dwv-linux kernel: [ 1813.316000] audit(1199736215.587:8): dev=eth1 prom=256 old_prom=0 auid=4294967295
Jan  7 15:03:35 dwv-linux kernel: [ 1813.316000] bridge-eth1: enabled promiscuous mode
Jan  7 15:03:35 dwv-linux kernel: [ 1813.316000] /dev/vmnet: port on hub 3 successfully opened
Jan  7 15:03:36 dwv-linux kernel: [ 1814.048000] /dev/vmmon[7562]: host clock rate change request 83 -> 19
Jan  7 15:03:36 dwv-linux kernel: [ 1814.056000] /dev/vmmon[7562]: host clock rate change request 19 -> 1
Jan  7 15:03:36 dwv-linux kernel: [ 1814.056000] /dev/vmmon[7562]: host clock rate change request 1 -> 19
Jan  7 15:03:38 dwv-linux kernel: [ 1815.688000] /dev/vmmon[7562]: host clock rate change request 19 -> 83
Jan  7 15:03:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 39 C
Jan  7 15:03:46 dwv-linux kernel: [ 1824.052000] device eth1 left promiscuous mode
Jan  7 15:03:46 dwv-linux kernel: [ 1824.052000] audit(1199736226.087:9): dev=eth1 prom=0 old_prom=256 auid=4294967295
Jan  7 15:03:46 dwv-linux kernel: [ 1824.052000] bridge-eth1: disabled promiscuous mode
Jan  7 15:03:46 dwv-linux kernel: [ 1824.052000] /dev/vmnet: open called by PID 7562 (vmware-vmx)
Jan  7 15:03:46 dwv-linux kernel: [ 1824.052000] device eth1 entered promiscuous mode
Jan  7 15:03:46 dwv-linux kernel: [ 1824.052000] audit(1199736226.087:10): dev=eth1 prom=256 old_prom=0 auid=4294967295
Jan  7 15:03:46 dwv-linux kernel: [ 1824.052000] bridge-eth1: enabled promiscuous mode
Jan  7 15:03:46 dwv-linux kernel: [ 1824.052000] /dev/vmnet: port on hub 3 successfully opened
Jan  7 15:08:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 15:13:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 15:17:01 dwv-linux /USR/SBIN/CRON[9333]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  7 15:18:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 15:23:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 15:28:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 15:33:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 15:38:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 15:43:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 39 C
Jan  7 15:48:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 39 C
Jan  7 15:53:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 15:58:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 16:03:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 39 C
Jan  7 16:08:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 16:13:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 16:17:01 dwv-linux /USR/SBIN/CRON[13027]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  7 16:18:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 16:23:42 dwv-linux hddtemp[5586]: /dev/sda: Hitachi HTS722020K9SA00: 40 C
Jan  7 16:25:32 dwv-linux syslogd 1.4.1#21ubuntu3: restart.
```

---

### Post by HDave on 2008-01-08
Turned off compiz fusion and just spend all day with vmware, pidgin, rhythmbox, open office, etc. and no lock ups. This hasn't happened ever. The system even *feels* more stable.

So its no more compiz for me...but I am very happy with the new found stability. Hopefully will get better in Hardy.

---

### Post by chadjohnson on 2008-02-11
When this was happening for you, did you notice whether your CPU was at 100% usage (either in the System Monitor or in top output)?

---

