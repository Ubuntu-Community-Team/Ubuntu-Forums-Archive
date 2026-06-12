---
title: "After suspend, disk comes back as read-only filesystem"
date: 2021-07-26
forum: General Help
---

### Post by uacnt83982803 on 2021-07-26
I keep having this issue where not every time, but about every 2nd or 3rd time I resume after a suspend, the pc is so slow it's almost unusable.  Then when I can finally log into it, apps won't run.  I eventually restart it (via the menu, not a hard reboot) and as it shuts down I get errors that files can't be closed due to a read-only file system.

So it restarts and then falls into the initramfs prompt.

I recover it by typing:  fsck /dev/mapper/ubuntu--vg-root /y and it fix the errors, then reboot.

After that it'll work fine for a few uses.  But almost always after 3 suspend/resume cycles, it faults again.

I've run the SMART tests on the hard drive.  A few bad sections but no major errors reported.

How do I solve this?  The PC is essentially useless to me if I have to redo this fix every couple of times I sign into it.

Thanks.

---

### Post by rbmorse on 2021-07-27
I'd be concerned about the errors SMART is reporting.  Unrecoverable bad sectors are a major error and an indication that the drive is failing and should be replaced at the first opportunity. 

If you haven't backed up your personal data to another physical device, do so now.

---

### Post by uacnt83982803 on 2021-07-29
I have everything backed up, multiple locations both local and remote.

The SMART status says the disk is ok, it reports 19 bad sectors but says the threshold (I assume for errors) is not exceeded.

Since the machine works perfectly except when I suspend and restore it a few times, I can't help but think it's something to do with the restore.  And, it's always that one folder that gets corrupted, nothing else.

---

### Post by uacnt83982803 on 2021-08-13
Update: through testing, I've determined that if I let the screen timeout expire and the system self-lock, this problem does not occur.  Eventually the system suspends (due to the power settings I have configured), but it recovers fine as long as I don't lock the screen or initiate suspend myself.

---

### Post by TheFu on 2021-08-13
I'd buy a new disk.  Any failed sectors are bad for data.  Learning about a failed sector due to file corruption isn't fun.  My data is more important than a $50 HDD/SSD.

SMART doesn't always provide notifications before failure according to experts.  In 100K+ disks, something like 22% failed without any SMART data hinting there were any issues at all.

---

### Post by Timothy Taylor on 2021-08-13
This resonates with issues I've had recently with system lock-up and no network access.
It all seemed to go wrong after the update which refuses to work with the proprietary Nvidia drivers...
:-(

---

### Post by TheFu on 2021-08-13
The 5.11.x kernel has been causing issues for other reasons.  Which kernel is being used?  Can you try an older kernel, say from the 5.8 or 5.4 kernel series?  Does that fix it?

---

### Post by Timothy Taylor on 2021-08-13
My current system:
Release 20.04.2 LTS (Focal Fossa) 64-bit
Kernel Linux 5.4.0-80-generic x86_64
MATE 1.24.0

I had the exact same experience as the OP (and my old HDD) a week or so back.

---

### Post by Timothy Taylor on 2021-08-15
Things started going wrong on my PC shortly after an upgrade which left me stuck in 640x480 graphics using NVIDIA driver.  I had to switch to X.Org.

I found this
[https://forums.developer.nvidia.com/t/black-screen-when-resuming-systemctl-suspend-using-nvidia-driver-470-57-02-with-kernel-5-8-0-63-generic-on-gtx-970-xubuntu-20-04-lts/184644](https://forums.developer.nvidia.com/t/black-screen-when-resuming-systemctl-suspend-using-nvidia-driver-470-57-02-with-kernel-5-8-0-63-generic-on-gtx-970-xubuntu-20-04-lts/184644)

---

