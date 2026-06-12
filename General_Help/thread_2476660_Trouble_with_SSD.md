---
title: "Trouble with SSD"
date: 2022-07-02
forum: General Help
---

### Post by peyre on 2022-07-02
A couple months ago I moved my hard drives back to my old desktop to make a games machine for my son.  I use the old standby, an SSD for boot and a HDD for bulk storage.  Once I got the automounting of the HDD straightened out everything was ok.  Then Wednesday it booted with this kind of error:

```
/dev/sdb3 contains a file system with errors, check forced.
/dev/sdb3:
Directory inode 7083535, block #0, offset 0: directory corrupted

/dev/sdb3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sb3 requires a manual fsck

BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

I ran **fsck -f /dev/sdb3**, it found errors, then I was able to boot normally again.  Thursday no problems.  Friday it booted fine, but then something happened (not sure what; I wasn't paying much attention) and I rebooted.  It came back to the same  **fsck -f /dev/sdb3**, fixed errors, and rebooted, but this time it came back to the same kind of error.  I tried twice more, but no good.  I booted up to the same again this morning (the error above is exactly what it's showing now).  Is the drive failing?

---

### Post by oldfred on 2022-07-02
If Ubuntu with disks, you have Smartmonitor tools in icon in upper right corner.
All I know is if drive is reported as good or bad, but it can run a lot of tests.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks is Smart Data:
[https://askubuntu.com/questions/983619/s-m-a-r-t-data-no-longer-available-in-ubuntu-16-04-disks-application](https://askubuntu.com/questions/983619/s-m-a-r-t-data-no-longer-available-in-ubuntu-16-04-disks-application)
 What a Failing HDD looks like
[https://ubuntuforums.org/showthread.php?t=2446974](https://ubuntuforums.org/showthread.php?t=2446974)

If you do not have Disks:
gsmartcontrol
sudo apt install smartmontools

---

### Post by peyre on 2022-07-02
Ok, I've booted from a live DVD, running Disk utility and scanning the SSD.  Short test didn't find anything.  Running an extended test now.

After that I guess I'll run the conveyance test.  What *is* that, anyway?

---

### Post by peyre on 2022-07-02
Looks like SMART gives it a passing grade on the extended test.  It shows some warning signs though, lots of "Old-Age" markers plus "Pre-Fail" markers on **Reallocated Sector Count**, **wear-leveling-count**, **used-reserved-blocks-total**, and **runtime-bad-block-total**. I'll run a conveyance test.

Edit: Ah, no.  It says:

```
Error starting SMART self-test.

sk_disk_smart_self_test: Operation not supported (udisks-error-quark, 0)
```

Is it that SSDs don't support a conveyance test?  Is that only for mechanicals?

---

