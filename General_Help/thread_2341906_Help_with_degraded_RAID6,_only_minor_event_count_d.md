---
title: "Help with degraded RAID6, only minor event count diffs but does not force assemble"
date: 2016-11-02
forum: General Help
---

### Post by jgrevich on 2016-11-02
A few drives were accidentally removed while upgrading one of my servers. After reboot, all drives in that array are marked as spares and a few have event counts that are off by 2:

```
md127 : inactive sdm1[2](S) sdj1[3](S) sdg1[4](S) sdi1[8](S) sdf1[1](S) sdl1[0](S) sdh1[9](S) sdk1[6](S) sdc1[5](S) sde1[10](S) sdd1[7](S)
[COLOR=#F5F5F5][FONT=Monaco]     64464288768 blocks super 1.2[/FONT][/COLOR]
```

```
oot@jn:~# grep Event raid.status.last 
         Events : 28051
         Events : 28051
         Events : 28051
         Events : 28051
         Events : 28051
         Events : 28049
         Events : 28049
         Events : 28051
         Events : 28049
         Events : 28051
[FONT=Monaco]Event[/FONT][COLOR=#F5F5F5][FONT=Monaco]s : 28051[/FONT][/COLOR]
```

I followed the guide here [https://raid.wiki.kernel.org/index.php/RAID_Recovery](https://raid.wiki.kernel.org/index.php/RAID_Recovery) and tried to force-assemble the array using the order reported from check `mdadm -E /dev/sd#` on each device. However it fails stating that there are not enough drives to start the array.

```
~# mdadm -v --assemble --force /dev/md127 /dev/sdl1 /dev/sdf1 /dev/sdm1 /dev/sdj1 /dev/sdg1 /dev/sdc1 /dev/sdk1 /dev/sdd1 /dev/sdi1 /dev/sdh1 /dev/sde1
mdadm: looking for devices for /dev/md127
mdadm: /dev/sdl1 is identified as a member of /dev/md127, slot 0.
mdadm: /dev/sdf1 is identified as a member of /dev/md127, slot 1.
mdadm: /dev/sdm1 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdj1 is identified as a member of /dev/md127, slot 3.
mdadm: /dev/sdg1 is identified as a member of /dev/md127, slot 4.
mdadm: /dev/sdc1 is identified as a member of /dev/md127, slot 5.
mdadm: /dev/sdk1 is identified as a member of /dev/md127, slot 6.
mdadm: /dev/sdd1 is identified as a member of /dev/md127, slot 9.
mdadm: /dev/sdi1 is identified as a member of /dev/md127, slot 8.
mdadm: /dev/sdh1 is identified as a member of /dev/md127, slot 7.
mdadm: /dev/sde1 is identified as a member of /dev/md127, slot 10.
mdadm: added /dev/sdf1 to /dev/md127 as 1
mdadm: added /dev/sdm1 to /dev/md127 as 2
mdadm: added /dev/sdj1 to /dev/md127 as 3
mdadm: added /dev/sdg1 to /dev/md127 as 4
mdadm: added /dev/sdc1 to /dev/md127 as 5
mdadm: added /dev/sdk1 to /dev/md127 as 6 (possibly out of date)
mdadm: added /dev/sdh1 to /dev/md127 as 7 (possibly out of date)
mdadm: added /dev/sdi1 to /dev/md127 as 8 (possibly out of date)
mdadm: added /dev/sdd1 to /dev/md127 as 9
mdadm: added /dev/sde1 to /dev/md127 as 10
mdadm: added /dev/sdl1 to /dev/md127 as 0
[FONT=Monaco]mdadm: /dev/md127 assembled from 8 drives - not enough to start the array.[/FONT]
```

I'm reluctant to proceed with restoring the array by recreating without looking into this further since that can be destructive. Might anyone have suggestions as to how best to proceed? I've had success with recreating arrays in a similar state in the past (and also some failures :( ). I want to make sure that recreating is the best option forward and that I'm doing that step correctly.

It's not the end of the world since the majority of the data is backed up elsewhere, however I'd like to prevent the loss and also learn how to potentially overcome situations like this going forward.

Thanks in advance.

---

### Post by jgrevich on 2016-11-02
This info from the syslog may also be helpful. I believe this is the event that caused the array to degrade and it also matches with the distribution of event counts mentioned earlier.

```

Oct 31 20:35:56 jn kernel: [   41.919371] md/raid:md127: device sdm1 operational as raid disk 9
Oct 31 20:35:56 jn kernel: [   41.919374] md/raid:md127: device sdl1 operational as raid disk 8
Oct 31 20:35:56 jn kernel: [   41.919375] md/raid:md127: device sdk1 operational as raid disk 7
Oct 31 20:35:56 jn kernel: [   41.919377] md/raid:md127: device sdj1 operational as raid disk 4
Oct 31 20:35:56 jn kernel: [   41.919378] md/raid:md127: device sdi1 operational as raid disk 1
Oct 31 20:35:56 jn kernel: [   41.919379] md/raid:md127: device sdh1 operational as raid disk 2
Oct 31 20:35:56 jn kernel: [   41.919381] md/raid:md127: device sdg1 operational as raid disk 0
Oct 31 20:35:56 jn kernel: [   41.919382] md/raid:md127: device sdf1 operational as raid disk 6
Oct 31 20:35:56 jn kernel: [   41.919383] md/raid:md127: device sde1 operational as raid disk 3
Oct 31 20:35:56 jn kernel: [   41.919384] md/raid:md127: device sdc1 operational as raid disk 5
Oct 31 20:35:56 jn kernel: [   41.919386] md/raid:md127: device sdd1 operational as raid disk 10
Oct 31 20:35:56 jn kernel: [   41.920020] md/raid:md127: allocated 11780kB
Oct 31 20:35:56 jn kernel: [   41.920092] md/raid:md127: raid level 6 active with 11 out of 11 devices, algorithm 2
Oct 31 20:37:27 jn kernel: [  132.407322] md/raid:md127: Disk failure on sde1, disabling device.
Oct 31 20:37:27 jn kernel: [  132.407322] md/raid:md127: Operation continuing on 10 devices.
Oct 31 20:37:27 jn kernel: [  132.414514] md/raid:md127: Disk failure on sdf1, disabling device.
Oct 31 20:37:27 jn kernel: [  132.414514] md/raid:md127: Operation continuing on 9 devices.
Oct 31 20:37:27 jn kernel: [  132.421829] md/raid:md127: Disk failure on sdg1, disabling device.
Oct 31 20:37:27 jn kernel: [  132.421829] md/raid:md127: Operation continuing on 8 devices.
Oct 31 20:37:27 jn kernel: [  132.428838] md/raid:md127: Disk failure on sdh1, disabling device.
Oct 31 20:37:27 jn kernel: [  132.428838] md/raid:md127: Operation continuing on 7 devices.
Oct 31 20:37:27 jn kernel: [  132.435664] md/raid:md127: Disk failure on sdi1, disabling device.
Oct 31 20:37:27 jn kernel: [  132.435664] md/raid:md127: Operation continuing on 6 devices.
Oct 31 20:37:27 jn kernel: [  132.439084] md/raid:md127: Disk failure on sdj1, disabling device.
Oct 31 20:37:27 jn kernel: [  132.439084] md/raid:md127: Operation continuing on 5 devices.
Oct 31 20:37:27 jn kernel: [  132.442461] md/raid:md127: Disk failure on sdk1, disabling device.
Oct 31 20:37:27 jn kernel: [  132.442461] md/raid:md127: Operation continuing on 4 devices.
Oct 31 20:37:27 jn kernel: [  132.445823] md/raid:md127: Disk failure on sdl1, disabling device.
Oct 31 20:37:27 jn kernel: [  132.445823] md/raid:md127: Operation continuing on 3 devices.

```

---

