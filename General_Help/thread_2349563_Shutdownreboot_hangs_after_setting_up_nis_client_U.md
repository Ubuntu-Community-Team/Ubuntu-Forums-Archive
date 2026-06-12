---
title: "Shutdown/reboot hangs after setting up nis client Ubuntu16.04 LTS server"
date: 2017-01-16
forum: General Help
---

### Post by kkumagai on 2017-01-16
Shutdown/reboot hangs after setting up nis client Ubuntu16.04 LTS server 

Shutdown/reboot hangs and time out in 1 minutes and 30 seconds after editing nsswitch.conf file on setting up nis client.

Shutdown log is below.

```
A stop job is running for Raise network interfaces([count up] /1min 30S)

```

I followed the page below for setting up nis client.

[https://www.server-world.info/en/note?os=Ubuntu_16.04&p=nis&f=2](https://www.server-world.info/en/note?os=Ubuntu_16.04&p=nis&f=2)

Software versions are as follows:

nis version: 3.17-34ubuntu3
systemd version: 229-4ubuntu4

journalctl log on hanging: 

```
Jan 16 09:16:13 ubuntu systemd[1]: Stopped Load/Save Random Seed.
Jan 16 09:16:13 ubuntu systemd[1]: Stopped Create Volatile Files and Directories.
Jan 16 09:16:13 ubuntu systemd[1]: Deactivated swap /dev/disk/by-path/pci-0000:00:10.0-scsi-0:0:0:0-part5.
Jan 16 09:16:13 ubuntu systemd[1]: Deactivated swap /dev/sda5.
Jan 16 09:16:13 ubuntu systemd[1]: Deactivated swap /dev/disk/by-uuid/bf849d23-e9e8-46b0-ba88-9f974d3a541d.
Jan 16 09:17:41 ubuntu systemd[1]: networking.service: Stopping timed out. Terminating.
Jan 16 09:17:41 ubuntu systemd[1]: Stopped Raise network interfaces.
Jan 16 09:17:41 ubuntu systemd[1]: networking.service: Unit entered failed state.
Jan 16 09:17:41 ubuntu systemd[1]: networking.service: Failed with result 'timeout'.
Jan 16 09:17:41 ubuntu systemd[1]: Stopped target Local File Systems.
Jan 16 09:17:41 ubuntu systemd[1]: Unmounting /run/user/1000...
Jan 16 09:17:41 ubuntu systemd[1]: Stopped Apply Kernel Variables.
Jan 16 09:17:41 ubuntu systemd[1]: Stopped Load Kernel Modules.
Jan 16 09:17:42 ubuntu systemd[1]: Unmounted /run/user/1000.
Jan 16 09:17:42 ubuntu systemd[1]: Reached target Unmount All Filesystems.
Jan 16 09:17:42 ubuntu systemd[1]: Stopped target Local File Systems (Pre).
Jan 16 09:17:42 ubuntu systemd[1]: Stopped Create Static Device Nodes in /dev.
Jan 16 09:17:42 ubuntu systemd[1]: Stopped Remount Root and Kernel File Systems.
Jan 16 09:17:42 ubuntu systemd[1]: Reached target Shutdown.
Jan 16 09:17:42 ubuntu systemd[1]: Reached target Final Step.
Jan 16 09:17:42 ubuntu systemd[1]: Starting Reboot...
Jan 16 09:17:42 ubuntu systemd[1]: Shutting down.
Jan 16 09:17:42 ubuntu systemd-shutdown[1]: Sending SIGTERM to remaining processes...
Jan 16 09:17:42 ubuntu systemd-journald[1905]: Journal stopped

```

Any advice? Thank you.

---

### Post by kkumagai on 2017-01-19
Running "sudo apt upgrade" solved this problem. Thank you.

---

