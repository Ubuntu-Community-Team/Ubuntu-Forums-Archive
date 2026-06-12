---
title: "Hang during reboot"
date: 2013-02-22
forum: General Help
---

### Post by hiKen on 2013-02-22
When issuing a reboot from Ubuntu 12.04/12.10 (Linux kernel 3.5), the laptop hangs for about 1m30s on the "Restarting System" line of the shutdown output. From what I've been able to gather, this only happens when I have a HDD/SDD on a specific SATA port on the laptop (the main SATA port, originally used for HDD, now with a SSD mounted). With the SSD mounted on the secondary SATA port, reboot is normal (no hang, pretty fast)

/etc/fstab:

UUID=0240d6ae-722b-44ed-afad-865b1b3259c4 /                ext4    errors=remount-ro,noatime,nodiratime,discard  0  1
UUID=025594dd-cd9f-4a9c-a078-88d69e4677ae none             swap    sw                                            0  0
none                                      /tmp             tmpfs   nodev,nosuid,mode=1777                        0  0
UUID=e9048353-e50c-4d7c-b716-9701bfdb4da9 /media/joao/DATA ext4    defaults                                      0  0

The strange thing is, this [B]only happens when issuing a restart, not when shutting down.
[/B]

Anyone with any ideas/solutions?

---

### Post by ersatzsplatt on 2013-02-23
... obviously it seems like this is related to your storage activity.  You can first reference your sytem log files (compare the shutdown of the fast/good to the slow/not-as-good).  If there is not enough information there, you find out what driver you are using for your sata.  Often it is possible to increase the logging (some kind of debug level).  Then repeat the comparison.
My first guess would be there is something exiting or not being scheduled which should flush to the SSD.

If you aren't up to that kind of heavy lifting, a quick check which could add more information is:
close all your applications ... maybe even your graphical environment.  Then issue:
sync
or
sudo sync
twice, so the password will not be required again.
... now will it be slow (with the "slow" configuration) when you reboot?  I would guess not.

---

### Post by hiKen on 2013-02-23
> **ersatzsplatt said:**
> ... obviously it seems like this is related to your storage activity.  You can first reference your sytem log files (compare the shutdown of the fast/good to the slow/not-as-good).  If there is not enough information there, you find out what driver you are using for your sata.  Often it is possible to increase the logging (some kind of debug level).  Then repeat the comparison.
My first guess would be there is something exiting or not being scheduled which should flush to the SSD.

If you aren't up to that kind of heavy lifting, a quick check which could add more information is:
close all your applications ... maybe even your graphical environment.  Then issue:
sync
or
sudo sync
twice, so the password will not be required again.
... now will it be slow (with the "slow" configuration) when you reboot?  I would guess not.

Is there a way to save the log files from shutdown/reboot? Right now I'm just looking at the output on the screen, where it hangs during "Restarting System." And I think this happens after the partitions are unmounted, so I dont think it would be possible to save.

Anyway, I stopped lightdm, switched to tty1, and issued "sudo sync" twice, and then issued a "sudo reboot", but the problem persists...

---

