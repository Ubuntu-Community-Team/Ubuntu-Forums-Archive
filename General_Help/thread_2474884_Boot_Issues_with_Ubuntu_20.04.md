---
title: "Boot Issues with Ubuntu 20.04"
date: 2022-05-10
forum: General Help
---

### Post by laurel798 on 2022-05-10
After fresh install of Ubuntu when the system restarts/powers off, on boot the screen hangs on a black screen. No keys do anything when pressed, other than when I hold the power key to do a 'hard shutdown'. Once I then power on again, the system boots up normally, taking me to the login screen.

I had originally installed 22.03 and changed to the previous LTS to see if this might help.
I have tried numerous different kernels (sorry, I can't remember which ones but usually the two newest avail and then an older one).
I have disabled secure boot in shim-signed.
I have edited my grub conf so that the hidden timeout style is commented out and timeout is set to 10 seconds. 
I have also added "processor.max_cstate=5 rcu_nocbs=0-11 idle=nomwait" to the kernel boot options.
I have changed the boot mode from splash to 'nomodeset', also to 'radeon.modeset=0' and lastly to 'nomodeset xforcevesa'.
I have blacklisted my radeon driver.
I have tried a boot repair.

I've been reading things about UEFI installs and I honestly can't make sense of that- all I can tell you is that I flashed iso files to a bootable usb and installed using it.

I ran a script for partition and boot info and sent it to paste. The info can be found under this link : [https://paste.ubuntu.com/p/NhhvdVdPjM/](https://paste.ubuntu.com/p/NhhvdVdPjM/)


Bootlog- 

```
[------------ Tue May 10 18:19:56 BST 2022 ------------
[[0;32m  OK  [0m] Started [0;1;39mShow Plymouth Boot Screen[0m.
[[0;32m  OK  [0m] Started [0;1;39mForward Password Requests to Plymouth Directory Watch[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mLocal Encrypted Volumes[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for core20, revision 1328[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gtk-common-themes, revision 1519[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gnome-3-38-2004, revision 99[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snap-store, revision 558[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mLoad/Save RF Kill Switch Status /dev/rfkill Watch[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snapd, revision 14978[0m.
[[0;32m  OK  [0m] Found device [0;1;39mSAMSUNG MZVLQ512HALU-00000 EFI\x20System\x20Partition[0m.
         Starting [0;1;39mFile System Check on /dev/disk/by-uuid/98FC-444E[0m...
[[0;32m  OK  [0m] Started [0;1;39mFile System Check Daemon to report status[0m.
[[0;32m  OK  [0m] Finished [0;1;39mFile System Check on /dev/disk/by-uuid/98FC-444E[0m.
         Mounting [0;1;39m/boot/efi[0m...
         Starting [0;1;39mLoad/Save RF Kill Switch Status[0m...
[[0;32m  OK  [0m] Mounted [0;1;39m/boot/efi[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mLocal File Systems[0m.
         Starting [0;1;39mLoad AppArmor profiles[0m...
         Starting [0;1;39mSet console font and keymap[0m...
         Starting [0;1;39mTell Plymouth To Write Out Runtime Data[0m...
         Starting [0;1;39mCommit a transient machine-id on disk[0m...
         Starting [0;1;39mCreate Volatile Files and Directories[0m...
[[0;32m  OK  [0m] Started [0;1;39mLoad/Save RF Kill Switch Status[0m.
[[0;32m  OK  [0m] Finished [0;1;39mSet console font and keymap[0m.
[[0;32m  OK  [0m] Finished [0;1;39mTell Plymouth To Write Out Runtime Data[0m.
[[0;32m  OK  [0m] Finished [0;1;39mCreate Volatile Files and Directories[0m.
         Starting [0;1;39mNetwork Name Resolution[0m...
         Starting [0;1;39mNetwork Time Synchronization[0m...
         Starting [0;1;39mUpdate UTMP about System Boot/Shutdown[0m...
[[0;32m  OK  [0m] Finished [0;1;39mCommit a transient machine-id on disk[0m.
[[0;32m  OK  [0m] Finished [0;1;39mUpdate UTMP about System Boot/Shutdown[0m.
[[0;32m  OK  [0m] Created slice [0;1;39msystem-systemd\x2dbacklight.slice[0m.
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of leds:asus::kbd_backlight[0m...
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen Backlight Brightness of leds:asus::kbd_backlight[0m.
[[0;32m  OK  [0m] Started [0;1;39mNetwork Time Synchronization[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Set[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Synchronized[0m.
         Starting [0;1;39mTell Plymouth To Write Out Runtime Data[0m...
------------ Tue May 10 18:19:56 BST 2022 ------------
[[0;32m  OK  [0m] Finished [0;1;39mTell Plymouth To Write Out Runtime Data[0m.
[[0;32m  OK  [0m] Started [0;1;39mNetwork Name Resolution[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mHost and Network Name Lookups[0m.
         Starting [0;1;39mLoad/Save Screen &#8230;ss of backlight:acpi_video0[0m...
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen &#8230;ness of backlight:acpi_video0[0m.
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor profiles[0m.
         Starting [0;1;39mLoad AppArmor pro&#8230;managed internally by snapd[0m...
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor pro&#8230;s managed internally by snapd[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Initialization[0m.
[[0;32m  OK  [0m] Started [0;1;39mACPI Events Check[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger to poll fo&#8230;y enabled on GCP LTS non-pro)[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger anacron every hour[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt download activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt upgrade and clean activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mPeriodic ext4 Onli&#8230;ata Check for All Filesystems[0m.
[[0;32m  OK  [0m] Started [0;1;39mDiscard unused blocks once a week[0m.
[[0;32m  OK  [0m] Started [0;1;39mRefresh fwupd metadata regularly[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily rotation of log files[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily man-db regeneration[0m.
[[0;32m  OK  [0m] Started [0;1;39mMessage of the Day[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily Cleanup of Temporary Directories[0m.
[[0;32m  OK  [0m] Started [0;1;39mUbuntu Advantage Timer for running repeated jobs[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mPaths[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mTimers[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mACPID Listen Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mAvahi mDNS/DNS-SD Stack Activation Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mD-Bus System Message Bus Socket[0m.
         Starting [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mUUID daemon activation socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSockets[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBasic System[0m.
         Starting [0;1;39mAccounts Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mACPI event daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mRun anacron jobs[0m.
         Starting [0;1;39mLSB: automatic crash report generation[0m...
         Starting [0;1;39mAvahi mDNS/DNS-SD Stack[0m...
         Starting [0;1;39mBluetooth service[0m...
[[0;32m  OK  [0m] Started [0;1;39mRegular background program processing daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mD-Bus System Message Bus[0m.
         Starting [0;1;39mNetwork Manager[0m...
[[0;32m  OK  [0m] Started [0;1;39mSave initial kernel messages after boot[0m.
         Starting [0;1;39mRemove Stale Onli&#8230;t4 Metadata Check Snapshots[0m...
[[0;32m  OK  [0m] Reached target [0;1;39mLogin Prompts[0m.
         Starting [0;1;39mDetect the availa&#8230;eal with any system changes[0m...
         Starting [0;1;39mRecord successful boot for GRUB[0m...
[[0;32m  OK  [0m] Started [0;1;39mirqbalance daemon[0m.
         Starting [0;1;39mDispatcher daemon for systemd-networkd[0m...
[[0;32m  OK  [0m] Started [0;1;39mSet the CPU Frequency Scaling governor[0m.
         Starting [0;1;39mAuthorization Manager[0m...
         Starting [0;1;39mRestore /etc/reso&#8230; the ppp link was shut down[0m...
         Starting [0;1;39mSystem Logging Service[0m...
         Starting [0;1;39mSecure Boot updates for DB and DBX[0m...
         Starting [0;1;39mSnap Daemon[0m...
         Starting [0;1;39mSwitcheroo Control Proxy service[0m...
         Starting [0;1;39mLogin Service[0m...
         Starting [0;1;39mThermal Daemon Service[0m...
         Starting [0;1;39mDisk Manager[0m...
         Starting [0;1;39mWPA supplicant[0m...
[[0;32m  OK  [0m] Finished [0;1;39mRemove Stale Onli&#8230;ext4 Metadata Check Snapshots[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRestore /etc/reso&#8230;re the ppp link was shut down[0m.
[[0;32m  OK  [0m] Finished [0;1;39mDetect the availa&#8230; deal with any system changes[0m.
[[0;32m  OK  [0m] Started [0;1;39mSystem Logging Service[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRecord successful boot for GRUB[0m.
         Starting [0;1;39mGRUB failed boot detection[0m...
[[0;32m  OK  [0m] Finished [0;1;39mSecure Boot updates for DB and DBX[0m.
[[0;32m  OK  [0m] Started [0;1;39mLSB: automatic crash report generation[0m.
[[0;32m  OK  [0m] Finished [0;1;39mGRUB failed boot detection[0m.
[[0;32m  OK  [0m] Started [0;1;39mWPA supplicant[0m.
[[0;32m  OK  [0m] Started [0;1;39mAvahi mDNS/DNS-SD Stack[0m.
[[0;32m  OK  [0m] Started [0;1;39mMake remote CUPS printers available locally[0m.
[[0;32m  OK  [0m] Started [0;1;39mBluetooth service[0m.
[[0;32m  OK  [0m] Started [0;1;39mThermal Daemon Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mSwitcheroo Control Proxy service[0m.
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBluetooth[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork[0m.
         Starting [0;1;39mNetwork Manager Wait Online[0m...
         Starting [0;1;39mSave/Restore Sound Card State[0m...
         Starting [0;1;39mOpenVPN service[0m...
         Starting [0;1;39mPermit User Sessions[0m...
[[0;32m  OK  [0m] Finished [0;1;39mOpenVPN service[0m.
[[0;32m  OK  [0m] Started [0;1;39mAuthorization Manager[0m.
         Starting [0;1;39mModem Manager[0m...
         Starting [0;1;39mHostname Service[0m...
[[0;32m  OK  [0m] Finished [0;1;39mPermit User Sessions[0m.
[[0;32m  OK  [0m] Finished [0;1;39mSave/Restore Sound Card State[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSound Card[0m.
         Starting [0;1;39mGNOME Display Manager[0m...
         Starting [0;1;39mHold until boot process finishes up[0m...
[[0;32m  OK  [0m] Started [0;1;39mAccounts Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mDisk Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mHostname Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mModem Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mDispatcher daemon for systemd-networkd[0m.
         Starting [0;1;39mNetwork Manager Script Dispatcher Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager Script Dispatcher Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mLogin Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mUnattended Upgrades Shutdown[0m.
[[0;32m  OK  [0m] Started [0;1;39mSnap Daemon[0m.
         Starting [0;1;39mWait until snapd is fully seeded[0m...
[[0;32m  OK  [0m] Started [0;1;39msnap.snap-store.ho&#8230;-4047-88d5-9da0f7d9059e.scope[0m.
[[0;32m  OK  [0m] Finished [0;1;39mNetwork Manager Wait Online[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork is Online[0m.
         Starting [0;1;39mTool to automatic&#8230;mit kernel crash signatures[0m...
[[0;32m  OK  [0m] Started [0;1;39mcrash report submission daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mTool to automatica&#8230;ubmit kernel crash signatures[0m.
         Starting [0;1;39mTime & Date Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mTime & Date Service[0m.
[[0;32m  OK  [0m] Finished [0;1;39mWait until snapd is fully seeded[0m.
------------ Tue May 10 18:27:08 BST 2022 ------------
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for bare, revision 5[0m.
[[0;32m  OK  [0m] Started [0;1;39mShow Plymouth Boot Screen[0m.
[[0;32m  OK  [0m] Started [0;1;39mForward Password Requests to Plymouth Directory Watch[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mLocal Encrypted Volumes[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gnome-3-38-2004, revision 99[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gtk-common-themes, revision 1519[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snapd, revision 14978[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mLoad/Save RF Kill Switch Status /dev/rfkill Watch[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snap-store, revision 558[0m.
         Starting [0;1;39mLoad/Save RF Kill Switch Status[0m...
[[0;32m  OK  [0m] Found device [0;1;39mSAMSUNG MZVLQ512HALU-00000 EFI\x20System\x20Partition[0m.
         Starting [0;1;39mFile System Check on /dev/disk/by-uuid/98FC-444E[0m...
[[0;32m  OK  [0m] Started [0;1;39mFile System Check Daemon to report status[0m.
[[0;32m  OK  [0m] Finished [0;1;39mFile System Check on /dev/disk/by-uuid/98FC-444E[0m.
         Mounting [0;1;39m/boot/efi[0m...
[[0;32m  OK  [0m] Started [0;1;39mLoad/Save RF Kill Switch Status[0m.
[[0;32m  OK  [0m] Mounted [0;1;39m/boot/efi[0m.
[[0;32m  OK  [0m] Created slice [0;1;39msystem-systemd\x2dbacklight.slice[0m.
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of leds:asus::kbd_backlight[0m...
[[0;32m  OK  [0m] Reached target [0;1;39mLocal File Systems[0m.
         Starting [0;1;39mLoad AppArmor profiles[0m...
         Starting [0;1;39mSet console font and keymap[0m...
         Starting [0;1;39mTell Plymouth To Write Out Runtime Data[0m...
         Starting [0;1;39mCreate Volatile Files and Directories[0m...
[[0;32m  OK  [0m] Finished [0;1;39mSet console font and keymap[0m.
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen Backlight Brightness of leds:asus::kbd_backlight[0m.
[[0;32m  OK  [0m] Finished [0;1;39mTell Plymouth To Write Out Runtime Data[0m.
[[0;32m  OK  [0m] Finished [0;1;39mCreate Volatile Files and Directories[0m.
         Starting [0;1;39mNetwork Name Resolution[0m...
         Starting [0;1;39mNetwork Time Synchronization[0m...
         Starting [0;1;39mUpdate UTMP about System Boot/Shutdown[0m...
[[0;32m  OK  [0m] Finished [0;1;39mUpdate UTMP about System Boot/Shutdown[0m.
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor profiles[0m.
         Starting [0;1;39mLoad AppArmor profiles managed internally by snapd[0m...
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor pro&#8230;s managed internally by snapd[0m.
[[0;32m  OK  [0m] Started [0;1;39mNetwork Time Synchronization[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Initialization[0m.
[[0;32m  OK  [0m] Started [0;1;39mACPI Events Check[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger to poll fo&#8230;y enabled on GCP LTS non-pro)[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily Cleanup of Temporary Directories[0m.
[[0;32m  OK  [0m] Started [0;1;39mUbuntu Advantage Timer for running repeated jobs[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mPaths[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Set[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Synchronized[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger anacron every hour[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt download activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt upgrade and clean activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mPeriodic ext4 Onli&#8230;ata Check for All Filesystems[0m.
[[0;32m  OK  [0m] Started [0;1;39mDiscard unused blocks once a week[0m.
[[0;32m  OK  [0m] Started [0;1;39mRefresh fwupd metadata regularly[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily rotation of log files[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily man-db regeneration[0m.
[[0;32m  OK  [0m] Started [0;1;39mMessage of the Day[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mTimers[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mACPID Listen Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mAvahi mDNS/DNS-SD Stack Activation Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mD-Bus System Message Bus Socket[0m.
         Starting [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mUUID daemon activation socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSockets[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBasic System[0m.
         Starting [0;1;39mAccounts Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mACPI event daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mRun anacron jobs[0m.
         Starting [0;1;39mLSB: automatic crash report generation[0m...
         Starting [0;1;39mAvahi mDNS/DNS-SD Stack[0m...
         Starting [0;1;39mBluetooth service[0m...
[[0;32m  OK  [0m] Started [0;1;39mRegular background program processing daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mD-Bus System Message Bus[0m.
         Starting [0;1;39mNetwork Manager[0m...
[[0;32m  OK  [0m] Started [0;1;39mSave initial kernel messages after boot[0m.
         Starting [0;1;39mRemove Stale Onli&#8230;t4 Metadata Check Snapshots[0m...
[[0;32m  OK  [0m] Reached target [0;1;39mLogin Prompts[0m.
         Starting [0;1;39mDetect the availa&#8230;eal with any system changes[0m...
         Starting [0;1;39mRecord successful boot for GRUB[0m...
[[0;32m  OK  [0m] Started [0;1;39mirqbalance daemon[0m.
         Starting [0;1;39mDispatcher daemon for systemd-networkd[0m...
[[0;32m  OK  [0m] Started [0;1;39mSet the CPU Frequency Scaling governor[0m.
         Starting [0;1;39mAuthorization Manager[0m...
         Starting [0;1;39mRestore /etc/reso&#8230; the ppp link was shut down[0m...
         Starting [0;1;39mSystem Logging Service[0m...
         Starting [0;1;39mSecure Boot updates for DB and DBX[0m...
         Starting [0;1;39mSnap Daemon[0m...
         Starting [0;1;39mSwitcheroo Control Proxy service[0m...
         Starting [0;1;39mLogin Service[0m...
         Starting [0;1;39mThermal Daemon Service[0m...
         Starting [0;1;39mDisk Manager[0m...
         Starting [0;1;39mWPA supplicant[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Name Resolution[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRestore /etc/reso&#8230;re the ppp link was shut down[0m.
[[0;32m  OK  [0m] Started [0;1;39mSystem Logging Service[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mHost and Network Name Lookups[0m.
[[0;32m  OK  [0m] Finished [0;1;39mDetect the availa&#8230; deal with any system changes[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRecord successful boot for GRUB[0m.
         Starting [0;1;39mGRUB failed boot detection[0m...
[[0;32m  OK  [0m] Finished [0;1;39mSecure Boot updates for DB and DBX[0m.
[[0;32m  OK  [0m] Started [0;1;39mLSB: automatic crash report generation[0m.
[[0;32m  OK  [0m] Finished [0;1;39mGRUB failed boot detection[0m.
[[0;32m  OK  [0m] Started [0;1;39mBluetooth service[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBluetooth[0m.
[[0;32m  OK  [0m] Started [0;1;39mAvahi mDNS/DNS-SD Stack[0m.
[[0;32m  OK  [0m] Started [0;1;39mWPA supplicant[0m.
[[0;32m  OK  [0m] Started [0;1;39mThermal Daemon Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mMake remote CUPS printers available locally[0m.
[[0;32m  OK  [0m] Started [0;1;39mSwitcheroo Control Proxy service[0m.
         Starting [0;1;39mSave/Restore Sound Card State[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork[0m.
         Starting [0;1;39mNetwork Manager Wait Online[0m...
         Starting [0;1;39mOpenVPN service[0m...
         Starting [0;1;39mPermit User Sessions[0m...
[[0;32m  OK  [0m] Finished [0;1;39mSave/Restore Sound Card State[0m.
[[0;32m  OK  [0m] Finished [0;1;39mOpenVPN service[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSound Card[0m.
         Starting [0;1;39mHostname Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mAuthorization Manager[0m.
         Starting [0;1;39mModem Manager[0m...
[[0;32m  OK  [0m] Finished [0;1;39mPermit User Sessions[0m.
         Starting [0;1;39mGNOME Display Manager[0m...
         Starting [0;1;39mHold until boot process finishes up[0m...
[[0;32m  OK  [0m] Started [0;1;39mAccounts Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mDisk Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mModem Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mDispatcher daemon for systemd-networkd[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRemove Stale Onli&#8230;ext4 Metadata Check Snapshots[0m.
[[0;32m  OK  [0m] Started [0;1;39mHostname Service[0m.
         Starting [0;1;39mNetwork Manager Script Dispatcher Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager Script Dispatcher Service[0m.
[[0;32m  OK  [0m] Finished [0;1;39mNetwork Manager Wait Online[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork is Online[0m.
         Starting [0;1;39mTool to automatic&#8230;mit kernel crash signatures[0m...
[[0;32m  OK  [0m] Started [0;1;39mcrash report submission daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mTool to automatica&#8230;ubmit kernel crash signatures[0m.
[[0;32m  OK  [0m] Started [0;1;39mSnap Daemon[0m.
         Starting [0;1;39mWait until snapd is fully seeded[0m...
         Starting [0;1;39mTime & Date Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mTime & Date Service[0m.
[[0;32m  OK  [0m] Finished [0;1;39mWait until snapd is fully seeded[0m.
[[0;32m  OK  [0m] Started [0;1;39mLogin Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mUnattended Upgrades Shutdown[0m.
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of backlight:acpi_video0[0m...
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of backlight:amdgpu_bl0[0m...
[[0;1;31mFAILED[0m] Failed to start [0;1;39mLoad/Save Screen Backlight Brightness of backlight:acpi_video0[0m.
See 'systemctl status [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e' for details.
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen Backlight Brightness of backlight:amdgpu_bl0[0m.
[[0;32m  OK  [0m] Started [0;1;39mGNOME Display Manager[0m.
------------ Wed May 11 01:51:46 BST 2022 ------------
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for core20, revision 1328[0m.
[[0;32m  OK  [0m] Started [0;1;39mShow Plymouth Boot Screen[0m.
[[0;32m  OK  [0m] Started [0;1;39mForward Password Requests to Plymouth Directory Watch[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mLocal Encrypted Volumes[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for core20, revision 1434[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snapd, revision 14978[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mLoad/Save RF Kill Switch Status /dev/rfkill Watch[0m.
         Starting [0;1;39mLoad/Save RF Kill Switch Status[0m...
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gtk-common-themes, revision 1519[0m.
[[0;32m  OK  [0m] Created slice [0;1;39msystem-systemd\x2dbacklight.slice[0m.
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of leds:asus::kbd_backlight[0m...
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen Backlight Brightness of leds:asus::kbd_backlight[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gnome-3-38-2004, revision 99[0m.
[[0;32m  OK  [0m] Started [0;1;39mLoad/Save RF Kill Switch Status[0m.
[[0;32m  OK  [0m] Found device [0;1;39mSAMSUNG MZVLQ512HALU-00000 EFI\x20System\x20Partition[0m.
         Starting [0;1;39mFile System Check on /dev/disk/by-uuid/98FC-444E[0m...
[[0;32m  OK  [0m] Started [0;1;39mFile System Check Daemon to report status[0m.
[[0;32m  OK  [0m] Finished [0;1;39mFile System Check on /dev/disk/by-uuid/98FC-444E[0m.
         Mounting [0;1;39m/boot/efi[0m...
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snap-store, revision 558[0m.
[[0;32m  OK  [0m] Mounted [0;1;39m/boot/efi[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snapd, revision 15534[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mLocal File Systems[0m.
         Starting [0;1;39mLoad AppArmor profiles[0m...
         Starting [0;1;39mSet console font and keymap[0m...
         Starting [0;1;39mTell Plymouth To Write Out Runtime Data[0m...
         Starting [0;1;39mCreate Volatile Files and Directories[0m...
[[0;32m  OK  [0m] Finished [0;1;39mSet console font and keymap[0m.
[[0;32m  OK  [0m] Finished [0;1;39mTell Plymouth To Write Out Runtime Data[0m.
[[0;32m  OK  [0m] Finished [0;1;39mCreate Volatile Files and Directories[0m.
         Starting [0;1;39mNetwork Name Resolution[0m...
         Starting [0;1;39mNetwork Time Synchronization[0m...
         Starting [0;1;39mUpdate UTMP about System Boot/Shutdown[0m...
[[0;32m  OK  [0m] Finished [0;1;39mUpdate UTMP about System Boot/Shutdown[0m.
         Starting [0;1;39mTell Plymouth To Write Out Runtime Data[0m...
------------ Wed May 11 01:51:46 BST 2022 ------------
[[0;32m  OK  [0m] Finished [0;1;39mTell Plymouth To Write Out Runtime Data[0m.
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor profiles[0m.
         Starting [0;1;39mLoad AppArmor pro&#8230;managed internally by snapd[0m...
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor pro&#8230;s managed internally by snapd[0m.
[[0;32m  OK  [0m] Started [0;1;39mNetwork Time Synchronization[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Initialization[0m.
[[0;32m  OK  [0m] Started [0;1;39mACPI Events Check[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger to poll fo&#8230;y enabled on GCP LTS non-pro)[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily Cleanup of Temporary Directories[0m.
[[0;32m  OK  [0m] Started [0;1;39mUbuntu Advantage Timer for running repeated jobs[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mPaths[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Set[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Synchronized[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger anacron every hour[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt download activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt upgrade and clean activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mPeriodic ext4 Onli&#8230;ata Check for All Filesystems[0m.
[[0;32m  OK  [0m] Started [0;1;39mDiscard unused blocks once a week[0m.
[[0;32m  OK  [0m] Started [0;1;39mRefresh fwupd metadata regularly[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily rotation of log files[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily man-db regeneration[0m.
[[0;32m  OK  [0m] Started [0;1;39mMessage of the Day[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mTimers[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mACPID Listen Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mAvahi mDNS/DNS-SD Stack Activation Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mD-Bus System Message Bus Socket[0m.
         Starting [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mUUID daemon activation socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSockets[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBasic System[0m.
         Starting [0;1;39mAccounts Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mACPI event daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mRun anacron jobs[0m.
         Starting [0;1;39mLSB: automatic crash report generation[0m...
         Starting [0;1;39mAvahi mDNS/DNS-SD Stack[0m...
         Starting [0;1;39mBluetooth service[0m...
[[0;32m  OK  [0m] Started [0;1;39mRegular background program processing daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mD-Bus System Message Bus[0m.
         Starting [0;1;39mNetwork Manager[0m...
[[0;32m  OK  [0m] Started [0;1;39mSave initial kernel messages after boot[0m.
         Starting [0;1;39mRemove Stale Onli&#8230;t4 Metadata Check Snapshots[0m...
[[0;32m  OK  [0m] Reached target [0;1;39mLogin Prompts[0m.
         Starting [0;1;39mDetect the availa&#8230;eal with any system changes[0m...
         Starting [0;1;39mRecord successful boot for GRUB[0m...
[[0;32m  OK  [0m] Started [0;1;39mirqbalance daemon[0m.
         Starting [0;1;39mDispatcher daemon for systemd-networkd[0m...
[[0;32m  OK  [0m] Started [0;1;39mSet the CPU Frequency Scaling governor[0m.
         Starting [0;1;39mAuthorization Manager[0m...
         Starting [0;1;39mRestore /etc/reso&#8230; the ppp link was shut down[0m...
         Starting [0;1;39mSystem Logging Service[0m...
         Starting [0;1;39mSecure Boot updates for DB and DBX[0m...
         Starting [0;1;39mSnap Daemon[0m...
         Starting [0;1;39mSwitcheroo Control Proxy service[0m...
         Starting [0;1;39mLogin Service[0m...
         Starting [0;1;39mThermal Daemon Service[0m...
         Starting [0;1;39mDisk Manager[0m...
         Starting [0;1;39mWPA supplicant[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Name Resolution[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRemove Stale Onli&#8230;ext4 Metadata Check Snapshots[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRestore /etc/reso&#8230;re the ppp link was shut down[0m.
[[0;32m  OK  [0m] Started [0;1;39mSystem Logging Service[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mHost and Network Name Lookups[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRecord successful boot for GRUB[0m.
         Starting [0;1;39mGRUB failed boot detection[0m...
[[0;32m  OK  [0m] Started [0;1;39mLSB: automatic crash report generation[0m.
[[0;32m  OK  [0m] Finished [0;1;39mSecure Boot updates for DB and DBX[0m.
[[0;32m  OK  [0m] Started [0;1;39mAvahi mDNS/DNS-SD Stack[0m.
[[0;32m  OK  [0m] Started [0;1;39mBluetooth service[0m.
[[0;32m  OK  [0m] Started [0;1;39mSwitcheroo Control Proxy service[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBluetooth[0m.
         Starting [0;1;39mSave/Restore Sound Card State[0m...
[[0;32m  OK  [0m] Started [0;1;39mMake remote CUPS printers available locally[0m.
[[0;32m  OK  [0m] Started [0;1;39mWPA supplicant[0m.
[[0;32m  OK  [0m] Finished [0;1;39mGRUB failed boot detection[0m.
[[0;32m  OK  [0m] Finished [0;1;39mSave/Restore Sound Card State[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSound Card[0m.
[[0;32m  OK  [0m] Started [0;1;39mThermal Daemon Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mAuthorization Manager[0m.
         Starting [0;1;39mModem Manager[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork[0m.
         Starting [0;1;39mNetwork Manager Wait Online[0m...
         Starting [0;1;39mOpenVPN service[0m...
         Starting [0;1;39mPermit User Sessions[0m...
[[0;32m  OK  [0m] Finished [0;1;39mOpenVPN service[0m.
         Starting [0;1;39mHostname Service[0m...
[[0;32m  OK  [0m] Finished [0;1;39mPermit User Sessions[0m.
         Starting [0;1;39mHold until boot process finishes up[0m...
[[0;32m  OK  [0m] Started [0;1;39mAccounts Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mDisk Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mModem Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mHostname Service[0m.
[[0;32m  OK  [0m] Finished [0;1;39mDetect the availa&#8230; deal with any system changes[0m.
         Starting [0;1;39mGNOME Display Manager[0m...
         Starting [0;1;39mNetwork Manager Script Dispatcher Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager Script Dispatcher Service[0m.
[[0;32m  OK  [0m] Finished [0;1;39mNetwork Manager Wait Online[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork is Online[0m.
         Starting [0;1;39mTool to automatic&#8230;mit kernel crash signatures[0m...
[[0;32m  OK  [0m] Started [0;1;39mcrash report submission daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mTool to automatica&#8230;ubmit kernel crash signatures[0m.
[[0;32m  OK  [0m] Started [0;1;39mDispatcher daemon for systemd-networkd[0m.
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of backlight:acpi_video0[0m...
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of backlight:amdgpu_bl0[0m...
[[0;1;31mFAILED[0m] Failed to start [0;1;39mLoad/Save Screen Backlight Brightness of backlight:acpi_video0[0m.
See 'systemctl status [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e' for details.
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen Backlight Brightness of backlight:amdgpu_bl0[0m.
[[0;32m  OK  [0m] Started [0;1;39mGNOME Display Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mLogin Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mUnattended Upgrades Shutdown[0m.
------------ Wed May 11 01:55:53 BST 2022 ------------
[[0;32m  OK  [0m] Finished [0;1;39mFlush Journal to Persistent Storage[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for core20, revision 1328[0m.
[[0;32m  OK  [0m] Started [0;1;39mShow Plymouth Boot Screen[0m.
[[0;32m  OK  [0m] Started [0;1;39mForward Password Requests to Plymouth Directory Watch[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mLocal Encrypted Volumes[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snapd, revision 14978[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for core20, revision 1434[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snapd, revision 15534[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gtk-common-themes, revision 1519[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gnome-3-38-2004, revision 99[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mLoad/Save RF Kill Switch Status /dev/rfkill Watch[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snap-store, revision 558[0m.
         Starting [0;1;39mLoad/Save RF Kill Switch Status[0m...
[[0;32m  OK  [0m] Started [0;1;39mLoad/Save RF Kill Switch Status[0m.
[[0;32m  OK  [0m] Found device [0;1;39mSAMSUNG MZVLQ&#8230;00 EFI\x20System\x20Partition[0m.
         Starting [0;1;39mFile System Check&#8230;/dev/disk/by-uuid/98FC-444E[0m...
[[0;32m  OK  [0m] Started [0;1;39mFile System Check Daemon to report status[0m.
[[0;32m  OK  [0m] Finished [0;1;39mFile System Check&#8230;n /dev/disk/by-uuid/98FC-444E[0m.
         Mounting [0;1;39m/boot/efi[0m...
[[0;32m  OK  [0m] Created slice [0;1;39msystem-systemd\x2dbacklight.slice[0m.
         Starting [0;1;39mLoad/Save Screen &#8230;ss of backlight:acpi_video0[0m...
         Starting [0;1;39mLoad/Save Screen &#8230;of leds:asus::kbd_backlight[0m...
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen &#8230;ness of backlight:acpi_video0[0m.
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen &#8230;s of leds:asus::kbd_backlight[0m.
[[0;32m  OK  [0m] Mounted [0;1;39m/boot/efi[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mLocal File Systems[0m.
         Starting [0;1;39mLoad AppArmor profiles[0m...
         Starting [0;1;39mSet console font and keymap[0m...
         Starting [0;1;39mTell Plymouth To Write Out Runtime Data[0m...
         Starting [0;1;39mCreate Volatile Files and Directories[0m...
[[0;32m  OK  [0m] Finished [0;1;39mSet console font and keymap[0m.
[[0;32m  OK  [0m] Finished [0;1;39mTell Plymouth To Write Out Runtime Data[0m.
[[0;32m  OK  [0m] Finished [0;1;39mCreate Volatile Files and Directories[0m.
         Starting [0;1;39mNetwork Name Resolution[0m...
         Starting [0;1;39mNetwork Time Synchronization[0m...
         Starting [0;1;39mUpdate UTMP about System Boot/Shutdown[0m...
         Starting [0;1;39mTell Plymouth To Write Out Runtime Data[0m...
[[0;32m  OK  [0m] Finished [0;1;39mUpdate UTMP about System Boot/Shutdown[0m.
------------ Wed May 11 01:55:53 BST 2022 ------------
[[0;32m  OK  [0m] Finished [0;1;39mTell Plymouth To Write Out Runtime Data[0m.
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor profiles[0m.
         Starting [0;1;39mLoad AppArmor pro&#8230;managed internally by snapd[0m...
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor pro&#8230;s managed internally by snapd[0m.
[[0;32m  OK  [0m] Started [0;1;39mNetwork Time Synchronization[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Initialization[0m.
[[0;32m  OK  [0m] Started [0;1;39mACPI Events Check[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger to poll fo&#8230;y enabled on GCP LTS non-pro)[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily Cleanup of Temporary Directories[0m.
[[0;32m  OK  [0m] Started [0;1;39mUbuntu Advantage Timer for running repeated jobs[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mPaths[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Set[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Synchronized[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger anacron every hour[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt download activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt upgrade and clean activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mPeriodic ext4 Onli&#8230;ata Check for All Filesystems[0m.
[[0;32m  OK  [0m] Started [0;1;39mDiscard unused blocks once a week[0m.
[[0;32m  OK  [0m] Started [0;1;39mRefresh fwupd metadata regularly[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily rotation of log files[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily man-db regeneration[0m.
[[0;32m  OK  [0m] Started [0;1;39mMessage of the Day[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mTimers[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mACPID Listen Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mAvahi mDNS/DNS-SD Stack Activation Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mD-Bus System Message Bus Socket[0m.
         Starting [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mUUID daemon activation socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSockets[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBasic System[0m.
         Starting [0;1;39mAccounts Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mACPI event daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mRun anacron jobs[0m.
         Starting [0;1;39mLSB: automatic crash report generation[0m...
         Starting [0;1;39mAvahi mDNS/DNS-SD Stack[0m...
         Starting [0;1;39mBluetooth service[0m...
[[0;32m  OK  [0m] Started [0;1;39mRegular background program processing daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mD-Bus System Message Bus[0m.
         Starting [0;1;39mNetwork Manager[0m...
[[0;32m  OK  [0m] Started [0;1;39mSave initial kernel messages after boot[0m.
         Starting [0;1;39mRemove Stale Onli&#8230;t4 Metadata Check Snapshots[0m...
[[0;32m  OK  [0m] Reached target [0;1;39mLogin Prompts[0m.
         Starting [0;1;39mDetect the availa&#8230;eal with any system changes[0m...
         Starting [0;1;39mRecord successful boot for GRUB[0m...
[[0;32m  OK  [0m] Started [0;1;39mirqbalance daemon[0m.
         Starting [0;1;39mDispatcher daemon for systemd-networkd[0m...
[[0;32m  OK  [0m] Started [0;1;39mSet the CPU Frequency Scaling governor[0m.
         Starting [0;1;39mAuthorization Manager[0m...
         Starting [0;1;39mRestore /etc/reso&#8230; the ppp link was shut down[0m...
         Starting [0;1;39mSystem Logging Service[0m...
         Starting [0;1;39mSecure Boot updates for DB and DBX[0m...
         Starting [0;1;39mSnap Daemon[0m...
         Starting [0;1;39mSwitcheroo Control Proxy service[0m...
         Starting [0;1;39mLogin Service[0m...
         Starting [0;1;39mThermal Daemon Service[0m...
         Starting [0;1;39mDisk Manager[0m...
         Starting [0;1;39mWPA supplicant[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Name Resolution[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRemove Stale Onli&#8230;ext4 Metadata Check Snapshots[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRestore /etc/reso&#8230;re the ppp link was shut down[0m.
[[0;32m  OK  [0m] Started [0;1;39mSystem Logging Service[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mHost and Network Name Lookups[0m.
[[0;32m  OK  [0m] Finished [0;1;39mDetect the availa&#8230; deal with any system changes[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRecord successful boot for GRUB[0m.
         Starting [0;1;39mGRUB failed boot detection[0m...
[[0;32m  OK  [0m] Finished [0;1;39mSecure Boot updates for DB and DBX[0m.
[[0;32m  OK  [0m] Started [0;1;39mLSB: automatic crash report generation[0m.
[[0;32m  OK  [0m] Started [0;1;39mBluetooth service[0m.
[[0;32m  OK  [0m] Started [0;1;39mAvahi mDNS/DNS-SD Stack[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBluetooth[0m.
[[0;32m  OK  [0m] Started [0;1;39mMake remote CUPS printers available locally[0m.
[[0;32m  OK  [0m] Started [0;1;39mSwitcheroo Control Proxy service[0m.
         Starting [0;1;39mSave/Restore Sound Card State[0m...
[[0;32m  OK  [0m] Started [0;1;39mWPA supplicant[0m.
[[0;32m  OK  [0m] Finished [0;1;39mGRUB failed boot detection[0m.
[[0;32m  OK  [0m] Finished [0;1;39mSave/Restore Sound Card State[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSound Card[0m.
[[0;32m  OK  [0m] Started [0;1;39mThermal Daemon Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mAuthorization Manager[0m.
         Starting [0;1;39mModem Manager[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork[0m.
         Starting [0;1;39mNetwork Manager Wait Online[0m...
         Starting [0;1;39mOpenVPN service[0m...
         Starting [0;1;39mPermit User Sessions[0m...
[[0;32m  OK  [0m] Finished [0;1;39mOpenVPN service[0m.
         Starting [0;1;39mHostname Service[0m...
[[0;32m  OK  [0m] Finished [0;1;39mPermit User Sessions[0m.
         Starting [0;1;39mGNOME Display Manager[0m...
         Starting [0;1;39mHold until boot process finishes up[0m...
[[0;32m  OK  [0m] Started [0;1;39mAccounts Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mDisk Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mModem Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mHostname Service[0m.
         Starting [0;1;39mNetwork Manager Script Dispatcher Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager Script Dispatcher Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mLogin Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mUnattended Upgrades Shutdown[0m.
[[0;32m  OK  [0m] Started [0;1;39mDispatcher daemon for systemd-networkd[0m.
[[0;32m  OK  [0m] Started [0;1;39mSnap Daemon[0m.
         Starting [0;1;39mWait until snapd is fully seeded[0m...
         Starting [0;1;39mTime & Date Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mTime & Date Service[0m.
[[0;32m  OK  [0m] Finished [0;1;39mWait until snapd is fully seeded[0m.
[[0;32m  OK  [0m] Finished [0;1;39mNetwork Manager Wait Online[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork is Online[0m.
         Starting [0;1;39mTool to automatic&#8230;mit kernel crash signatures[0m...
[[0;32m  OK  [0m] Started [0;1;39mcrash report submission daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mTool to automatica&#8230;ubmit kernel crash signatures[0m.
------------ Wed May 11 02:03:25 BST 2022 ------------
[[0;32m  OK  [0m] Started [0;1;39mShow Plymouth Boot Screen[0m.
[[0;32m  OK  [0m] Started [0;1;39mForward Password Requests to Plymouth Directory Watch[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mLocal Encrypted Volumes[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for core20, revision 1434[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for core20, revision 1328[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snapd, revision 15534[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mLoad/Save RF Kill Switch Status /dev/rfkill Watch[0m.
         Starting [0;1;39mLoad/Save RF Kill Switch Status[0m...
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snap-store, revision 558[0m.
[[0;32m  OK  [0m] Created slice [0;1;39msystem-systemd\x2dbacklight.slice[0m.
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of leds:asus::kbd_backlight[0m...
[[0;32m  OK  [0m] Started [0;1;39mLoad/Save RF Kill Switch Status[0m.
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen Backlight Brightness of leds:asus::kbd_backlight[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gnome-3-38-2004, revision 99[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for snapd, revision 14978[0m.
[[0;32m  OK  [0m] Mounted [0;1;39mMount unit for gtk-common-themes, revision 1519[0m.
[[0;32m  OK  [0m] Found device [0;1;39mSAMSUNG MZVLQ&#8230;00 EFI\x20System\x20Partition[0m.
         Starting [0;1;39mFile System Check&#8230;/dev/disk/by-uuid/98FC-444E[0m...
[[0;32m  OK  [0m] Started [0;1;39mFile System Check Daemon to report status[0m.
[[0;32m  OK  [0m] Finished [0;1;39mFile System Check&#8230;n /dev/disk/by-uuid/98FC-444E[0m.
         Mounting [0;1;39m/boot/efi[0m...
[[0;32m  OK  [0m] Mounted [0;1;39m/boot/efi[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mLocal File Systems[0m.
         Starting [0;1;39mLoad AppArmor profiles[0m...
         Starting [0;1;39mSet console font and keymap[0m...
         Starting [0;1;39mTell Plymouth To Write Out Runtime Data[0m...
         Starting [0;1;39mCreate Volatile Files and Directories[0m...
[[0;32m  OK  [0m] Finished [0;1;39mSet console font and keymap[0m.
[[0;32m  OK  [0m] Finished [0;1;39mTell Plymouth To Write Out Runtime Data[0m.
[[0;32m  OK  [0m] Finished [0;1;39mCreate Volatile Files and Directories[0m.
         Starting [0;1;39mNetwork Name Resolution[0m...
         Starting [0;1;39mNetwork Time Synchronization[0m...
         Starting [0;1;39mUpdate UTMP about System Boot/Shutdown[0m...
[[0;32m  OK  [0m] Finished [0;1;39mUpdate UTMP about System Boot/Shutdown[0m.
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor profiles[0m.
         Starting [0;1;39mLoad AppArmor pro&#8230;managed internally by snapd[0m...
[[0;32m  OK  [0m] Finished [0;1;39mLoad AppArmor pro&#8230;s managed internally by snapd[0m.
[[0;32m  OK  [0m] Started [0;1;39mNetwork Time Synchronization[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Initialization[0m.
[[0;32m  OK  [0m] Started [0;1;39mACPI Events Check[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger to poll fo&#8230;y enabled on GCP LTS non-pro)[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily Cleanup of Temporary Directories[0m.
[[0;32m  OK  [0m] Started [0;1;39mUbuntu Advantage Timer for running repeated jobs[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mPaths[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Set[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSystem Time Synchronized[0m.
[[0;32m  OK  [0m] Started [0;1;39mTrigger anacron every hour[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt download activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily apt upgrade and clean activities[0m.
[[0;32m  OK  [0m] Started [0;1;39mPeriodic ext4 Onli&#8230;ata Check for All Filesystems[0m.
[[0;32m  OK  [0m] Started [0;1;39mDiscard unused blocks once a week[0m.
[[0;32m  OK  [0m] Started [0;1;39mRefresh fwupd metadata regularly[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily rotation of log files[0m.
[[0;32m  OK  [0m] Started [0;1;39mDaily man-db regeneration[0m.
[[0;32m  OK  [0m] Started [0;1;39mMessage of the Day[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mTimers[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mACPID Listen Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mAvahi mDNS/DNS-SD Stack Activation Socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mD-Bus System Message Bus Socket[0m.
         Starting [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mUUID daemon activation socket[0m.
[[0;32m  OK  [0m] Listening on [0;1;39mSocket activation for snappy daemon[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSockets[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBasic System[0m.
         Starting [0;1;39mAccounts Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mACPI event daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mRun anacron jobs[0m.
         Starting [0;1;39mLSB: automatic crash report generation[0m...
         Starting [0;1;39mAvahi mDNS/DNS-SD Stack[0m...
         Starting [0;1;39mBluetooth service[0m...
[[0;32m  OK  [0m] Started [0;1;39mRegular background program processing daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mCUPS Scheduler[0m.
[[0;32m  OK  [0m] Started [0;1;39mD-Bus System Message Bus[0m.
         Starting [0;1;39mNetwork Manager[0m...
[[0;32m  OK  [0m] Started [0;1;39mSave initial kernel messages after boot[0m.
         Starting [0;1;39mRemove Stale Onli&#8230;t4 Metadata Check Snapshots[0m...
[[0;32m  OK  [0m] Reached target [0;1;39mLogin Prompts[0m.
         Starting [0;1;39mDetect the availa&#8230;eal with any system changes[0m...
         Starting [0;1;39mRecord successful boot for GRUB[0m...
[[0;32m  OK  [0m] Started [0;1;39mirqbalance daemon[0m.
         Starting [0;1;39mDispatcher daemon for systemd-networkd[0m...
[[0;32m  OK  [0m] Started [0;1;39mSet the CPU Frequency Scaling governor[0m.
         Starting [0;1;39mAuthorization Manager[0m...
         Starting [0;1;39mRestore /etc/reso&#8230; the ppp link was shut down[0m...
         Starting [0;1;39mSystem Logging Service[0m...
         Starting [0;1;39mSecure Boot updates for DB and DBX[0m...
         Starting [0;1;39mSnap Daemon[0m...
         Starting [0;1;39mSwitcheroo Control Proxy service[0m...
         Starting [0;1;39mLogin Service[0m...
         Starting [0;1;39mThermal Daemon Service[0m...
         Starting [0;1;39mDisk Manager[0m...
         Starting [0;1;39mWPA supplicant[0m...
[[0;32m  OK  [0m] Started [0;1;39mNetwork Name Resolution[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRemove Stale Online ext4 Metadata Check Snapshots[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRestore /etc/resolv.conf if the system crashed before the ppp link was shut down[0m.
[[0;32m  OK  [0m] Started [0;1;39mSystem Logging Service[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mHost and Network Name Lookups[0m.
[[0;32m  OK  [0m] Started [0;1;39mBluetooth service[0m.
[[0;32m  OK  [0m] Started [0;1;39mAvahi mDNS/DNS-SD Stack[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mBluetooth[0m.
[[0;32m  OK  [0m] Started [0;1;39mMake remote CUPS printers available locally[0m.
[[0;32m  OK  [0m] Finished [0;1;39mRecord successful boot for GRUB[0m.
[[0;32m  OK  [0m] Finished [0;1;39mDetect the available GPUs and deal with any system changes[0m.
[[0;32m  OK  [0m] Started [0;1;39mSwitcheroo Control Proxy service[0m.
         Starting [0;1;39mSave/Restore Sound Card State[0m...
         Starting [0;1;39mGRUB failed boot detection[0m...
[[0;32m  OK  [0m] Started [0;1;39mLSB: automatic crash report generation[0m.
[[0;32m  OK  [0m] Finished [0;1;39mSecure Boot updates for DB and DBX[0m.
[[0;32m  OK  [0m] Finished [0;1;39mSave/Restore Sound Card State[0m.
[[0;32m  OK  [0m] Started [0;1;39mAuthorization Manager[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mSound Card[0m.
         Starting [0;1;39mModem Manager[0m...
[[0;32m  OK  [0m] Started [0;1;39mWPA supplicant[0m.
[[0;32m  OK  [0m] Started [0;1;39mThermal Daemon Service[0m.
[[0;32m  OK  [0m] Finished [0;1;39mGRUB failed boot detection[0m.
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork[0m.
         Starting [0;1;39mNetwork Manager Wait Online[0m...
         Starting [0;1;39mOpenVPN service[0m...
         Starting [0;1;39mPermit User Sessions[0m...
[[0;32m  OK  [0m] Finished [0;1;39mOpenVPN service[0m.
         Starting [0;1;39mHostname Service[0m...
[[0;32m  OK  [0m] Finished [0;1;39mPermit User Sessions[0m.
         Starting [0;1;39mGNOME Display Manager[0m...
         Starting [0;1;39mHold until boot process finishes up[0m...
[[0;32m  OK  [0m] Started [0;1;39mAccounts Service[0m.
[[0;32m  OK  [0m] Started [0;1;39mDisk Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mModem Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mHostname Service[0m.
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of backlight:acpi_video0[0m...
         Starting [0;1;39mLoad/Save Screen Backlight Brightness of backlight:amdgpu_bl0[0m...
[[0;1;31mFAILED[0m] Failed to start [0;1;39mLoad/Save Screen Backlight Brightness of backlight:acpi_video0[0m.
See 'systemctl status [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e' for details.
[[0;32m  OK  [0m] Finished [0;1;39mLoad/Save Screen Backlight Brightness of backlight:amdgpu_bl0[0m.
         Starting [0;1;39mNetwork Manager Script Dispatcher Service[0m...
[[0;32m  OK  [0m] Started [0;1;39mGNOME Display Manager[0m.
[[0;32m  OK  [0m] Started [0;1;39mNetwork Manager Script Dispatcher Service[0m.
[[0;32m  OK  [0m] Finished [0;1;39mNetwork Manager Wait Online[0m.
[[0;32m  OK  [0m] Reached target [0;1;39mNetwork is Online[0m.
         Starting [0;1;39mTool to automatically collect and submit kernel crash signatures[0m...
[[0;32m  OK  [0m] Started [0;1;39mcrash report submission daemon[0m.
[[0;32m  OK  [0m] Started [0;1;39mTool to automatically collect and submit kernel crash signatures[0m.
[[0;32m  OK  [0m] Started [0;1;39mDispatcher daemon for systemd-networkd[0m.]
```

If anyone has any ideas I'd be forever grateful!

---

### Post by CharlesA on 2022-05-11
I have moved your post to it's own thread.

I don't see much info to help you with this suspend issue.

I don't know if you are suspending to RAM or suspending to disk by default, but these links might be worth a look, regardless:
For suspending to RAM:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

For suspending to disk (I think this is normally how it works):
[https://wiki.ubuntu.com/DebuggingKernelHibernate](https://wiki.ubuntu.com/DebuggingKernelHibernate)

---

### Post by laurel798 on 2022-05-12
Thank you for creating a new thread for this!

---

