---
title: "So tell me if you heard this one already.. The other day i broke my laptop.."
date: 2024-07-28
forum: General Help
---

### Post by nariub on 2024-07-28
Backstory is normal 
Friday morning just beating about on the internet and I thought..  hey i haven't cleaned up my boot partition in a while..  (see where this is going yet?)

i wrote a script years ago when my boot part was so much smaller (its 1G now, different story) 
it goes and looks at the list of installed kernels and does a apt purge on them until i have only 5 left..

so i run it .. whaaa..   i have 72 kernels.. this is going to take a minute..   my attention wanes   and i discover a thing that has not historically been a big issue
the in the list of kernels   -116- comes right after -11-  but before -20-  so  shorter story.. i deleted my active kernel on my 22.04 ... solidly updated and reliable laptop

so black screen ..  i get it.. so get an installation disc (actually a USB, because, surprisingly, the install ISO doesnt fit on a 4.7Gb DVD-R anymore)
booted
went to try ubuntu
pulled up a terminal
opened my LUKS partition (whole disc encryption)
mounted my LUKS part
mounted my boot part
--bind the dev  dev/pts sys and proc
chroot over to my broken system

and heres where the wierd parts go.. i tried to reinstall the 5.15.0-116  and 117  (and tried 6.5.0-18 too)  apt install hangs installing any of the kernels just stops after generating the initramfs
whole thing pauses and never completes ...   so trying again says dpkg is hung 
so i do dpkg --configure -a and that also hangs in the same place  

i can manually run update-initramfs -k all -c and it completes fine
i can manually run update-grub and it works fine

i can successfully uninstall kernels all day and it clears the apt process but for some reason it just will not complete an install

booting my laptop now times out opening my hd's 
it drops me to initramfs prompt 
but i can cryptsetup open /dev/sda2 rootfs and it prompts for a password and lets me see the contents
if i exit busybox it prompts me for my LUKS password again.. which makes me kinda happy  but then just goes again into blinking cursor and staring at me.. 

i tried reinstalling grub ... 

i thought i would run the install disc and just -re-install- the OS but this morning the install disc doesnt even detect the existing 22.04 installation on the disc so.. back to fixing the kernel install


Edit: 
found waiting an hour got dpkg to complete 
Also 2 hours and i could complete apt install --reinstall Linux-generic
But still hangs at initramfs 

anybody?
I feel like i am missing something, i am getting older and this happens.

i have an old Latitude E6520
i have a 1G boot part at /dev/sda1
i have a 480G LUKS part at /dev/sda2
i have been mounting them by UUID for a while in FSTAB
and for what its worth i am also encrypting the user directories too.., so pulling the data off to an external drive and recreating it might be a little wierd too.. never tried that before..


my last boot.log says
```
------------ Fri Jul 26 11:32:42 MST 2024 ------------
[  OK  ] Started Show Plymouth Boot Screen.
[  OK  ] Started Forward Password Requests to Plymouth Directory Watch.
[  OK  ] Created slice Slice /system/systemd-backlight.
         Starting Load/Save Screen Backlight Brightness of backlight:acpi_video0...
[  OK  ] Finished Load/Save Screen Backlight Brightness of backlight:acpi_video0.
[  OK  ] Found device SSD_PLUS_480GB 1.
         Starting File System Check on /dev/disk/by-uuid/1e74deba-b828-4455-ace9-84b92d9174ff...
[  OK  ] Found device SSD_PLUS_480GB 2.
         Starting Cryptography Setup for sda5_crypt...
[  OK  ] Started File System Check Daemon to report status.
[  OK  ] Finished File System Check on /dev/disk/by-uuid/1e74deba-b828-4455-ace9-84b92d9174ff.
[FAILED] Failed to start Cryptography Setup for sda5_crypt.
See 'systemctl status systemd-cryptsetup@sda5_crypt.service' for details.
[DEPEND] Dependency failed for Local Encrypted Volumes.
[  OK  ] Reached target Block Device Preparation for /dev/mapper/sda5_crypt.
[  OK  ] Stopped target Block Device Preparation for /dev/mapper/sda5_crypt.
[ TIME ] Timed out waiting for device /dev/mapper/cryptswap1.
[DEPEND] Dependency failed for /dev/mapper/cryptswap1.
[DEPEND] Dependency failed for Swaps.
[  OK  ] Reached target System Initialization.
[  OK  ] Started ACPI Events Check.
[  OK  ] Started CUPS Scheduler.
[  OK  ] Started resolvconf-pull-resolved.path.
[  OK  ] Started Start whoopsie on modification of the /var/crash directory.
[  OK  ] Started Trigger anacron every hour.
[  OK  ] Started Daily apt download activities.
[  OK  ] Started Daily apt upgrade and clean activities.
[  OK  ] Started Daily dpkg database backup timer.
[  OK  ] Started Periodic ext4 Online Metadata Check for All Filesystems.
[  OK  ] Started Discard unused blocks once a week.
[  OK  ] Started Refresh fwupd metadata regularly.
[  OK  ] Started Daily rotation of log files.
[  OK  ] Started Daily man-db regeneration.
[  OK  ] Started Message of the Day.
[  OK  ] Started Update the plocate database daily.
[  OK  ] Started Daily Cleanup of Temporary Directories.
[  OK  ] Started Ubuntu Pro Timer for running repeated jobs.
[  OK  ] Reached target Path Units.
[  OK  ] Listening on ACPID Listen Socket.
[  OK  ] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
[  OK  ] Listening on CUPS Scheduler.
[  OK  ] Listening on D-Bus System Message Bus Socket.
[  OK  ] Listening on PC/SC Smart Card Daemon Activation Socket.
         Starting Socket activation for snappy daemon...
[  OK  ] Listening on UUID daemon activation socket.
[  OK  ] Listening on Socket activation for snappy daemon.
[  OK  ] Reached target Socket Units.
[  OK  ] Reached target Basic System.
[  OK  ] Started ACPI event daemon.
[  OK  ] Started Run anacron jobs.
         Starting LSB: automatic crash report generation...
         Starting Avahi mDNS/DNS-SD Stack...
         Starting Bluetooth management mechanism...
         Starting Bluetooth service...
         Starting Clam AntiVirus userspace daemon...
[  OK  ] Started D-Bus System Message Bus.
         Starting Network Manager...
[  OK  ] Started Save initial kernel messages after boot.
         Starting Remove Stale Online ext4 Metadata Check Snapshots...
[  OK  ] Reached target Login Prompts.
         Starting Detect the available GPUs and deal with any system changes...
         Starting Record successful boot for GRUB...
[  OK  ] Started irqbalance daemon.
         Starting Initialize hardware monitoring sensors...
         Starting Dispatcher daemon for systemd-networkd...
         Starting LSB: Set the CPU Frequency Scaling governor to "ondemand"...
         Starting Authorization Manager...
         Starting Power Profiles daemon...
         Starting LSB: Run /etc/rc.local if it exist...
         Starting resolvconf-pull-resolved.service...
         Starting System Logging Service...
[  OK  ] Reached target Preparation for Logins.
         Starting Wait until snapd is fully seeded...
         Starting Snap Daemon...
[  OK  ] Reached target User and Group Name Lookups.
[DEPEND] Dependency failed for SSSD NSS Service responder socket.
[DEPEND] Dependency failed for SSSD AutoFS Service responder socket.
[DEPEND] Dependency failed for SSSD PAC Service responder socket.
[DEPEND] Dependency failed for SSSD PAM Service responder private socket.
[DEPEND] Dependency failed for SSSD PAM Service responder socket.
[DEPEND] Dependency failed for SSSD SSH Service responder socket.
[DEPEND] Dependency failed for SSSD Sudo Service responder socket.
         Starting Accounts Service...
         Starting Deferred execution scheduler...
[  OK  ] Started Regular background program processing daemon.
         Starting Switcheroo Control Proxy service...
         Starting User Login Management...
         Starting Thermal Daemon Service...
         Starting Disk Manager...
         Starting LSB: This services starts and stops the USB Arbitrator....
         Starting WPA supplicant...
[  OK  ] Started Deferred execution scheduler.
[  OK  ] Started Clam AntiVirus userspace daemon.
[  OK  ] Finished Initialize hardware monitoring sensors.
[  OK  ] Started System Logging Service.
[  OK  ] Finished Record successful boot for GRUB.
         Starting GRUB failed boot detection...
[  OK  ] Started LSB: Run /etc/rc.local if it exist.
[  OK  ] Finished Remove Stale Online ext4 Metadata Check Snapshots.
[  OK  ] Started LSB: Set the CPU Frequency Scaling governor to "ondemand".
[  OK  ] Finished GRUB failed boot detection.
[  OK  ] Started LSB: automatic crash report generation.
[  OK  ] Finished resolvconf-pull-resolved.service.
[  OK  ] Started Switcheroo Control Proxy service.
         Starting Save/Restore Sound Card State...
[  OK  ] Started Avahi mDNS/DNS-SD Stack.
[  OK  ] Started Thermal Daemon Service.
[  OK  ] Started WPA supplicant.
[  OK  ] Started Network Manager.
[  OK  ] Finished Save/Restore Sound Card State.
[  OK  ] Reached target Network.
[  OK  ] Reached target Sound Card.
         Starting Network Manager Wait Online...
         Starting CUPS Scheduler...
         Starting OpenVPN service...
[  OK  ] Started Service for snap application canonical-livepatch.canonical-livepatchd.
[  OK  ] Started Service for snap application cups.cups-browsed.
[  OK  ] Started Service for snap application cups.cupsd.
         Starting Permit User Sessions...
[  OK  ] Finished OpenVPN service.
[  OK  ] Started Authorization Manager.
[  OK  ] Started Power Profiles daemon.
[  OK  ] Started Bluetooth service.
[  OK  ] Reached target Bluetooth Support.
         Starting Modem Manager...
         Starting Hostname Service...
[  OK  ] Finished Permit User Sessions.
         Starting Hold until boot process finishes up...
         Starting Forward Password Requests to Wall...
[  OK  ] Stopped Forward Password Requests to Plymouth Directory Watch.
         Stopping Forward Password Requests to Plymouth...
[  OK  ] Stopped Forward Password Requests to Plymouth.
[  OK  ] Started Forward Password Requests to Wall.
[  OK  ] Started User Login Management.
[  OK  ] Started Unattended Upgrades Shutdown.
[  OK  ] Started Accounts Service.
         Starting Manage, Install and Generate Color Profiles...
[  OK  ] Started Dispatcher daemon for systemd-networkd.
[  OK  ] Started Hostname Service.
[  OK  ] Started Modem Manager.
[  OK  ] Started LSB: This services starts and stops the USB Arbitrator..
[  OK  ] Started Manage, Install and Generate Color Profiles.
         Starting Network Manager Script Dispatcher Service...
[  OK  ] Started Network Manager Script Dispatcher Service.
[  OK  ] Started Disk Manager.
[  OK  ] Started CUPS Scheduler.
[  OK  ] Started Bluetooth management mechanism.
         Starting resolvconf-pull-resolved.service...
[  OK  ] Finished resolvconf-pull-resolved.service.
[  OK  ] Finished Network Manager Wait Online.
[  OK  ] Reached target Network is Online.
[  OK  ] Started Download data for packages that failed at package install time.
[  OK  ] Started Check to see whether there is a new version of Ubuntu available.
[  OK  ] Reached target Timer Units.
[  OK  ] Started ClamAV virus database updater.
[  OK  ] Started Make remote CUPS printers available locally.
         Starting LSB: disk temperature monitoring daemon...
         Starting Tool to automatically collect and submit kernel crash signatures...
         Starting LSB: This service starts and stops VMware services...
[  OK  ] Started crash report submission.
[  OK  ] Started LSB: disk temperature monitoring daemon.
[  OK  ] Started Tool to automatically collect and submit kernel crash signatures.
[FAILED] Failed to start LSB: This service starts and stops VMware services.
See 'systemctl status vmware.service' for details.
[  OK  ] Started Snap Daemon.
         Starting Time & Date Service...
[  OK  ] Started Time & Date Service.
[  OK  ] Finished Wait until snapd is fully seeded.
[  OK  ] Finished Detect the available GPUs and deal with any system changes.
         Starting GNOME Display Manager...
[  OK  ] Started GNOME Display Manager.
```




Thanks
Marion

---

### Post by TheFu on 2024-07-29
I'd start by assuming the storage device is failing. I'd run all the normal disk checks on it to see if there are any clear issues.  I'd spend $30 to get a new OS SSD and move on.  HDDs fail all the time.

And I'd do a better job at keeping the number of kernels down to under 4 total going forward.  Even with 1GB /boot, I find it hard to believe that more than 8 full kernels will fit into that amount of storage.  Each kernel seems to need 140MB on my 22.04 system.  3 kernels are using 536MB here.

---

### Post by grahammechanical on 2024-07-29
This command will remove excess Linux kernels leaving just two with a recovery mode option for each of them.

```
sudo apt autoremove
```

Alternatively, if we run Software Updater it will run apt update; apt upgrade and apt autoremove.

I have also noted that after running apt update and apt upgrade in the terminal I get information about packages that can be removed with apt autoremove. Sometimes, Software Updater will load and inform me that there is updated software available which is in reality software packages including kernels that can be remove. Click yes to that and Software Updater will remove those packages.

Regards

---

### Post by TheFu on 2024-07-29
> **grahammechanical said:**
> This command will remove excess Linux kernels leaving just two with a recovery mode option for each of them.

```
sudo apt autoremove
```
 

I've seen different results.  It leaves 2 kernels for each kernel line, so if you have v5.4.x, v5.10.x, v5.15.x, and some version of 6.x.x, then there will be 8 kernels.  Each kernel line is considered separately.  IME.

---

### Post by nariub on 2024-07-29
so first
thank you for the replies 

Second the sandisk ssd hd seems fine and fsck was clean every time 

Progress though

Fun fact
When you chroot and cryptsetup open the LUKS part
Ya gotta use the name from /etec/crypttab
Not rootfs as i was using
It makes initramfs create a bad init image

And lots of patience with kernel installs

Also added a blank line at the end of my crypttab because the Internet said so

Gui dont start but i dont need a liveCD to interact with my system anymore 

Going to reinstall my Nvidia drivers to get my gui back but i think what i was missing was the sd5_crypt instead of rootfs on the cryptsetup line

---

### Post by nariub on 2024-07-29
Oh and i know better than to purge kernels with a script 
But i had a senior moment

---

### Post by nariub on 2024-07-30
Thanks Guys,
Re installed my video drivers and I am back to normal again..

---

