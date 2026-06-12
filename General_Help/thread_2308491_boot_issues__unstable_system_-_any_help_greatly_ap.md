---
title: "boot issues / unstable system/ - any help greatly appreciated  15.04"
date: 2016-01-03
forum: General Help
---

### Post by ubuntark on 2016-01-03
Having multiple issues. I know enough to get ubuntu installed but do not have enough experience to keep it running smoothly.  

1 Can't install updates - receive error that I do not have enough free disk space  "
The upgrade needs a total of 86.4 M free space on disk '/boot'. Please free at least an additional 23.8 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

    I have tried teh sudo apt-get clean makes not difference and of course emptied all trash but still get same error when I attempt to update. 

2 boot issues ,  took me multiple attempts and finally it fired up. 


custom built laptop 
Memory 15.6 GiB
Processor Intel® Core&#8482; i7-4700MQ CPU @ 2.40GHz × 8 
Graphics  Intel® Haswell Mobile
OS type 64-bit
Disk 1.1 TB  plus a solid state drive where the OS is loaded

Here the details over my head:
elcome to Ubuntu 15.04!

[  OK  ] Created slice Root Slice.
[  OK  ] Listening on Journal Audit Socket.
[  OK  ] Listening on fsck to fsckd communication Socket.
[  OK  ] Listening on Journal Socket (/dev/log).
[  OK  ] Listening on Delayed Shutdown Socket.
[  OK  ] Created slice User and Session Slice.
[  OK  ] Created slice System Slice.
[  OK  ] Created slice system-getty.slice.
[  OK  ] Reached target Slices.
[  OK  ] Listening on udev Kernel Socket.
[  OK  ] Reached target Remote File Systems (Pre).
         Starting Increase datagram queue length...
[  OK  ] Listening on Journal Socket.
         Starting Load Kernel Modules...
         Starting Nameserver information manager...
         Starting Create list of required static device nodes for the current kernel...
         Starting Uncomplicated firewall...
         Mounting Debug File System...
[  OK  ] Started Read required files in advance.
         Starting Read required files in advance...
         Mounting Huge Pages File System...
         Mounting POSIX Message Queue File System...
[  OK  ] Started Braille Device Support.
         Starting Braille Device Support...
         Starting Setup Virtual Console...
[  OK  ] Listening on udev Control Socket.
         Starting udev Coldplug all Devices...
[  OK  ] Created slice system-systemd\x2dcryptsetup.slice.
[  OK  ] Set up automount Arbitrary Executable File Formats File System Automount Point.
[  OK  ] Created slice system-systemd\x2dfsck.slice.
[  OK  ] Listening on /dev/initctl Compatibility Named Pipe.
[  OK  ] Mounted POSIX Message Queue File System.
[  OK  ] Mounted Debug File System.
[  OK  ] Mounted Huge Pages File System.
[  OK  ] Started Increase datagram queue length.
[  OK  ] Started Create list of required static device nodes for the current kernel.
[  OK  ] Started Setup Virtual Console.
[  OK  ] Started Nameserver information manager.
         Starting Create Static Device Nodes in /dev...
[  OK  ] Listening on Syslog Socket.
         Starting Journal Service...
[  OK  ] Started udev Coldplug all Devices.
         Starting udev Wait for Complete Device Initialization...
[  OK  ] Started Load Kernel Modules.
         Mounting FUSE Control File System...
         Starting Apply Kernel Variables...
[  OK  ] Mounted FUSE Control File System.
[  OK  ] Started Apply Kernel Variables.
[  OK  ] Started Create Static Device Nodes in /dev.
         Starting udev Kernel Device Manager...
[  OK  ] Started Journal Service.
[  OK  ] Started udev Kernel Device Manager.
         Starting Show Plymouth Boot Screen...
[  OK  ] Started Show Plymouth Boot Screen.
[  OK  ] Created slice system-systemd\x2dbacklight.slice.
[  OK  ] Started Uncomplicated firewall.
[  OK  ] Created slice system-ifup.slice.
[  OK  ] Reached target Sound Card.
[  OK  ] Created slice system-systemd\x2drfkill.slice.
[  OK  ] Found device WDC_WD10JUCT-63CYNY0 1.
[  OK  ] Found device PLEXTOR_PX-128M6M 6.
[  OK  ] Found device PLEXTOR_PX-128M6M 1.
[  OK  ] Started udev Wait for Complete Device Initialization.
         Starting Copy rules generated while the root was ro...
         Starting File System Check on Root Device...
[  OK  ] Started Copy rules generated while the root was ro.
[  OK  ] Started File System Check Daemon to report status.
         Starting File System Check Daemon to report status...
[FAILED] Failed to start File System Check on Root Device.
See "systemctl status systemd-fsck-root.service" for details.
         Starting Remount Root and Kernel File Systems...
[  OK  ] Reached target Timers.
[  OK  ] Closed ACPID Listen Socket.
[  OK  ] Closed UUID daemon activation socket.
[  OK  ] Stopped Getty on tty1.
[  OK  ] Stopped getty on tty2-tty6 if dbus and logind are not available.
[  OK  ] Stopped Network Manager Wait Online.
[  OK  ] Stopped target Graphical Interface.
[  OK  ] Stopped Accounts Service.
[  OK  ] Stopped Light Display Manager.
[  OK  ] Stopped Detect the available GPUs and deal with any system changes.
[  OK  ] Stopped target Multi-User System.
[  OK  ] Stopped LSB: automatic crash report generation.
[  OK  ] Stopped Thermal Daemon Service.
[  OK  ] Stopped Wait for Plymouth Boot Screen to Quit.
[  OK  ] Stopped D-Bus System Message Bus.
[  OK  ] Stopped /etc/rc.local Compatibility.
[  OK  ] Reached target Login Prompts.
[  OK  ] Stopped Permit User Sessions.
[  OK  ] Stopped System Logging Service.
[  OK  ] Closed Syslog Socket.
[  OK  ] Stopped Network Manager.
[  OK  ] Stopped Modem Manager.
[  OK  ] Stopped LSB: Record successful boot for GRUB.
[  OK  ] Stopped LSB: Tool to automatically collect and submit kernel crash signatures.
[  OK  ] Stopped Cgroup management proxy.
[  OK  ] Stopped Cgroup management daemon.
[  OK  ] Stopped Enable support for additional executable binary formats.
[  OK  ] Stopped Login Service.
[  OK  ] Closed D-Bus System Message Bus Socket.
[  OK  ] Stopped Make remote CUPS printers available locally.
[  OK  ] Stopped CUPS Scheduler.
[  OK  ] Closed CUPS Scheduler.
[  OK  ] Stopped Avahi mDNS/DNS-SD Stack.
[  OK  ] Closed Avahi mDNS/DNS-SD Stack Activation Socket.
[  OK  ] Stopped LSB: Set the CPU Frequency Scaling governor to "ondemand".
[  OK  ] Stopped crash report submission daemon.
[  OK  ] Stopped Regular background program processing daemon.
[  OK  ] Stopped Restore /etc/resolv.conf if the system crashed before the ppp link was shut down..
[  OK  ] Stopped LSB: Speech Dispatcher.
[  OK  ] Stopped Run anacron jobs.
[  OK  ] Stopped LSB: Cleans up any mess left by 0dns-up.
[  OK  ] Stopped LSB: daemon to balance interrupts for SMP systems.
[  OK  ] Stopped target Basic System.
[  OK  ] Reached target Paths.
[  OK  ] Reached target Sockets.
[  OK  ] Stopped target System Initialization.
         Starting Restore Sound Card State...
[  OK  ] Started Emergency Shell.
         Starting Emergency Shell...
[  OK  ] Reached target Emergency Mode.
[  OK  ] Started Restore Sound Card State.
[  OK  ] Started Remount Root and Kernel File Systems.
         Starting Flush Journal to Persistent Storage...
         Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...
[  OK  ] Reached target Local File Systems (Pre).
         Starting File System Check on /dev/disk/by-uuid/21bdf37d-f5d2-484a-a851-2e2bc5e88ae4...
         Starting File System Check on /dev/disk/by-uuid/89130cc0-2867-4a9e-a95c-ede7e2e9d2a9...
         Starting Load/Save RF Kill Switch Status of rfkill0...
         Starting Load/Save Random Seed...
[  OK  ] Started Load/Save Screen Backlight Brightness of backlight:intel_backlight.
[  OK  ] Started File System Check on /dev/disk/by-uuid/21bdf37d-f5d2-484a-a851-2e2bc5e88ae4.
[  OK  ] Started File System Check on /dev/disk/by-uuid/89130cc0-2867-4a9e-a95c-ede7e2e9d2a9.
[  OK  ] Started Load/Save RF Kill Switch Status of rfkill0.
[  OK  ] Started Load/Save Random Seed.
[  OK  ] Started Flush Journal to Persistent Storage.
         Starting Cryptography Setup for cryptswap1...
         Mounting /boot...
         Mounting /home...
[  OK  ] Mounted /boot.
[  OK  ] Started Cryptography Setup for cryptswap1.
[  OK  ] Reached target Encrypted Volumes.
[  OK  ] Mounted /home.
[  OK  ] Found device /dev/mapper/cryptswap1.
         Activating swap /dev/mapper/cryptswap1...
[  OK  ] Reached target Local File Systems.
         Starting Wait for all "auto" /etc/network/interfaces to be up for network-online.target...
[  OK  ] Reached target Remote File Systems.
         Starting Set console keymap...
         Starting Create Volatile Files and Directories...
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting LSB: AppArmor initialization...
[  OK  ] Started Wait for all "auto" /etc/network/interfaces to be up for network-online.target.
[  OK  ] Activated swap /dev/mapper/cryptswap1.
[  OK  ] Started Create Volatile Files and Directories.
         Starting Update UTMP about System Boot/Shutdown...
         Starting Network Time Synchronization...
[  OK  ] Reached target Swap.
[  OK  ] Started Tell Plymouth To Write Out Runtime Data.
[  OK  ] Started Set console keymap.
[  OK  ] Started LSB: AppArmor initialization.
         Starting LSB: Raise network interfaces....
[  OK  ] Started ifup for eth0.
         Starting ifup for eth0...
[  OK  ] Started ifup for wlan0.
         Starting ifup for wlan0...
[  OK  ] Started Update UTMP about System Boot/Shutdown.
         Starting Update UTMP about System Runlevel Changes...
[  OK  ] Started Network Time Synchronization.
[  OK  ] Reached target System Time Synchronized.
[  OK  ] Started Update UTMP about System Runlevel Changes.
[  OK  ] Started LSB: Raise network interfaces..
[  OK  ] Reached target Network.
[  OK  ] Reached target Network is Online.
think@7887-W65-67SZ:~$ systemctl status systemd-fsck-root.service
&#9679; systemd-fsck-root.service - File System Check on Root Device
   Loaded: loaded (/lib/systemd/system/systemd-fsck-root.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since dom 2016-01-03 12:01:00 CST; 4h 30min ago
Condition: start condition failed at dom 2016-01-03 12:01:15 CST; 4h 29min ago
           ConditionPathIsReadWrite=!/ was not met
     Docs: man:systemd-fsck-root.service(8)
  Process: 622 ExecStart=/lib/systemd/systemd-fsck (code=exited, status=1/FAILURE)
 Main PID: 622 (code=exited, status=1/FAILURE)

ene 03 12:00:24 7887-W65-67SZ systemd-fsck[622]: /dev/sdb5: Inode 12785 has imagic flag set.
ene 03 12:00:24 7887-W65-67SZ systemd-fsck[622]: /dev/sdb5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
ene 03 12:00:24 7887-W65-67SZ systemd-fsck[622]: (i.e., without -a or -p options)
ene 03 12:01:00 7887-W65-67SZ systemd-fsck[622]: fsck failed with error code 4.
ene 03 12:01:00 7887-W65-67SZ systemd-fsck[622]: Running request emergency.target/start/replace
ene 03 12:01:00 7887-W65-67SZ systemd[1]: systemd-fsck-root.service: main process exited, code=exited, status=1/FAILURE
ene 03 12:01:00 7887-W65-67SZ systemd[1]: Failed to start File System Check on Root Device.
ene 03 12:01:00 7887-W65-67SZ systemd[1]: Unit systemd-fsck-root.service entered failed state.
ene 03 12:01:00 7887-W65-67SZ systemd[1]: systemd-fsck-root.service failed.
ene 03 12:01:15 7887-W65-67SZ systemd[1]: Started File System Check on Root Device.

---

### Post by ian-weisser on 2016-01-03
> **ubuntark said:**
> The upgrade needs a total of 86.4 M free space on disk '/boot'. Please free at least an additional 23.8 M of disk space on '/boot'.

Please show us the complete output of the following three commands:
```
uname -r
df
ls -l /boot
```

---

### Post by Seanan on 2016-01-04
Quick qestion? Have you messed around or installed anything that messes around with any permissions? Also have you had the boot error again since you got it to boot up again?

---

### Post by Seanan on 2016-01-04
> **ubuntark said:**
> 
think@7887-W65-67SZ:~$ systemctl status systemd-fsck-root.service
&#9679; systemd-fsck-root.service - File System Check on Root Device
   Loaded: loaded (/lib/systemd/system/systemd-fsck-root.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since dom 2016-01-03 12:01:00 CST; 4h 30min ago
Condition: start condition failed at dom 2016-01-03 12:01:15 CST; 4h 29min ago
           ConditionPathIsReadWrite=!/ was not met

 This would appear that some permissions are not correct

---

### Post by ubuntark on 2016-02-19
I got frustrated and trashed the whole system.  Not sure how to even end this thread or delete it...   thanks your time.

---

### Post by Bucky Ball on 2016-02-19
No-one seems to have mentioned this. 15.04 is no longer supported officially here or by Canonical. It has reached end-of-life, will receive no updates of any kind, including security, and shortly the repositories will be moved and you will be facing greater issues than this.

Suggest you upgrade to a supported release, 15.10 or 14.04 LTS, both upgradeable to 16.04 LTS (LTS has five years support) in the second part of 2016.

Good luck.

PS: Just mark the thread as 'solved' and move on if you're finished here. Users can't delete threads (and staff don't). I can close the thread if you'd prefer.

---

### Post by ubuntark on 2016-02-19
Thank you

---

### Post by Bucky Ball on 2016-02-19
Follow link in my signature to mark officially as solved. :)

---

