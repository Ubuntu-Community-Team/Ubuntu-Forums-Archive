---
title: "Fstrim is killing my boot time :-("
date: 2019-01-14
forum: General Help
---

### Post by risbac on 2019-01-14
I'm using a laptop with a SSD drive. Quite often it's unusable for long minutes at boot. Fstrim is working non stop, and I don't know why. 

Here is a good example :

risbac@francois-W550:/etc$ sudo systemd-analyze blame
    21min 9.643s fstrim.service
         33.652s plymouth-quit-wait.service
         30.104s NetworkManager-wait-online.service
         27.925s apt-daily.service
          3.781s minidlna.service
          3.748s teamviewerd.service
          2.767s ModemManager.service
          2.694s colord.service

I guess it's pretty obvious :) Question is, what can I do to improve that ? I don't really know where to look at. If you have any advice, I would be happy to hear ! Thanks !

---

### Post by oldfred on 2019-01-14
Is some massive amount of data getting added then deleted from SSD?
What settings do you have for drive in UEFI (s/b AHCI), and fstab?
Post this to see settings mounting partitions:
cat /etc/fstab

What brand/model system?
What video card/chip?

---

### Post by MartyBuntu on 2019-01-14
Have you moved or re-sized partitions (even swap partitions) lately?

---

### Post by mc4man on 2019-01-14
The  fstrim.service is only supposed to run once a week, is it more often for you?
How large is your unused mounted space?

To ck. it's history - 
```
journalctl -u fstrim
```
To ck. schedule
```
systemctl list-timers |grep fstrim
```

What happens if you run manually?
```
sudo fstrim -v /
```

---

### Post by risbac on 2019-01-15
Thanks for the feedback

I will run the commands when i'm back in front of the laptop.
But some answers already :

-Is some massive amount of data getting added then deleted from SSD?
I wouldn't say so. I have a 128Gb SSD and a 2Tb HD. Most data is on the 2Tb HD. So it can't be massive amount of data.


-What brand/model system?
It's a Clevo W550, with Intel chips. 

-Have you moved or re-sized partitions (even swap partitions) lately?
No, I didn't touch anything.

-The fstrim.service is only supposed to run once a week, is it more often for you?
No, I think it's running once a week only. I don't run this laptop often though, so I'm not surprised that fstrim is running each time I boot it.

-How large is your unused mounted space?
I have to check


-What happens if you run manually? sudo fstrim -v /
I tried yesterday, after it worked for 20 minutes on the first ftstrim. I updated Ubuntu, maybe 15 updates to run. It did sync some files with my NAS, but only on the 2Tb harddrive I think. So it's maybe 150Mb of data written on the SSD ? The second fstrim was running again for minutes, I stopped it to be able to work. I was surprised it didn't finish quickly after this first run.

---

### Post by risbac on 2019-01-15
Partition is 112gb, free space is 43Gb


journalctl -u fstrim

```
nov. 19 08:57:03 francois-W550 systemd[1]: Starting Discard unused blocks...
nov. 19 09:29:43 francois-W550 fstrim[1231]: /*: 38,4 GiB (41212026880*octets) t
nov. 19 09:29:43 francois-W550 systemd[1]: Started Discard unused blocks.
-- Reboot --
nov. 26 21:31:31 francois-W550 systemd[1]: Starting Discard unused blocks...
nov. 26 22:04:17 francois-W550 fstrim[1288]: /*: 33,2 GiB (35670732800*octets) t
nov. 26 22:04:17 francois-W550 systemd[1]: Started Discard unused blocks.
-- Reboot --
déc. 03 08:59:43 francois-W550 systemd[1]: Starting Discard unused blocks...
déc. 03 09:02:44 francois-W550 fstrim[12512]: /*: 4,9 GiB (5189734400*octets) ta
déc. 03 09:02:44 francois-W550 systemd[1]: Started Discard unused blocks.
-- Reboot --
déc. 10 21:36:14 francois-W550 systemd[1]: Starting Discard unused blocks...
déc. 10 22:08:54 francois-W550 fstrim[1317]: /*: 34 GiB (36474368000*octets) tai
déc. 10 22:08:54 francois-W550 systemd[1]: Started Discard unused blocks.
-- Reboot --
déc. 19 21:33:55 francois-W550 systemd[1]: Starting Discard unused blocks...
déc. 19 21:37:09 francois-W550 fstrim[9699]: /*: 4,3 GiB (4597256192*octets) tai
déc. 19 21:37:09 francois-W550 systemd[1]: Started Discard unused blocks.
-- Reboot --
déc. 28 21:29:10 francois-W550 systemd[1]: Starting Discard unused blocks...
déc. 28 21:57:23 francois-W550 systemd[1]: fstrim.service: Main process exited, 
déc. 28 21:57:23 francois-W550 systemd[1]: fstrim.service: Failed with result 's
déc. 28 21:57:23 francois-W550 systemd[1]: Stopped Discard unused blocks.
-- Reboot --
janv. 04 09:47:01 francois-W550 systemd[1]: Starting Discard unused blocks...
janv. 04 10:06:58 francois-W550 fstrim[1268]: /*: 41,3 GiB (44357140480*octets) 
janv. 04 10:06:58 francois-W550 systemd[1]: Started Discard unused blocks.
-- Reboot --
janv. 07 20:50:30 francois-W550 systemd[1]: Starting Discard unused blocks...
janv. 07 21:11:34 francois-W550 fstrim[6369]: /*: 40,8 GiB (43819663360*octets) 
janv. 07 21:11:34 francois-W550 systemd[1]: Started Discard unused blocks.
-- Reboot --
janv. 14 20:54:27 francois-W550 systemd[1]: Starting Discard unused blocks...
janv. 14 21:15:33 francois-W550 fstrim[1285]: /*: 40,5 GiB (43455893504*octets) 
janv. 14 21:15:33 francois-W550 systemd[1]: Started Discard unused blocks.
```


```
 systemctl list-timers |grep fstrim
Mon 2019-01-21 00:00:00 CET  5 days left   Mon 2019-01-14 20:54:27 CET  24h ago      fstrim.timer                 fstrim.service
```

```
fstab :
UUID=7666925c-b553-4ece-960c-909ce1b5ebdf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=10631389-90c7-4193-9a21-97ea5c3d8084 none            swap    sw              0       0
/dev/disk/by-label/Data /mnt/Data auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-label/Data2 /mnt/Data2 auto nosuid,nodev,nofail,x-gvfs-show 0 0

```

```
 sudo fstrim -v /
/*: 40,5 GiB (43444658176*octets) taillés
```

So it seems to be 40Gb each time.

---

### Post by jdeca57 on 2019-03-11
It's probably not the best way to reopen a thread but I have exactly the same problem. Once a week my boot time is very long, and I abort after disk activity stops {and I mean I hit the power button) and after a reboot everything is peachy. Next week I intend to try not to shutdown and see what happens since the problem is fstrim.
> jdc@johan-Latitude-E6430:~$ systemctl list-timers |grep fstrim
Mon 2019-03-18 00:00:00 CET  6 days left   Mon 2019-03-11 11:46:46 CET  5h 34min ago fstrim.timer                 fstrim.service
Doing it manually (getting long file activity)
> jdc@johan-Latitude-E6430:~$  sudo fstrim -v /
[sudo] password for jdc: 
/: 402,6 GiB (432260124672 bytes) trimmed
But ends normal and it takes minutes, but stops after disk activity.
And the last entry in the journal
j> dc@johan-Latitude-E6430:~$ journalctl -u fstrim
Mär 11 11:46:46 johan-Latitude-E6430 systemd[1]: Starting Discard unused blocks...
Mär 11 11:50:21 johan-Latitude-E6430 fstrim[598]: /: 402,6 GiB (432225497088 bytes) trimmed
Mär 11 11:50:21 johan-Latitude-E6430 systemd[1]: Started Discard unused blocks.
So putting it clearly once a week I don't have a normal startup. Perhaps if I leave the system up from Sunday to Monday I can avoid this problem but ...
Any Idea's?

---

### Post by jdeca57 on 2019-04-01
I did leave my computer on this night (march 31) and...

```
journalctl -u fstrim
.,,
Apr 01 00:00:22 johan-Latitude-E6430 systemd[1]: Starting Discard unused blocks.
Apr 01 00:04:15 johan-Latitude-E6430 fstrim[11184]: /: 400,8 GiB (430322884608 b
Apr 01 00:04:15 johan-Latitude-E6430 systemd[1]: Started Discard unused blocks.

```

Not a glitch. So there is a problem with fstrim and shutdown: when you start the system again it fails. After a reboot it works normally. Not critical, just annoying.

---

### Post by jdeca57 on 2019-04-22
This issue seems solved with the last upgrade. now - 19.04 - fstrim runs in the background and login works fine. Mind - the hardware is identical.

---

