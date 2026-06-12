---
title: "RAIDZ2 pool degrades during/after shutdown."
date: 2023-04-10
forum: General Help
---

### Post by papriak on 2023-04-10
I'm assuming that ZFS has no built-in terms for "gracefully halting" operations before an Ubuntu system shuts off.

Is there a way to add those parameters to the shutdown/poweroff command set, or maybe another way to prevent my pool from needing to be restored each time I turn the system off?

---

### Post by #&amp;thj^% on 2023-04-10
Far to vague, could you add some flesh/substance to your query:
Examples would be how do i keep my rpool/bpool/tank/storage-pools freshly mounted on boot.
If your speaking of a storage pools, I have no problems with:
Export each pool via zpool export <name of pool>, and them import them via 
```

zpool import -f -R /mnt <name of pool>
```
Is one good example, another path I use is
```
/usr/share/<pool-name>
```
As seen with:
```
/usr/share/pool/
```
```
stat /usr/share/pool
  File: /usr/share/pool
  Size: 2         	Blocks: 2          IO Block: 512    directory
Device: 0,26	Inode: 859532      Links: 2
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-04-09 19:00:09.456215326 -0600
Modify: 2023-04-04 17:01:36.355030934 -0600
Change: 2023-04-04 17:01:36.355030934 -0600
 Birth: 2023-04-04 17:01:36.355030934 -0600


```

---

### Post by MAFoElffen on 2023-04-10
> **papriak said:**
> [COLOR=#ff0000]I'm **assuming**[/COLOR] that ZFS has no built-in terms for "gracefully halting" operations before an Ubuntu system shuts off.

Is there a way to add those parameters to the shutdown/poweroff command set, or maybe another way to prevent my pool from needing to be restored each time I turn the system off?
I feel the 'assuming' part of that is incorrect. ZFS is a copy-on-write (COW) filesystem. It is robust and trust worthy. It has been around a while and had things worked out to ensure that. It does take a hit on performance to ensure that.

I am with 1fallen in that I also do not have a problem with my pools, nor RAIDZ members shutting down "gracefully". The only times I've ever had a problem is when they have inadvertently halted occasionally, other than normal shutdown = Power Outages... or after a system crash because I purposely pushed the system much too far, doing 'some things'. During normal shutdown, the system will flush buffers and unmount the ZFS filesystems automatically. It you turn off (remove) 'quiet' from the Grub2 kernel boot parameters (which I do on my installs/configs), pay attention to the system messages, when it shuts down and you will see massage about "waiting for the pools to shutdown... It does take a bit longer (then other filesystems) to for those processes to finish during the shutdown process.
 
I think both 1fallen and I do caching, so every once in a while, if that a problem happens, where it couldn't shutdown gracefully, then you will get an cache mount error on boot... Then  I would have to shutdown, temporarily remount my pools and have to export them, to fix the cache's, so that on the next boot when it mounts the tries to use the caches, then it does without errors. 1fallen and I talk allot, and I remember he had to do that occasionally (not often, but once in a blue moon) also. We also both use ZFS RAIDZ and DRAID.

We are both not "normal users", but rather push both our config's trying and doing some push-the-limits kinds of things, testing what is possible, so... Sometimes things happen. We both do "I wonder what would happen if I do this this?' and "I wonder if it can do this?" kinds of things as very day kinds of entertainment. So we both have experience in having to recover from those sorts of events. (LOL) That really isn't something that generally is any kind of consideration during normal use. Normal shutdown has those procedures built in (To close and unmount the filesystem.) 

So I do not understand your statement saying that your "RAIDZ pool *degrades* during/after shutdown..." What problems are you experiencing? Or are you *assuming* that you have a potential problem?

---

### Post by #&amp;thj^% on 2023-04-10
The OP inquired about spinning down drives on occasions in another post: [https://ubuntuforums.org/showthread.php?t=2485780](https://ubuntuforums.org/showthread.php?t=2485780)
Still don't know though....waiting for input from OP

---

### Post by papriak on 2023-04-10
Hello guys, thanks for responding.

I read that ZFS isn't included by default, so perhaps it isn't integrating properly?  My case is that I'm using RAIDZ2 to host a network share, and I'm turning the system off at night.

Each morning after booting the system, I check the status of the pool and one or two disks are always faulted.

@MaFoElffen:  Will typing "Shutdown -quiet" in the terminal show the output, or will I need to alter a file?


Something I hadn't considered yet is that I'm using Webmin to access the system, perhaps that program is sending the wrong commands?

---

### Post by #&amp;thj^% on 2023-04-10
> **papriak said:**
> Hello guys, thanks for responding.

I read that ZFS isn't included by default,
Not True: it dropped in the live-installer due to a bug on 22.04 but it lives and prospers On Ubuntu. (using it now on 23.04 Lunar)
> **papriak said:**
> 
 so perhaps it isn't integrating properly?  My case is that I'm using RAIDZ2 to host a network share, and I'm turning the system off at night.
Mine and MaFoElffen  integrate very nicely, again more info is needed to properly advise you.
> **papriak said:**
> 
Each morning after booting the system, I check the status of the pool and one or two disks are always faulted.
Now you see why I never spin down drives on a zfs-root system, I do shut down at night @ 12:20AM, but all pools are there at boot, unless I tell them not to.
Can we please see:
```
zpool get all
```

---

### Post by papriak on 2023-04-10
I apologize for not being specific, I have much to learn.

@1Fallen:  I'd still like the drives to spin down, but my first priority is that they'll stay stable.


```
root@server:~# zpool get all      
NAME  PROPERTY                       VALUE                          SOURCE
Pool  size                           29.1T                          -
Pool  capacity                       5%                             -
Pool  altroot                        -                              default
Pool  health                         DEGRADED                       -
Pool  guid                           6816464837305634266            -
Pool  version                        -                              default
Pool  bootfs                         -                              default
Pool  delegation                     on                             default
Pool  autoreplace                    off                            default
Pool  cachefile                      -                              default
Pool  failmode                       wait                           default
Pool  listsnapshots                  off                            default
Pool  autoexpand                     off                            default
Pool  dedupratio                     1.00x                          -
Pool  free                           27.5T                          -
Pool  allocated                      1.57T                          -
Pool  readonly                       off                            -
Pool  ashift                         0                              default
Pool  comment                        -                              default
Pool  expandsize                     -                              -
Pool  freeing                        0                              -
Pool  fragmentation                  0%                             -
Pool  leaked                         0                              -
Pool  multihost                      off                            default
Pool  checkpoint                     -                              -
Pool  load_guid                      15611584276955092467           -
Pool  autotrim                       off                            default
Pool  compatibility                  off                            default
Pool  feature@async_destroy          enabled                        local
Pool  feature@empty_bpobj            enabled                        local
Pool  feature@lz4_compress           active                         local
Pool  feature@multi_vdev_crash_dump  enabled                        local
Pool  feature@spacemap_histogram     active                         local
Pool  feature@enabled_txg            active                         local
Pool  feature@hole_birth             active                         local
Pool  feature@extensible_dataset     active                         local
Pool  feature@embedded_data          active                         local
Pool  feature@bookmarks              enabled                        local
Pool  feature@filesystem_limits      enabled                        local
Pool  feature@large_blocks           enabled                        local
Pool  feature@large_dnode            enabled                        local
Pool  feature@sha512                 enabled                        local
Pool  feature@skein                  enabled                        local
Pool  feature@edonr                  enabled                        local
Pool  feature@userobj_accounting     active                         local
Pool  feature@encryption             enabled                        local
Pool  feature@project_quota          active                         local
Pool  feature@device_removal         enabled                        local
Pool  feature@obsolete_counts        enabled                        local
Pool  feature@zpool_checkpoint       enabled                        local
Pool  feature@spacemap_v2            active                         local
Pool  feature@allocation_classes     enabled                        local
Pool  feature@resilver_defer         enabled                        local
Pool  feature@bookmark_v2            enabled                        local
Pool  feature@redaction_bookmarks    enabled                        local
Pool  feature@redacted_datasets      enabled                        local
Pool  feature@bookmark_written       enabled                        local
Pool  feature@log_spacemap           active                         local
Pool  feature@livelist               enabled                        local
Pool  feature@device_rebuild         enabled                        local
Pool  feature@zstd_compress          enabled                        local
Pool  feature@draid                  enabled                        local
```

---

### Post by #&amp;thj^% on 2023-04-10
> **papriak said:**
> I apologize for not being specific, I have much to learn.
No worries, we have all been here a time or two.
> **papriak said:**
> 
@1Fallen:  I'd still like the drives to spin down, but my first priority is that they'll stay stable.
This is the potential risk of automating a spin down IE:
>  DEGRADED
    The virtual device has experienced a failure but can still function. This state is most common when a mirror or RAID-Z device has lost one or more constituent devices. The fault tolerance of the pool might be compromised, as a subsequent fault in another device might be unrecoverable.

This is all the nanny-ism i will preach here. (Moving forward)
It's cheap to find repurposed wood, or Thick plastic and a fan with a dryer duct vent to blow the heat else where.
i never know what state my system is in if I choose to spin a Drive/s down, hopefully that makes some sense.

---

### Post by MAFoElffen on 2023-04-10
At the question directed to me... In the "GRUB_CMDLINE_LINUX_DEFAULT=" line of /etc/default/grub, remove "quiet" and run
```

sudo update-grub

```
or to do that temporarily, at the Grub2 Boot menu, press <E> to get into an edit mode, go down to the line that starts with "linux" and remove the word "quiet", then <Cntrl><X> to boot.

I do that on all my machines. I want to see if there are successes or failures. I don't mind the messages scrolling at bootup to see what is going on.

---

### Post by #&amp;thj^% on 2023-04-10
+1 to the above..
As for why degraded shows, maybe peek at:
```
zpool status -v {option here, or leave empty}
```
Also check space once in while with:
```
zpool get all | grep capacity
```
small example:
```
zpool get all | grep capacity
bpool  capacity                       70%                            -
rpool  capacity                       29%  
```
I keep an eye on my bpool, I test a few kernels. (And Snap shots)

---

### Post by papriak on 2023-04-10
> **MAFoElffen said:**
> At the question directed to me... In the "GRUB_CMDLINE_LINUX_DEFAULT=" line of /etc/default/grub, remove "quiet" and run
```

sudo update-grub

```
or to do that temporarily, at the Grub2 Boot menu, press <E> to get into an edit mode, go down to the line that starts with "linux" and remove the word "quiet", then <Cntrl><X> to boot.

I do that on all my machines. I want to see if there are successes or failures. I don't mind the messages scrolling at bootup to see what is going on.

Is there a way to log the text displayed by the shutdown sequence?

---

### Post by MAFoElffen on 2023-04-11
keep this in mind, that you are looking at the journal of this machine as an example:
```

mafoelffen@Mikes-B460M:~$ sudo zfs list
[sudo] password for mafoelffen: 
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              293M  1.46G       96K  /boot
bpool/BOOT                                         291M  1.46G       96K  none
bpool/BOOT/ubuntu_2cwpns                           291M  1.46G      291M  /boot
datapool                                           697G  2.83T       96K  none
datapool/DATA                                      697G  2.83T      697G  /data
rpool                                             15.4G   876G       96K  /
rpool/ROOT                                        10.8G   876G       96K  none
rpool/ROOT/ubuntu_2cwpns                          10.8G   876G     4.79G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   876G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   876G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   876G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      6.05G   876G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   876G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  5.92G   876G     5.78G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   876G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    152K   876G      152K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              98.9M   876G     98.9M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             45.4M   876G     45.4M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   131M   876G      131M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   876G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.41M   876G     1.41M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 112K   876G      112K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   876G       96K  /var/www
rpool/USERDATA                                    4.58G   876G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  4.58G   876G     4.58G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        1.81M   876G     1.81M  /root

```
I clipped the last 100 lines and sorted it in reverse order, so back in time... I went back 2 boots... Because my wife blew the fuse on that circuit with her hair dryer.)
```

mafoelffen@Mikes-B460M:~$ journalctl -b-2 | tail -n 100 | grep 'systemd' | sort --reverse 
Apr 06 01:38:26 Mikes-B460M systemd[1]: whoopsie.path: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: virtlogd.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: virtlogd-admin.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: virtlockd.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: virtlockd-admin.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: uuidd.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unset automount Arbitrary Executable File Formats File System Automount Point.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/www...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/spool...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/mail...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/lib/NetworkManager...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/lib/dpkg...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/lib/apt...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/lib/AccountsService...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/games...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /usr/local...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /srv...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /run/snapd/ns/snapd-desktop-integration.mnt...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /run/credentials/systemd-sysusers.service...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /root...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Prepare /run/qemu to allow still running qemu binaries of former builds (after package upgrades) to fallback-load modules from there...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snap-store, revision 638...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snap-store, revision 599...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snapd, revision 18596...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snapd, revision 18357...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snapd-desktop-integration, revision 57...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snapd-desktop-integration, revision 49...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gtk-common-themes, revision 1535...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gtk-common-themes, revision 1534...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gnome-42-2204, revision 68...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gnome-42-2204, revision 65...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gnome-3-38-2004, revision 137...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gnome-3-38-2004, revision 119...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for firefox, revision 2487...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for firefox, revision 2391...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for firefox, revision 2088 via mount-control...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for core22, revision 583...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for core22, revision 547...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for core20, revision 1852...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for core20, revision 1828...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for bare, revision 5...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /home/mafoelffen...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /data...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /boot/grub...
Apr 06 01:38:26 Mikes-B460M systemd[1]: systemd-update-utmp.service: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: systemd-tmpfiles-setup.service: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: systemd-timesyncd.service: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: systemd-sysctl.service: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: systemd-networkd.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: systemd-modules-load.service: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: systemd-ask-password-wall.path: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: syslog.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopping Record System Boot/Shutdown in UTMP...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopping Network Time Synchronization...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopping Flush Journal to Persistent Storage...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped target System Initialization.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped target Socket Units.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped target Slice Units.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped target Mounted snaps.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped target Local Verity Protected Volumes.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped target Local File Systems.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped target Local Encrypted Volumes.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped Start whoopsie on modification of the /var/crash directory.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped Record System Boot/Shutdown in UTMP.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped Network Time Synchronization.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped Load Kernel Modules.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped Load AppArmor profiles managed internally by snapd.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped Forward Password Requests to Wall Directory Watch.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped CUPS Scheduler.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped Create Volatile Files and Directories.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped Apply Kernel Variables.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Stopped ACPI Events Check.
Apr 06 01:38:26 Mikes-B460M systemd[1]: snapd.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: snapd.apparmor.service: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Removed slice Virtual Machine and Container Slice.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Removed slice User and Session Slice.
Apr 06 01:38:26 Mikes-B460M systemd[1]: proc-sys-fs-binfmt_misc.mount: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: proc-sys-fs-binfmt_misc.automount: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: libvirtd.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: libvirtd-ro.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: libvirtd-admin.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: cups.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: cups.path: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Virtual machine log manager socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Virtual machine log manager socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Virtual machine lock manager socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Virtual machine lock manager admin socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed UUID daemon activation socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Syslog Socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Socket activation for snappy daemon.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Network Service Netlink Socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Libvirt local socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Libvirt local read-only socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Libvirt admin socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed CUPS Scheduler.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed Avahi mDNS/DNS-SD Stack Activation Socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: Closed ACPID Listen Socket.
Apr 06 01:38:26 Mikes-B460M systemd[1]: avahi-daemon.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: acpid.socket: Deactivated successfully.
Apr 06 01:38:26 Mikes-B460M systemd[1]: acpid.path: Deactivated successfully.

```
You can tweak that to see what you want...

---

### Post by papriak on 2023-04-11
Using "journalctl -rb -1" I was able to get the following information about the most recent shutdown:

```

root@server:~# journalctl -rb -1
Apr 10 18:19:21 server systemd-journald[327]: Journal stopped
Apr 10 18:19:21 server systemd-shutdown[1]: Sending SIGTERM to remaining processes...
Apr 10 18:19:21 server systemd-shutdown[1]: Syncing filesystems and block devices.
Apr 10 18:19:21 server systemd[1]: Shutting down.
Apr 10 18:19:21 server systemd[1]: Reached target System Reboot.
Apr 10 18:19:21 server systemd[1]: Finished System Reboot.
Apr 10 18:19:21 server systemd[1]: systemd-reboot.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Reached target Late Shutdown Services.
Apr 10 18:19:21 server systemd[1]: Reached target System Shutdown.
Apr 10 18:19:21 server systemd[1]: Stopped Remount Root and Kernel File Systems.
Apr 10 18:19:21 server systemd[1]: systemd-remount-fs.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Reached target Unmount All Filesystems.
Apr 10 18:19:21 server systemd[1]: Deactivated swap /swapfile.
Apr 10 18:19:21 server systemd[1]: swapfile.swap: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Stopped Create System Users.
Apr 10 18:19:21 server systemd[1]: systemd-sysusers.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Stopped Create Static Device Nodes in /dev.
Apr 10 18:19:21 server systemd[1]: systemd-tmpfiles-setup-dev.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Deactivating swap /swapfile...
Apr 10 18:19:21 server systemd[1]: Stopped target Swaps.
Apr 10 18:19:21 server systemd[1]: Stopped target Preparation for Local File Systems.
Apr 10 18:19:21 server systemd[1]: Unmounted /run/snapd/ns.
Apr 10 18:19:21 server systemd[1]: run-snapd-ns.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Removed slice Slice /system/systemd-fsck.
Apr 10 18:19:21 server systemd[1]: Stopped File System Check on /dev/disk/by-uuid/8BAE-A2B5.
Apr 10 18:19:21 server systemd[1]: systemd-fsck@dev-disk-by\x2duuid-8BAE\x2dA2B5.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounting /run/snapd/ns...
Apr 10 18:19:21 server systemd[1]: Stopped target Mounting snaps.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for firefox, revision 2356 via mount-control.
Apr 10 18:19:21 server systemd[1]: var-snap-firefox-common-host\x2dhunspell.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snapd-desktop-integration, revision 57.
Apr 10 18:19:21 server systemd[1]: snap-snapd\x2ddesktop\x2dintegration-57.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snapd-desktop-integration, revision 49.
Apr 10 18:19:21 server systemd[1]: snap-snapd\x2ddesktop\x2dintegration-49.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snapd, revision 18596.
Apr 10 18:19:21 server systemd[1]: snap-snapd-18596.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snapd, revision 18357.
Apr 10 18:19:21 server systemd[1]: snap-snapd-18357.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snap-store, revision 638.
Apr 10 18:19:21 server systemd[1]: snap-snap\x2dstore-638.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for gtk-common-themes, revision 1535.
Apr 10 18:19:21 server systemd[1]: snap-gtk\x2dcommon\x2dthemes-1535.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for gnome-42-2204, revision 68.
Apr 10 18:19:21 server systemd[1]: snap-gnome\x2d42\x2d2204-68.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for gnome-3-38-2004, revision 137.
Apr 10 18:19:21 server systemd[1]: snap-gnome\x2d3\x2d38\x2d2004-137.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for gnome-3-38-2004, revision 119.
Apr 10 18:19:21 server systemd[1]: snap-gnome\x2d3\x2d38\x2d2004-119.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for firefox, revision 2487.
Apr 10 18:19:21 server systemd[1]: snap-firefox-2487.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for firefox, revision 2356.
Apr 10 18:19:21 server systemd[1]: snap-firefox-2356.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for core22, revision 607.
Apr 10 18:19:21 server systemd[1]: snap-core22-607.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for core20, revision 1852.
Apr 10 18:19:21 server systemd[1]: snap-core20-1852.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for core20, revision 1822.
Apr 10 18:19:21 server systemd[1]: snap-core20-1822.mount: Deactivated successfully.

```


I don't see anything about my ZFS pool in there.

---

### Post by #&amp;thj^% on 2023-04-11
> **papriak said:**
> Using "journalctl -rb -1" I was able to get the following information about the most recent shutdown:

```

root@server:~# journalctl -rb -1
Apr 10 18:19:21 server systemd-journald[327]: Journal stopped
Apr 10 18:19:21 server systemd-shutdown[1]: Sending SIGTERM to remaining processes...
Apr 10 18:19:21 server systemd-shutdown[1]: Syncing filesystems and block devices.
Apr 10 18:19:21 server systemd[1]: Shutting down.
Apr 10 18:19:21 server systemd[1]: Reached target System Reboot.
Apr 10 18:19:21 server systemd[1]: Finished System Reboot.
Apr 10 18:19:21 server systemd[1]: systemd-reboot.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Reached target Late Shutdown Services.
Apr 10 18:19:21 server systemd[1]: Reached target System Shutdown.
Apr 10 18:19:21 server systemd[1]: Stopped Remount Root and Kernel File Systems.
Apr 10 18:19:21 server systemd[1]: systemd-remount-fs.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Reached target Unmount All Filesystems.
Apr 10 18:19:21 server systemd[1]: Deactivated swap /swapfile.
Apr 10 18:19:21 server systemd[1]: swapfile.swap: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Stopped Create System Users.
Apr 10 18:19:21 server systemd[1]: systemd-sysusers.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Stopped Create Static Device Nodes in /dev.
Apr 10 18:19:21 server systemd[1]: systemd-tmpfiles-setup-dev.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Deactivating swap /swapfile...
Apr 10 18:19:21 server systemd[1]: Stopped target Swaps.
Apr 10 18:19:21 server systemd[1]: Stopped target Preparation for Local File Systems.
Apr 10 18:19:21 server systemd[1]: Unmounted /run/snapd/ns.
Apr 10 18:19:21 server systemd[1]: run-snapd-ns.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Removed slice Slice /system/systemd-fsck.
Apr 10 18:19:21 server systemd[1]: Stopped File System Check on /dev/disk/by-uuid/8BAE-A2B5.
Apr 10 18:19:21 server systemd[1]: systemd-fsck@dev-disk-by\x2duuid-8BAE\x2dA2B5.service: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounting /run/snapd/ns...
Apr 10 18:19:21 server systemd[1]: Stopped target Mounting snaps.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for firefox, revision 2356 via mount-control.
Apr 10 18:19:21 server systemd[1]: var-snap-firefox-common-host\x2dhunspell.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snapd-desktop-integration, revision 57.
Apr 10 18:19:21 server systemd[1]: snap-snapd\x2ddesktop\x2dintegration-57.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snapd-desktop-integration, revision 49.
Apr 10 18:19:21 server systemd[1]: snap-snapd\x2ddesktop\x2dintegration-49.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snapd, revision 18596.
Apr 10 18:19:21 server systemd[1]: snap-snapd-18596.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snapd, revision 18357.
Apr 10 18:19:21 server systemd[1]: snap-snapd-18357.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for snap-store, revision 638.
Apr 10 18:19:21 server systemd[1]: snap-snap\x2dstore-638.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for gtk-common-themes, revision 1535.
Apr 10 18:19:21 server systemd[1]: snap-gtk\x2dcommon\x2dthemes-1535.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for gnome-42-2204, revision 68.
Apr 10 18:19:21 server systemd[1]: snap-gnome\x2d42\x2d2204-68.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for gnome-3-38-2004, revision 137.
Apr 10 18:19:21 server systemd[1]: snap-gnome\x2d3\x2d38\x2d2004-137.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for gnome-3-38-2004, revision 119.
Apr 10 18:19:21 server systemd[1]: snap-gnome\x2d3\x2d38\x2d2004-119.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for firefox, revision 2487.
Apr 10 18:19:21 server systemd[1]: snap-firefox-2487.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for firefox, revision 2356.
Apr 10 18:19:21 server systemd[1]: snap-firefox-2356.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for core22, revision 607.
Apr 10 18:19:21 server systemd[1]: snap-core22-607.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for core20, revision 1852.
Apr 10 18:19:21 server systemd[1]: snap-core20-1852.mount: Deactivated successfully.
Apr 10 18:19:21 server systemd[1]: Unmounted Mount unit for core20, revision 1822.
Apr 10 18:19:21 server systemd[1]: snap-core20-1822.mount: Deactivated successfully.

```


I don't see anything about my ZFS pool in there.

Humm?? the plot thickens..
a very short snip from mine:
```
journalctl -rb -1
Apr 11 12:07:18 me-Lenovo-Legion-5-15ARH05 systemd[1]: Unmounted root-.zfs-snap>
Apr 11 12:07:18 me-Lenovo-Legion-5-15ARH05 systemd[1]: root-.zfs-snapshot-autoz>
Apr 11 12:07:18 me-Lenovo-Legion-5-15ARH05 systemd[1]: Unmounted root-.zfs-snap>
Apr 11 12:07:18 me-Lenovo-Legion-5-15ARH05 systemd[1]: root-.zfs-snapshot-autoz>
Apr 11 12:07:18 me-Lenovo-Legion-5-15ARH05 systemd[1]: Unmounted root-.zfs-snap>
Apr 11 12:07:18 me-Lenovo-Legion-5-15ARH05 systemd[1]: root-.zfs-snapshot-autoz>
Apr 11 12:07:18 me-Lenovo-Legion-5-15ARH05 systemd[1]: Unmounted boot-grub.moun>

```
That is a problem though....need to think a bit on this before I add anything more.
I would like to know if you see anything zfs wise on boot-up?
please show this:
```
journalctl --since "2 days ago"

```
again a short snip of mine:
```
Apr 09 13:18:22 me-Lenovo-Legion-5-15ARH05 systemd[6757]: Starting zsys-user-sa>
Apr 09 13:18:22 me-Lenovo-Legion-5-15ARH05 systemd[1]: Starting zsysd.service ->
Apr 09 13:18:22 me-Lenovo-Legion-5-15ARH05 systemd[1]: Started zsysd.service - >
Apr 09 13:18:22 me-Lenovo-Legion-5-15ARH05 zsysctl[1089933]: Successfully saved>
Apr 09 13:18:22 me-Lenovo-Legion-5-15ARH05 systemd[6757]: Finished zsys-user-sa>
Apr 09 13:19:22 me-Lenovo-Legion-5-15ARH05 systemd[1]: zsysd.service: Deactivat
```

---

### Post by MAFoElffen on 2023-04-11
That shutdown was a reboot?

Let's see it if you shutdown the system normally instead of a reboot, then after booting again, do
```

journalctl -b-2 | tail -n 200 | grep 'systemd' | sort --reverse

```
Then for after a spin down and it coming back up, how are you spinning down the drives? With 'hdparm' triggered by suspend_on_idle.timer service? Just trying to figure out a query that would catch that condition and what follows that.

---

### Post by papriak on 2023-04-11
The output was too long to share, but Notepad and Wordpad both failed to find the terms "zfs" or "pool" in the text.

---

### Post by papriak on 2023-04-11
> **MAFoElffen said:**
> That shutdown was a reboot?

Let's see it if you shutdown the system normally instead of a reboot, then after booting again, do
```

journalctl -b-2 | tail -n 200 | grep 'systemd' | sort --reverse

```
Then for after a spin down and it coming back up, how are you spinning down the drives? With 'hdparm' triggered by suspend_on_idle.timer service? Just trying to figure out a query that would catch that condition and what follows that.

When I get home I'll attach an external drive and back up the pool's contents, then see what happens during a shutdown.

Thank you both for your continued assistance.

---

### Post by #&amp;thj^% on 2023-04-11
> **MAFoElffen said:**
> 
Then for after a spin down and it coming back up, how are you spinning down the drives? With 'hdparm' triggered by suspend_on_idle.timer service? Just trying to figure out a query that would catch that condition and what follows that.
MAFoElffen  can you take this one, my only full day off, and I got Honey-Do's out the ying yang.

---

### Post by MAFoElffen on 2023-04-11
Okay, let's change the filter to this:
```

journalctl -rb-1 | grep 'zfs\|pool'

```
Here is my output:
```

mafoelffen@Mikes-B460M:~$ journalctl -rb-2 | grep 'zfs\|pool'
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/spool...
Apr 06 01:38:24 Mikes-B460M systemd[1]: zfs-zed.service: Deactivated successfully.
Apr 06 01:38:24 Mikes-B460M systemd[1]: zfs-share.service: Deactivated successfully.
Apr 06 01:34:33 Mikes-B460M zed[3187]: eid=15 class=config_sync pool='datapool'
Apr 06 01:34:33 Mikes-B460M zed[3182]: eid=13 class=pool_import pool='datapool'
Apr 06 01:34:33 Mikes-B460M zed[3180]: eid=12 class=config_sync pool='datapool'
Apr 06 01:34:33 Mikes-B460M zed[2786]: eid=7 class=config_sync pool='bpool'
Apr 06 01:34:33 Mikes-B460M zed[2787]: eid=2 class=config_sync pool='rpool'
Apr 06 01:34:33 Mikes-B460M zed[2785]: eid=8 class=pool_import pool='bpool'
Apr 06 01:34:33 Mikes-B460M zed[2788]: eid=5 class=config_sync pool='rpool'
Apr 06 01:34:33 Mikes-B460M zed[2784]: eid=3 class=pool_import pool='rpool'
Apr 06 01:34:33 Mikes-B460M zed[2783]: eid=10 class=config_sync pool='bpool'
Apr 06 01:34:32 Mikes-B460M systemd[1]: Reached target ZFS pool import target.
Apr 06 01:34:32 Mikes-B460M systemd[1]: Finished Import ZFS pools by cache file.
Apr 06 01:34:30 Mikes-B460M systemd[1]: Starting Import ZFS pools by cache file...
Apr 06 01:34:29 Mikes-B460M udevadm[1319]: systemd-udev-settle.service is deprecated. Please fix zfs-load-module.service, zfs-import-cache.service not to pull it in.
Apr 06 01:34:29 Mikes-B460M systemd[1]: Mounted /var/spool.
Apr 06 01:34:29 Mikes-B460M systemd[1]: Mounting /var/spool...
Apr 06 01:34:29 Mikes-B460M kernel: ZFS: Loaded module v2.1.5-1ubuntu6~22.04.1, ZFS pool version 5000, ZFS filesystem version 5
Apr 06 01:34:29 Mikes-B460M kernel: zswap: loaded using pool lzo/zbud
Apr 06 01:34:29 Mikes-B460M kernel: DMA: preallocated 4096 KiB GFP_KERNEL|GFP_DMA32 pool for atomic allocations
Apr 06 01:34:29 Mikes-B460M kernel: DMA: preallocated 4096 KiB GFP_KERNEL|GFP_DMA pool for atomic allocations
Apr 06 01:34:29 Mikes-B460M kernel: DMA: preallocated 4096 KiB GFP_KERNEL pool for atomic allocations
Apr 06 01:34:29 Mikes-B460M kernel: Kernel command line: BOOT_IMAGE=/BOOT/ubuntu_2cwpns@/vmlinuz-5.19.0-38-generic root=ZFS=rpool/ROOT/ubuntu_2cwpns ro -- splash kvm-intel.nested=1 intel_idle.max_cstate=4 video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid intel_iommu=on systemd.unified_cgroup_hierarchy=0
Apr 06 01:34:29 Mikes-B460M kernel: efi: seeding entropy pool
Apr 06 01:34:29 Mikes-B460M kernel: Command line: BOOT_IMAGE=/BOOT/ubuntu_2cwpns@/vmlinuz-5.19.0-38-generic root=ZFS=rpool/ROOT/ubuntu_2cwpns ro -- splash kvm-intel.nested=1 intel_idle.max_cstate=4 video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid intel_iommu=on systemd.unified_cgroup_hierarchy=0

```

---

### Post by MAFoElffen on 2023-04-11
Oh dang... Case...
```

mafoelffen@Mikes-B460M:~$ journalctl -rb-2 | grep -i 'zfs\|pool'
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/spool...
Apr 06 01:38:24 Mikes-B460M systemd[1]: Stopped ZFS Event Daemon (zed).
Apr 06 01:38:24 Mikes-B460M systemd[1]: zfs-zed.service: Deactivated successfully.
Apr 06 01:38:24 Mikes-B460M systemd[1]: Stopping ZFS Event Daemon (zed)...
Apr 06 01:38:24 Mikes-B460M systemd[1]: Stopped ZFS file system shares.
Apr 06 01:38:24 Mikes-B460M systemd[1]: zfs-share.service: Deactivated successfully.
Apr 06 01:38:24 Mikes-B460M systemd[1]: Stopped target ZFS volumes are ready.
Apr 06 01:38:24 Mikes-B460M systemd[1]: Stopped target ZFS startup target.
Apr 06 01:34:47 Mikes-B460M systemd[1]: Reached target ZFS startup target.
Apr 06 01:34:47 Mikes-B460M systemd[1]: Finished ZFS file system shares.
Apr 06 01:34:47 Mikes-B460M systemd[1]: Starting ZFS file system shares...
Apr 06 01:34:33 Mikes-B460M zed[3187]: eid=15 class=config_sync pool='datapool'
Apr 06 01:34:33 Mikes-B460M zed[3182]: eid=13 class=pool_import pool='datapool'
Apr 06 01:34:33 Mikes-B460M zed[3180]: eid=12 class=config_sync pool='datapool'
Apr 06 01:34:33 Mikes-B460M zed[2786]: eid=7 class=config_sync pool='bpool'
Apr 06 01:34:33 Mikes-B460M zed[2787]: eid=2 class=config_sync pool='rpool'
Apr 06 01:34:33 Mikes-B460M zed[2785]: eid=8 class=pool_import pool='bpool'
Apr 06 01:34:33 Mikes-B460M zed[2788]: eid=5 class=config_sync pool='rpool'
Apr 06 01:34:33 Mikes-B460M zed[2784]: eid=3 class=pool_import pool='rpool'
Apr 06 01:34:33 Mikes-B460M zed[2783]: eid=10 class=config_sync pool='bpool'
Apr 06 01:34:33 Mikes-B460M zed[2706]: ZFS Event Daemon 2.1.5-1ubuntu6~22.04.1 (PID 2706)
Apr 06 01:34:33 Mikes-B460M systemd[1]: Started ZFS Event Daemon (zed).
Apr 06 01:34:32 Mikes-B460M systemd[1]: Finished Mount ZFS filesystems.
Apr 06 01:34:32 Mikes-B460M systemd[1]: Reached target ZFS volumes are ready.
Apr 06 01:34:32 Mikes-B460M systemd[1]: Finished Wait for ZFS Volume (zvol) links in /dev.
Apr 06 01:34:32 Mikes-B460M systemd[1]: Starting Mount ZFS filesystems...
Apr 06 01:34:32 Mikes-B460M systemd[1]: Starting Wait for ZFS Volume (zvol) links in /dev...
Apr 06 01:34:32 Mikes-B460M systemd[1]: Reached target ZFS pool import target.
Apr 06 01:34:32 Mikes-B460M systemd[1]: Finished Import ZFS pools by cache file.
Apr 06 01:34:30 Mikes-B460M systemd[1]: Starting Import ZFS pools by cache file...
Apr 06 01:34:30 Mikes-B460M systemd[1]: Finished Install ZFS kernel module.
Apr 06 01:34:30 Mikes-B460M systemd[1]: Starting Install ZFS kernel module...
Apr 06 01:34:29 Mikes-B460M udevadm[1319]: systemd-udev-settle.service is deprecated. Please fix zfs-load-module.service, zfs-import-cache.service not to pull it in.
Apr 06 01:34:29 Mikes-B460M systemd[1]: Mounted /var/spool.
Apr 06 01:34:29 Mikes-B460M systemd[1]: Mounting /var/spool...
Apr 06 01:34:29 Mikes-B460M kernel: ZFS: Loaded module v2.1.5-1ubuntu6~22.04.1, ZFS pool version 5000, ZFS filesystem version 5
Apr 06 01:34:29 Mikes-B460M kernel: zswap: loaded using pool lzo/zbud
Apr 06 01:34:29 Mikes-B460M kernel: DMA: preallocated 4096 KiB GFP_KERNEL|GFP_DMA32 pool for atomic allocations
Apr 06 01:34:29 Mikes-B460M kernel: DMA: preallocated 4096 KiB GFP_KERNEL|GFP_DMA pool for atomic allocations
Apr 06 01:34:29 Mikes-B460M kernel: DMA: preallocated 4096 KiB GFP_KERNEL pool for atomic allocations
Apr 06 01:34:29 Mikes-B460M kernel: Kernel command line: BOOT_IMAGE=/BOOT/ubuntu_2cwpns@/vmlinuz-5.19.0-38-generic root=ZFS=rpool/ROOT/ubuntu_2cwpns ro -- splash kvm-intel.nested=1 intel_idle.max_cstate=4 video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid intel_iommu=on systemd.unified_cgroup_hierarchy=0
Apr 06 01:34:29 Mikes-B460M kernel: efi: seeding entropy pool
Apr 06 01:34:29 Mikes-B460M kernel: Command line: BOOT_IMAGE=/BOOT/ubuntu_2cwpns@/vmlinuz-5.19.0-38-generic root=ZFS=rpool/ROOT/ubuntu_2cwpns ro -- splash kvm-intel.nested=1 intel_idle.max_cstate=4 video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid intel_iommu=on systemd.unified_cgroup_hierarchy=0
mafoelffen@Mikes-B460M:~$ 

```
But if I change the filter to this instead:
```

mafoelffen@Mikes-B460M:~$ journalctl -rb-2 | grep -i 'unmount\|export'
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/www...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/spool...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for firefox, revision 2088 via mount-control...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/mail...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/lib/dpkg...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/lib/apt...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/lib/NetworkManager...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/lib/AccountsService...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /var/games...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /usr/local...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /srv...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snapd-desktop-integration, revision 57...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snapd-desktop-integration, revision 49...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snapd, revision 18596...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snapd, revision 18357...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snap-store, revision 638...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for snap-store, revision 599...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gtk-common-themes, revision 1535...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gtk-common-themes, revision 1534...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gnome-42-2204, revision 68...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gnome-42-2204, revision 65...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gnome-3-38-2004, revision 137...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for gnome-3-38-2004, revision 119...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for firefox, revision 2487...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for firefox, revision 2391...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for core22, revision 583...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for core22, revision 547...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for core20, revision 1852...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for core20, revision 1828...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Mount unit for bare, revision 5...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /run/snapd/ns/snapd-desktop-integration.mnt...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting Prepare /run/qemu to allow still running qemu binaries of former builds (after package upgrades) to fallback-load modules from there...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /run/credentials/systemd-sysusers.service...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /root...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /home/mafoelffen...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /data...
Apr 06 01:38:26 Mikes-B460M systemd[1]: Unmounting /boot/grub...
Apr 06 01:38:24 Mikes-B460M systemd[1]: Unmounted RPC Pipe File System.
Apr 06 01:38:24 Mikes-B460M systemd[1]: Unmounting RPC Pipe File System...
Apr 06 01:38:24 Mikes-B460M kernel: nfsd: last server has exited, flushing export cache
Apr 06 01:38:24 Mikes-B460M systemd[1]: Unmounted /run/user/1000.
Apr 06 01:38:24 Mikes-B460M systemd[1]: Unmounted /run/user/1000/gvfs.
Apr 06 01:38:24 Mikes-B460M systemd[1]: Unmounted /run/user/1000/doc.
Apr 06 01:34:29 Mikes-B460M systemd-fsck[1673]: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.

```
I think those two filters should show what we are looking for in the shutdown.

EDIT: So I think combining the two like this:
```

journalctl -rb-2 | grep -i 'zfs\|pool\|unmount\|export'

```
There are other things that happen after the unmounts, that happens in meoery and doesn't get logged, but since they happen after the disks are unmounted, they wouldn't relate to ZFS...

---

### Post by MAFoElffen on 2023-04-11
> **1fallen said:**
> MAFoElffen  can you take this one, my only full day off, and I got Honey-Do's out the ying yang.
By coincidence, today is the first of my two days off. I have honey-do list also, but she is taking a nap. LOL

---

### Post by MAFoElffen on 2023-04-11
> **papriak said:**
> *When I get home I'll attach an external drive and back up the pool's contents, then see what happens during a shutdown.*
So this "drive" is not always attached? Please paint me a picture of how it is used and how it lives in your world... Normally.

[s]If it does not stay attached all the time, then before you detach the drive, then I would take the effort to export the pool on it before it is "disconnected." If often, then a quick, simple script to automate that. That way you ensure that the filesystem is finished shutting down. Just my thoughts on that. 

Thinking out loud:
Because if you spin down a drive via suspend _idle.timer, it doesn't shut down the filesystem in that process, so the filesystem is still open. So disconnecting that drive while it was spun down from an idle condition... Would be a problem.[/s]

But then I reread that, and you are just doing a back up. LOL Understood now.

---

### Post by #&amp;thj^% on 2023-04-11
> **MAFoElffen said:**
> By coincidence, today is the first of my two days off. I have honey-do list also, but she is taking a nap. LOL

I'll just keep checking between my water breaks, She's cracking the whip today:lolflag:

---

### Post by papriak on 2023-04-11
> **MAFoElffen said:**
> Then for after a spin down and it coming back up, how are you spinning down the drives? With 'hdparm' triggered by suspend_on_idle.timer service? Just trying to figure out a query that would catch that condition and what follows that.

I haven't done anything to spin down the drives yet.  They still spin the whole time the system is on.

---

### Post by MAFoElffen on 2023-04-11
Okay... Understood. No rush. Waiting patiently. 

Someone had a family emergency, and I am being called into work to cover for them... But will check before and after I pull this shift.

---

### Post by papriak on 2023-04-11
> EDIT: So I think combining the two like this:
```

journalctl -rb-2 | grep -i 'zfs\|pool\|unmount\|export'

```
There are other things that happen after the unmounts, that happens in meoery and doesn't get logged, but since they happen after the disks are unmounted, they wouldn't relate to ZFS...

Looks like that found some entries on my machine.  I'll do a "proper" shutdown and boot after the backups complete, then run it again.

```
root@server:~# journalctl -rb-2 | grep -i 'zfs\|pool\|unmount\|export'
Apr 10 15:22:28 server systemd[1]: Reached target Unmount All Filesystems.
Apr 10 15:22:28 server systemd[1]: Unmounted /run/snapd/ns.
Apr 10 15:22:28 server systemd[1]: Unmounting /run/snapd/ns...
Apr 10 15:22:28 server systemd[1]: Unmounted /run/snapd/ns/snapd-desktop-integration.mnt.
Apr 10 15:22:28 server systemd[1]: Unmounted /boot/efi.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for firefox, revision 2356 via mount-control.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for snapd-desktop-integration, revision 57.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for snapd-desktop-integration, revision 49.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for snapd, revision 18596.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for snapd, revision 18357.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for snap-store, revision 638.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for gtk-common-themes, revision 1535.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for gnome-42-2204, revision 68.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for gnome-3-38-2004, revision 137.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for gnome-3-38-2004, revision 119.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for firefox, revision 2487.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for firefox, revision 2356.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for core22, revision 607.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for core20, revision 1852.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for core20, revision 1822.
Apr 10 15:22:28 server systemd[1]: Unmounted Mount unit for bare, revision 5.
Apr 10 15:22:28 server systemd[1]: Unmounted /run/credentials/systemd-sysusers.service.
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for firefox, revision 2356 via mount-control...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for snapd-desktop-integration, revision 57...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for snapd-desktop-integration, revision 49...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for snapd, revision 18596...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for snapd, revision 18357...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for snap-store, revision 638...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for gtk-common-themes, revision 1535...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for gnome-42-2204, revision 68...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for gnome-3-38-2004, revision 137...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for gnome-3-38-2004, revision 119...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for firefox, revision 2487...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for firefox, revision 2356...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for core22, revision 607...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for core20, revision 1852...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for core20, revision 1822...
Apr 10 15:22:28 server systemd[1]: Unmounting Mount unit for bare, revision 5...
Apr 10 15:22:28 server systemd[1]: Unmounting /run/snapd/ns/snapd-desktop-integration.mnt...
Apr 10 15:22:28 server systemd[1]: Unmounting /run/credentials/systemd-sysusers.service...
Apr 10 15:22:28 server systemd[1]: Unmounting /boot/efi...
Apr 10 15:22:26 server systemd[1]: Unmounted /Transfer.
Apr 10 15:22:26 server kernel: EXT4-fs (nvme1n1p1): unmounting filesystem.
Apr 10 15:22:26 server systemd[1]: Unmounting /Transfer...
Apr 10 15:22:26 server systemd[1]: Unmounted /run/user/1001.
Apr 10 15:22:26 server systemd[1]: Unmounted /run/user/1001/doc.
Apr 10 15:22:26 server systemd[1]: Unmounted /run/user/1001/gvfs.
Apr 10 15:22:26 server systemd[1]: zfs-zed.service: Consumed 1.007s CPU time.
Apr 10 15:22:26 server systemd[1]: Stopped ZFS Event Daemon (zed).
Apr 10 15:22:26 server systemd[1]: zfs-zed.service: Deactivated successfully.
Apr 10 15:22:26 server systemd[1]: Stopping ZFS Event Daemon (zed)...
Apr 10 15:22:26 server systemd[1]: Stopped ZFS file system shares.
Apr 10 15:22:26 server systemd[1]: zfs-share.service: Deactivated successfully.
Apr 10 15:22:26 server systemd[1]: Stopped target ZFS volumes are ready.
Apr 10 15:22:26 server systemd[1]: Stopped target ZFS pool import target.
Apr 10 15:22:26 server systemd[1]: Stopped target ZFS startup target.
Apr 10 15:20:12 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=393216 size=131072 flags=a0ac0
Apr 10 15:20:12 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776208384 size=114688 flags=a0ac0
Apr 10 15:20:12 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776585216 size=131072 flags=a0ac0
Apr 10 15:20:12 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776470528 size=114688 flags=a0ac0
Apr 10 15:20:12 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=278528 size=114688 flags=a0ac0
Apr 10 15:20:10 server zed[13536]: eid=71 class=io pool='Pool' vdev=sde1 size=8192 offset=270336 priority=1 err=5 flags=0x80ac0 delay=26ms
Apr 10 15:20:10 server zed[13535]: eid=72 class=io pool='Pool' vdev=sde1 size=131072 offset=393216 priority=1 err=5 flags=0x80ac0 delay=25ms
Apr 10 15:20:10 server zed[13532]: eid=70 class=io pool='Pool' vdev=sde1 size=114688 offset=278528 priority=1 err=5 flags=0x80ac0 delay=26ms
Apr 10 15:20:10 server zed[13531]: eid=69 class=io pool='Pool' vdev=sde1 size=131072 offset=131072 priority=1 err=5 flags=0x80ac0 delay=26ms
Apr 10 15:20:10 server zed[13529]: eid=68 class=io pool='Pool' vdev=sde1 size=114688 offset=16384 priority=1 err=5 flags=0x80ac0 delay=27ms
Apr 10 15:20:10 server zed[13525]: eid=67 class=io pool='Pool' vdev=sde1 size=8192 offset=8192 priority=1 err=5 flags=0x80ac0 delay=27ms
Apr 10 15:20:10 server zed[13521]: eid=66 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776585216 priority=1 err=5 flags=0x80ac0 delay=46ms
Apr 10 15:20:10 server zed[13518]: eid=65 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776323072 priority=1 err=5 flags=0x80ac0 delay=51ms
Apr 10 15:20:10 server zed[13515]: eid=64 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776470528 priority=1 err=5 flags=0x80ac0 delay=49ms
Apr 10 15:20:10 server zed[13512]: eid=63 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776208384 priority=1 err=5 flags=0x80ac0 delay=78ms
Apr 10 15:20:10 server zed[13508]: eid=62 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776200192 priority=1 err=5 flags=0x80ac0 delay=52ms
Apr 10 15:20:10 server zed[13506]: eid=61 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776462336 priority=1 err=5 flags=0x80ac0 delay=49ms
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776462336 size=8192 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776200192 size=8192 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776208384 size=114688 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776470528 size=114688 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776323072 size=131072 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776585216 size=131072 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=8192 size=8192 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=16384 size=114688 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=131072 size=131072 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=278528 size=114688 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=270336 size=8192 flags=80ac0
Apr 10 15:20:10 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=393216 size=131072 flags=80ac0
Apr 10 15:17:26 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776585216 size=131072 flags=a0ac0
Apr 10 15:17:26 server zed[11866]: eid=60 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776200192 priority=1 err=5 flags=0xa0ac0 delay=1334ms
Apr 10 15:17:26 server zed[11864]: eid=59 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776208384 priority=1 err=5 flags=0xa0ac0 delay=3809ms
Apr 10 15:17:25 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776323072 size=131072 flags=a0ac0
Apr 10 15:17:25 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776208384 size=114688 flags=a0ac0
Apr 10 15:17:25 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776200192 size=8192 flags=a0ac0
Apr 10 15:17:24 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=16384 size=114688 flags=a0ac0
Apr 10 15:17:24 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=131072 size=131072 flags=a0ac0
Apr 10 15:17:21 server zed[11857]: eid=58 class=io pool='Pool' vdev=sde1 size=131072 offset=393216 priority=1 err=5 flags=0x80ac0 delay=25ms
Apr 10 15:17:21 server zed[11855]: eid=57 class=io pool='Pool' vdev=sde1 size=8192 offset=270336 priority=1 err=5 flags=0x80ac0 delay=26ms
Apr 10 15:17:21 server zed[11854]: eid=56 class=io pool='Pool' vdev=sde1 size=114688 offset=278528 priority=1 err=5 flags=0x80ac0 delay=26ms
Apr 10 15:17:21 server zed[11851]: eid=55 class=io pool='Pool' vdev=sde1 size=131072 offset=131072 priority=1 err=5 flags=0x80ac0 delay=26ms
Apr 10 15:17:21 server zed[11850]: eid=54 class=io pool='Pool' vdev=sde1 size=114688 offset=16384 priority=1 err=5 flags=0x80ac0 delay=27ms
Apr 10 15:17:21 server zed[11845]: eid=53 class=io pool='Pool' vdev=sde1 size=8192 offset=8192 priority=1 err=5 flags=0x80ac0 delay=27ms
Apr 10 15:17:21 server zed[11842]: eid=52 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776323072 priority=1 err=5 flags=0x80ac0 delay=281ms
Apr 10 15:17:21 server zed[11839]: eid=51 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776462336 priority=1 err=5 flags=0x80ac0 delay=281ms
Apr 10 15:17:21 server zed[11835]: eid=50 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776585216 priority=1 err=5 flags=0x80ac0 delay=280ms
Apr 10 15:17:21 server zed[11833]: eid=49 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776470528 priority=1 err=5 flags=0x80ac0 delay=281ms
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776470528 size=114688 flags=80ac0
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776585216 size=131072 flags=80ac0
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776462336 size=8192 flags=80ac0
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776323072 size=131072 flags=80ac0
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=8192 size=8192 flags=80ac0
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=16384 size=114688 flags=80ac0
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=131072 size=131072 flags=80ac0
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=278528 size=114688 flags=80ac0
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=270336 size=8192 flags=80ac0
Apr 10 15:17:21 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=393216 size=131072 flags=80ac0
Apr 10 15:14:25 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776585216 size=131072 flags=a0ac0
Apr 10 15:14:25 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776470528 size=114688 flags=a0ac0
Apr 10 15:14:25 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776462336 size=8192 flags=a0ac0
Apr 10 15:14:24 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776323072 size=131072 flags=a0ac0
Apr 10 15:14:24 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776208384 size=114688 flags=a0ac0
Apr 10 15:14:24 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776200192 size=8192 flags=a0ac0
Apr 10 15:14:22 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=278528 size=114688 flags=a0ac0
Apr 10 15:14:20 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=393216 size=131072 flags=a0ac0
Apr 10 15:14:18 server zed[6692]: eid=48 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776200192 priority=1 err=5 flags=0x80ac0 delay=30ms
Apr 10 15:14:18 server zed[6690]: eid=47 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776208384 priority=1 err=5 flags=0x80ac0 delay=30ms
Apr 10 15:14:18 server zed[6688]: eid=46 class=io pool='Pool' vdev=sde1 size=131072 offset=393216 priority=1 err=5 flags=0x80ac0 delay=30ms
Apr 10 15:14:18 server zed[6686]: eid=45 class=io pool='Pool' vdev=sde1 size=8192 offset=270336 priority=1 err=5 flags=0x80ac0 delay=30ms
Apr 10 15:14:18 server zed[6682]: eid=44 class=io pool='Pool' vdev=sde1 size=114688 offset=278528 priority=1 err=5 flags=0x80ac0 delay=31ms
Apr 10 15:14:18 server zed[6684]: eid=43 class=io pool='Pool' vdev=sde1 size=131072 offset=131072 priority=1 err=5 flags=0x80ac0 delay=31ms
Apr 10 15:14:18 server zed[6677]: eid=42 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776462336 priority=1 err=5 flags=0x80ac0 delay=54ms
Apr 10 15:14:18 server zed[6674]: eid=41 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776585216 priority=1 err=5 flags=0x80ac0 delay=53ms
Apr 10 15:14:18 server zed[6670]: eid=40 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776323072 priority=1 err=5 flags=0x80ac0 delay=84ms
Apr 10 15:14:18 server zed[6668]: eid=39 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776470528 priority=1 err=5 flags=0x80ac0 delay=54ms
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776470528 size=114688 flags=80ac0
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776323072 size=131072 flags=80ac0
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776585216 size=131072 flags=80ac0
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776462336 size=8192 flags=80ac0
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=131072 size=131072 flags=80ac0
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=278528 size=114688 flags=80ac0
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=270336 size=8192 flags=80ac0
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=393216 size=131072 flags=80ac0
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776208384 size=114688 flags=80ac0
Apr 10 15:14:18 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776200192 size=8192 flags=80ac0
Apr 10 15:13:16 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776208384 size=114688 flags=a0ac0
Apr 10 15:13:15 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776323072 size=131072 flags=a0ac0
Apr 10 15:13:12 server zed[6473]: eid=38 class=io pool='Pool' vdev=sde1 size=8192 offset=270336 priority=1 err=5 flags=0x80ac0 delay=25ms
Apr 10 15:13:12 server zed[6471]: eid=36 class=io pool='Pool' vdev=sde1 size=131072 offset=131072 priority=1 err=5 flags=0x80ac0 delay=26ms
Apr 10 15:13:12 server zed[6469]: eid=37 class=io pool='Pool' vdev=sde1 size=114688 offset=278528 priority=1 err=5 flags=0x80ac0 delay=25ms
Apr 10 15:13:12 server zed[6467]: eid=35 class=io pool='Pool' vdev=sde1 size=114688 offset=16384 priority=1 err=5 flags=0x80ac0 delay=27ms
Apr 10 15:13:12 server zed[6464]: eid=34 class=io pool='Pool' vdev=sde1 size=8192 offset=8192 priority=1 err=5 flags=0x80ac0 delay=27ms
Apr 10 15:13:12 server zed[6461]: eid=33 class=io pool='Pool' vdev=sde1 size=131072 offset=393216 priority=1 err=5 flags=0x80ac0 delay=95ms
Apr 10 15:13:12 server zed[6458]: eid=32 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776585216 priority=1 err=5 flags=0x80ac0 delay=237ms
Apr 10 15:13:12 server zed[6455]: eid=31 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776462336 priority=1 err=5 flags=0x80ac0 delay=238ms
Apr 10 15:13:12 server zed[6452]: eid=30 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776470528 priority=1 err=5 flags=0x80ac0 delay=238ms
Apr 10 15:13:12 server zed[6449]: eid=29 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776323072 priority=1 err=5 flags=0x80ac0 delay=238ms
Apr 10 15:13:12 server zed[6445]: eid=28 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776208384 priority=1 err=5 flags=0x80ac0 delay=334ms
Apr 10 15:13:12 server zed[6442]: eid=27 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776200192 priority=1 err=5 flags=0x80ac0 delay=239ms
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776200192 size=8192 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776208384 size=114688 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776323072 size=131072 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776470528 size=114688 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776462336 size=8192 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776585216 size=131072 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=393216 size=131072 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=8192 size=8192 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=16384 size=114688 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=131072 size=131072 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=278528 size=114688 flags=80ac0
Apr 10 15:13:11 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=270336 size=8192 flags=80ac0
Apr 10 15:13:02 server sudo[6284]:     root : TTY=pts/1 ; PWD=/root ; USER=root ; COMMAND=/usr/sbin/zpool create Pool raidz3 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh
Apr 10 15:12:07 server sudo[4831]:     root : TTY=pts/1 ; PWD=/root ; USER=root ; COMMAND=/usr/sbin/zpool create Pool raidz3 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh
Apr 10 15:11:41 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776585216 size=131072 flags=a0ac0
Apr 10 15:11:38 server zed[4790]: eid=26 class=io pool='Pool' vdev=sde1 size=8192 offset=270336 priority=1 err=5 flags=0x80ac0 delay=54ms
Apr 10 15:11:38 server zed[4788]: eid=25 class=io pool='Pool' vdev=sde1 size=114688 offset=278528 priority=1 err=5 flags=0x80ac0 delay=54ms
Apr 10 15:11:38 server zed[4786]: eid=24 class=io pool='Pool' vdev=sde1 size=131072 offset=131072 priority=1 err=5 flags=0x80ac0 delay=55ms
Apr 10 15:11:38 server zed[4785]: eid=23 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776200192 priority=1 err=5 flags=0x80ac0 delay=108ms
Apr 10 15:11:38 server zed[4780]: eid=22 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776208384 priority=1 err=5 flags=0x80ac0 delay=108ms
Apr 10 15:11:38 server zed[4777]: eid=21 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776323072 priority=1 err=5 flags=0x80ac0 delay=107ms
Apr 10 15:11:38 server zed[4775]: eid=20 class=io pool='Pool' vdev=sde1 size=8192 offset=4000776462336 priority=1 err=5 flags=0x80ac0 delay=107ms
Apr 10 15:11:38 server zed[4771]: eid=19 class=io pool='Pool' vdev=sde1 size=114688 offset=4000776470528 priority=1 err=5 flags=0x80ac0 delay=107ms
Apr 10 15:11:38 server zed[4768]: eid=18 class=io pool='Pool' vdev=sde1 size=131072 offset=4000776585216 priority=1 err=5 flags=0x80ac0 delay=106ms
Apr 10 15:11:38 server zed[4765]: eid=17 class=io pool='Pool' vdev=sde1 size=131072 offset=393216 priority=1 err=5 flags=0x80ac0 delay=863ms
Apr 10 15:11:38 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=393216 size=131072 flags=80ac0
Apr 10 15:11:37 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776585216 size=131072 flags=80ac0
Apr 10 15:11:37 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776470528 size=114688 flags=80ac0
Apr 10 15:11:37 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776462336 size=8192 flags=80ac0
Apr 10 15:11:37 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776323072 size=131072 flags=80ac0
Apr 10 15:11:37 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776208384 size=114688 flags=80ac0
Apr 10 15:11:37 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=4000776200192 size=8192 flags=80ac0
Apr 10 15:11:37 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=131072 size=131072 flags=80ac0
Apr 10 15:11:37 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=278528 size=114688 flags=80ac0
Apr 10 15:11:37 server kernel: zio pool=Pool vdev=/dev/sde1 error=5 type=2 offset=270336 size=8192 flags=80ac0
Apr 10 15:11:28 server sudo[4602]:     root : TTY=pts/1 ; PWD=/root ; USER=root ; COMMAND=/usr/sbin/zpool create -f Pool raidz3 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh
Apr 10 15:10:28 server jellyfin[2780]: [15:10:28] [INF] Skipping realtime monitor for /Pool/Movies because the path does not exist
Apr 10 15:10:16 server zed[2514]: eid=16 class=zpool pool='Pool'
Apr 10 15:10:16 server zed[2509]: eid=15 class=statechange pool='Pool' vdev=sdd1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2464]: eid=12 class=vdev.no_replicas pool='Pool'
Apr 10 15:10:16 server zed[2452]: eid=13 class=statechange pool='Pool' vdev=sde1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2431]: eid=11 class=statechange pool='Pool' vdev=sdc1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2445]: eid=14 class=statechange pool='Pool' vdev=sdb1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2425]: eid=10 class=statechange pool='Pool' vdev=sdf1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2413]: eid=8 class=zpool pool='Pool'
Apr 10 15:10:16 server zed[2417]: eid=9 class=statechange pool='Pool' vdev=sda1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2405]: eid=7 class=statechange pool='Pool' vdev=sde1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2334]: eid=6 class=statechange pool='Pool' vdev=sdb1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2331]: eid=4 class=vdev.no_replicas pool='Pool'
Apr 10 15:10:16 server zed[2321]: eid=5 class=statechange pool='Pool' vdev=sdd1 vdev_state=UNAVAIL
Apr 10 15:10:16 server systemd[1]: Reached target ZFS startup target.
Apr 10 15:10:16 server zed[2278]: eid=3 class=statechange pool='Pool' vdev=sdc1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2265]: eid=1 class=statechange pool='Pool' vdev=sda1 vdev_state=UNAVAIL
Apr 10 15:10:16 server zed[2252]: eid=2 class=statechange pool='Pool' vdev=sdf1 vdev_state=UNAVAIL
Apr 10 15:10:16 server systemd[1]: Finished ZFS file system shares.
Apr 10 15:10:16 server zed[2218]: ZFS Event Daemon 2.1.5-1ubuntu6~22.04.1 (PID 2218)
Apr 10 15:10:16 server systemd[1]: Started ZFS Event Daemon (zed).
Apr 10 15:10:16 server systemd[1]: Starting ZFS file system shares...
Apr 10 15:10:16 server systemd[1]: Reached target ZFS volumes are ready.
Apr 10 15:10:16 server systemd[1]: Finished Wait for ZFS Volume (zvol) links in /dev.
Apr 10 15:10:15 server systemd[1]: Finished Mount ZFS filesystems.
Apr 10 15:10:15 server systemd[1]: Starting Wait for ZFS Volume (zvol) links in /dev...
Apr 10 15:10:15 server systemd[1]: Starting Mount ZFS filesystems...
Apr 10 15:10:15 server systemd[1]: Reached target ZFS pool import target.
Apr 10 15:10:15 server systemd[1]: Failed to start Import ZFS pools by cache file.
Apr 10 15:10:15 server systemd[1]: zfs-import-cache.service: Failed with result 'exit-code'.
Apr 10 15:10:15 server systemd[1]: zfs-import-cache.service: Main process exited, code=exited, status=1/FAILURE
Apr 10 15:10:15 server zpool[1885]: cachefile import failed, retrying
Apr 10 15:10:15 server zpool[1885]: cannot import 'Pool': one or more devices is currently unavailable
Apr 10 15:10:15 server zpool[1885]: cannot import 'Pool': one or more devices is currently unavailable
Apr 10 15:10:15 server systemd[1]: Starting Import ZFS pools by cache file...
Apr 10 15:10:15 server systemd[1]: Finished Install ZFS kernel module.
Apr 10 15:10:15 server systemd[1]: Starting Install ZFS kernel module...
Apr 10 15:10:15 server kernel: ZFS: Loaded module v2.1.5-1ubuntu6, ZFS pool version 5000, ZFS filesystem version 5
Apr 10 15:10:14 server udevadm[363]: systemd-udev-settle.service is deprecated. Please fix zfs-load-module.service, zfs-import-cache.service not to pull it in.
Apr 10 15:10:14 server kernel: mpt2sas_cm0: reply pool(0x000000002819e716) - dma(0x115c80000): depth(3556), frame_size(128), pool_size(444 kB)
Apr 10 15:10:14 server kernel: mpt2sas_cm0: sense pool(0x00000000065dedd2)- dma(0x115c00000): depth(3367),element_size(96), pool_size(0 kB)
Apr 10 15:10:14 server kernel: mpt2sas_cm0: sense pool(0x00000000065dedd2) - dma(0x115c00000): depth(3367), element_size(96), pool_size (315 kB)
Apr 10 15:10:14 server kernel: mpt2sas_cm0: request pool(0x000000007f1a90fd) - dma(0x115580000): depth(3492), frame_size(128), pool_size(436 kB)
Apr 10 15:10:14 server kernel: zswap: loaded using pool lzo/zbud
Apr 10 15:10:14 server kernel: DMA: preallocated 4096 KiB GFP_KERNEL|GFP_DMA32 pool for atomic allocations
Apr 10 15:10:14 server kernel: DMA: preallocated 4096 KiB GFP_KERNEL|GFP_DMA pool for atomic allocations
Apr 10 15:10:14 server kernel: DMA: preallocated 4096 KiB GFP_KERNEL pool for atomic allocations
```

---

### Post by papriak on 2023-04-11
Alright, I've shutdown and restarted the machine to find the pool degraded with two disks faulted this time.

Here's the output of the command:

```
root@server:~# journalctl -rb-1 | grep -i 'zfs\|pool\|unmount\|export'
Apr 11 20:03:14 server systemd[1]: Reached target Unmount All Filesystems.
Apr 11 20:03:14 server systemd[1]: Unmounted /run/snapd/ns.
Apr 11 20:03:14 server systemd[1]: Unmounting /run/snapd/ns...
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for firefox, revision 2356 via mount-control.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for snapd-desktop-integration, revision 57.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for snapd-desktop-integration, revision 49.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for snapd, revision 18596.
Apr 11 20:03:14 server systemd[1]: Unmounted /Pool.
Apr 11 20:03:14 server systemd[1]: Pool.mount: Deactivated successfully.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for snapd, revision 18357.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for snap-store, revision 638.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for gtk-common-themes, revision 1535.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for gnome-42-2204, revision 68.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for gnome-3-38-2004, revision 137.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for gnome-3-38-2004, revision 119.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for firefox, revision 2559.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for firefox, revision 2487.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for core22, revision 607.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for core20, revision 1852.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for core20, revision 1822.
Apr 11 20:03:14 server systemd[1]: Unmounted Mount unit for bare, revision 5.
Apr 11 20:03:14 server systemd[1]: Unmounted /run/snapd/ns/snapd-desktop-integration.mnt.
Apr 11 20:03:14 server systemd[1]: Unmounted /run/snapd/ns/firefox.mnt.
Apr 11 20:03:14 server systemd[1]: Unmounted /run/credentials/systemd-sysusers.service.
Apr 11 20:03:14 server systemd[1]: Unmounted /boot/efi.
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for firefox, revision 2356 via mount-control...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for snapd-desktop-integration, revision 57...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for snapd-desktop-integration, revision 49...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for snapd, revision 18596...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for snapd, revision 18357...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for snap-store, revision 638...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for gtk-common-themes, revision 1535...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for gnome-42-2204, revision 68...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for gnome-3-38-2004, revision 137...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for gnome-3-38-2004, revision 119...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for firefox, revision 2559...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for firefox, revision 2487...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for core22, revision 607...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for core20, revision 1852...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for core20, revision 1822...
Apr 11 20:03:14 server systemd[1]: Unmounting Mount unit for bare, revision 5...
Apr 11 20:03:14 server systemd[1]: Unmounting /run/snapd/ns/snapd-desktop-integration.mnt...
Apr 11 20:03:14 server systemd[1]: Unmounting /run/snapd/ns/firefox.mnt...
Apr 11 20:03:14 server systemd[1]: Unmounting /run/credentials/systemd-sysusers.service...
Apr 11 20:03:14 server systemd[1]: Unmounting /boot/efi...
Apr 11 20:03:14 server systemd[1]: Unmounting /Pool...
Apr 11 20:03:14 server systemd[1]: Unmounted /Transfer.
Apr 11 20:03:14 server kernel: EXT4-fs (nvme1n1p1): unmounting filesystem.
Apr 11 20:03:09 server systemd[1]: Unmounting /Transfer...
Apr 11 20:03:09 server systemd[1]: Unmounted /run/user/1001.
Apr 11 20:03:08 server systemd[1]: Unmounted /run/user/1001/gvfs.
Apr 11 20:03:08 server systemd[1]: Unmounted /run/user/1001/doc.
Apr 11 20:03:08 server systemd[1]: zfs-zed.service: Consumed 1min 3.340s CPU time.
Apr 11 20:03:08 server systemd[1]: Stopped ZFS Event Daemon (zed).
Apr 11 20:03:08 server systemd[1]: zfs-zed.service: Deactivated successfully.
Apr 11 20:03:08 server systemd[1]: Stopping ZFS Event Daemon (zed)...
Apr 11 20:03:08 server systemd[1]: Stopped ZFS file system shares.
Apr 11 20:03:08 server systemd[1]: zfs-share.service: Deactivated successfully.
Apr 11 20:03:08 server systemd[1]: Stopped target ZFS volumes are ready.
Apr 11 20:03:08 server systemd[1]: Stopped target ZFS pool import target.
Apr 11 20:03:08 server systemd[1]: Stopped target ZFS startup target.

```


Should I just re-install the system at this point?  Maybe using the Server version, since I'm remoting into it anyway?

Edit:  Does it make a difference that I'm using a PERC H310 controller card, flashed to IT mode instead of the motherboard's headers?

---

### Post by #&amp;thj^% on 2023-04-12
> **papriak said:**
> 

Edit:  Does it make a difference that I'm using a PERC H310 controller card, flashed to IT mode instead of the motherboard's headers?

Now we are on to something, Talking with a Developer last night, He asked me about something along those lines.
I'll give you his advice to me:
> If you put it into IT mode then it will act as just a disk controller and pass all the disks to the computer natively. I believe you need to flash the IT firmware (as opposed to the IR firmware) onto the card to achieve this. This is the best way to use it for ZFS. 

I'd flash it so the disks can be attached differently in case the controller blows up Edit: also its probably advisable to prevent the controller from using raid cache mechanisms that interfere with zfs caching optimization 

---

### Post by MAFoElffen on 2023-04-12
> **papriak said:**
> Alright, I've shutdown and restarted the machine to find the pool degraded with two disks faulted this time.

Here's the output of the command:

```
root@server:~# journalctl -rb-1 | grep -i 'zfs\|pool\|unmount\|export'
Apr 11 20:03:14 server systemd[1]: Reached target Unmount All Filesystems.
Apr 11 20:03:14 server systemd[1]: Unmounted /Pool.
Apr 11 20:03:14 server systemd[1]: Pool.mount: Deactivated successfully.
Apr 11 20:03:14 server systemd[1]: Unmounting /Pool...
Apr 11 20:03:08 server systemd[1]: Stopped ZFS Event Daemon (zed).
Apr 11 20:03:08 server systemd[1]: zfs-zed.service: Deactivated successfully.
Apr 11 20:03:08 server systemd[1]: Stopping ZFS Event Daemon (zed)...
Apr 11 20:03:08 server systemd[1]: Stopped ZFS file system shares.
Apr 11 20:03:08 server systemd[1]: zfs-share.service: Deactivated successfully.

```

Should I just re-install the system at this point? Maybe using the Server version, since I'm remoting into it anyway?

Edit: Does it make a difference that I'm using a PERC H310 controller card, flashed to IT mode instead of the motherboard's headers?
No,. I don't think it's the PERC card that is causing a problem... ***Except for some considerations that I'll note at the end, which will make things a challenge...

It's unmounting during the shutdown. If you want to see how (the details), Run Level 0 (rc0) is halt and Run Level 6 (rc6) is reboot. The scripts for each run level are in directories /etc/rc[0-6,S].d. So the ones we are looking at are /etc/rc0.d/ and /etc/rc6.d/. Those are symlinks to the real script /etc/init.d/zfs-mount. As seen here:
```

mafoelffen@Mikes-B460M:~$ file /etc/rc[0,6].d/???zfs-mount
/etc/rc0.d/K01zfs-mount: symbolic link to ../init.d/zfs-mount
/etc/rc6.d/K01zfs-mount: symbolic link to ../init.d/zfs-mount

mafoelffen@Mikes-B460M:~$ grep . /etc/init.d/zfs-mount
#!/bin/sh
#
# zfs-mount     This script will mount/umount the zfs filesystems.
#
# chkconfig:    2345 06 99
# description:  This script will mount/umount the zfs filesystems during
#               system boot/shutdown. Configuration of which filesystems
#               should be mounted is handled by the zfs 'mountpoint' and
#               'canmount' properties. See the zfs(8) man page for details.
#               It is also responsible for all userspace zfs services.
# probe: true
#
### BEGIN INIT INFO
# Provides:          zfs-mount
# Required-Start:    $local_fs zfs-import
# Required-Stop:     $local_fs zfs-import
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# X-Stop-After:      zfs-zed
# Short-Description: Mount ZFS filesystems and volumes
# Description: Run the `zfs mount -a` or `zfs umount -a` commands.
### END INIT INFO
#
# Released under the 2-clause BSD license.
#
# This script is based on debian/zfsutils.zfs.init from the
# Debian GNU/kFreeBSD zfsutils 8.1-3 package, written by Aurelien Jarno.
# Source the common init script
. /etc/zfs/zfs-functions
# ----------------------------------------------------
chkroot() {
    while read -r _ mp _; do
        if [ "$mp" = "/" ]; then
            return 0
        fi
    done < /proc/self/mounts
    return 1
}
do_depend()
{
    # Try to allow people to mix and match fstab with ZFS in a way that makes sense.
    if [ "$(mountinfo -s /)" = 'zfs' ]
    then
        before localmount
    else
        after localmount
    fi
    # bootmisc will log to /var which may be a different zfs than root.
    before bootmisc logger
    after zfs-import sysfs
    use mtab
    keyword -lxc -openvz -prefix -vserver
}
# Mount all datasets/filesystems
do_mount()
{
    local verbose overlay i mntpt
    check_boolean "$VERBOSE_MOUNT" && verbose=v
    check_boolean "$DO_OVERLAY_MOUNTS" && overlay=O
    zfs_action "Mounting ZFS filesystem(s)" \
        "$ZFS" mount -a$verbose$overlay "$MOUNT_EXTRA_OPTIONS"
    # Require each volume/filesystem to have 'noauto' and no fsck
    # option. This shouldn't really be necessary, as long as one
    # can get zfs-import to run sufficiently early on in the boot
    # process - before local mounts. This is just here in case/if
    # this isn't possible.
    check_boolean "$VERBOSE_MOUNT" && \
        zfs_log_begin_msg "Mounting volumes and filesystems registered in fstab"
    read_mtab  "^/dev/(zd|zvol)"
    read_fstab "^/dev/(zd|zvol)"
    i=0; var="FSTAB_0"
    while [ -n "$(eval echo "\$$var")" ]
    do
        mntpt=$(eval echo "\$$var")
        dev=$(eval echo "\$FSTAB_dev_$i")
        if ! in_mtab "$mntpt" && ! is_mounted "$mntpt" && [ -e "$dev" ]
        then
            check_boolean "$VERBOSE_MOUNT" && \
                zfs_log_progress_msg "$mntpt "
            fsck "$dev" && mount "$mntpt"
        fi
        i=$((i + 1))
        var=$(eval echo "FSTAB_$i")
    done
    read_mtab  "[[:space:]]zfs[[:space:]]"
    read_fstab "[[:space:]]zfs[[:space:]]"
    i=0; var=$(eval echo "FSTAB_$i")
    while [ -n "$(eval echo "\$$var")" ]
    do
        mntpt=$(eval echo "\$$var")
        if ! in_mtab "$mntpt" && ! is_mounted "$mntpt"
        then
            check_boolean "$VERBOSE_MOUNT" && \
                zfs_log_progress_msg "$mntpt "
            mount "$mntpt"
        fi
        i=$((i + 1))
        var=$(eval echo "FSTAB_$i")
    done
    check_boolean "$VERBOSE_MOUNT" && zfs_log_end_msg 0
    return 0
}
# Unmount all filesystems
do_unmount()
{
    local i var mntpt
    # This shouldn't really be necessary, as long as one can get
    # zfs-import to run sufficiently late in the shutdown/reboot process
    # - after unmounting local filesystems. This is just here in case/if
    # this isn't possible.
    zfs_action "Unmounting ZFS filesystems" "$ZFS" unmount -a
    check_boolean "$VERBOSE_MOUNT" && \
        zfs_log_begin_msg "Unmounting volumes and filesystems registered in fstab"
    read_mtab  "^/dev/(zd|zvol)"
    read_fstab "^/dev/(zd|zvol)"
    i=0; var="FSTAB_0"
    while [ -n "$(eval echo "\$$var")" ]
    do
        mntpt=$(eval echo "\$$var")
        dev=$(eval echo "\$FSTAB_dev_$i")
        if in_mtab "$mntpt"
        then
            check_boolean "$VERBOSE_MOUNT" && \
                zfs_log_progress_msg "$mntpt "
            umount "$mntpt"
        fi
        i=$((i + 1))
        var=$(eval echo "FSTAB_$i")
    done
    read_mtab  "[[:space:]]zfs[[:space:]]"
    read_fstab "[[:space:]]zfs[[:space:]]"
    i=0; var="FSTAB_0"
    while [ -n "$(eval echo "\$$var")" ]
    do
        mntpt=$(eval echo "\$$var")
        if in_mtab "$mntpt"; then
            check_boolean "$VERBOSE_MOUNT" && \
                zfs_log_progress_msg "$mntpt "
            umount "$mntpt"
        fi
        i=$((i + 1))
        var=$(eval echo "FSTAB_$i")
    done
    check_boolean "$VERBOSE_MOUNT" && zfs_log_end_msg 0
    return 0
}
do_start()
{
    check_boolean "$ZFS_MOUNT" || exit 0
    check_module_loaded "zfs" || exit 0
    # Ensure / exists in /proc/self/mounts.
    # This should be handled by rc.sysinit but lets be paranoid.
    if ! chkroot
    then
        mount -f /
    fi
    do_mount
}
do_stop()
{
    check_boolean "$ZFS_UNMOUNT" || exit 0
    check_module_loaded "zfs" || exit 0
    do_unmount
}
# ----------------------------------------------------
if [ ! -e /sbin/openrc-run ]
then
    case "$1" in
        start)
            do_start
            ;;
        stop)
            do_stop
            ;;
        force-reload|condrestart|reload|restart|status)
            # no-op
            ;;
        *)
            [ -n "$1" ] && echo "Error: Unknown command $1."
            echo "Usage: $0 {start|stop}"
            exit 3
            ;;
    esac
    exit $?
else
    # Create wrapper functions since Gentoo don't use the case part.
    depend() { do_depend; }
    start() { do_start; }
    stop() { do_stop; }
fi

```
It is running successfully and the status is in red in your logs above.

So the question still, is why is your RAID members getting errors and degrading.

A few admin kinds of things
```

sudo zfs status -v <pool_name> | grep -i 'scrub'

```
Would show any errors that were found in the pool during the last scrub.

RE:/etc/cron.d/zfs-utils
```

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# TRIM the first Sunday of every month.
24 0 1-7 * * root if [ $(date +\%w) -eq 0 ] && [ -x /usr/lib/zfs-linux/trim ]; then /usr/lib/zfs-linux/trim; fi

# Scrub the second Sunday of every month.
24 0 8-14 * * root if [ $(date +\%w) -eq 0 ] && [ -x /usr/lib/zfs-linux/scrub ]; then /usr/lib/zfs-linux/scrub; fi

```
By default, Ubuntu's default schedule for ZFS Trim is the first Sunday of the month, and ZFS Scrub on the second Sunday of the month, but... You turn off your system at night, so no telling when the last time or if your pools have ever had a Scrub done to check integrity. You may have to run them to chack the health of your pools.

Next is your question about your PERC 310. After looking at the filesystem of the pools, nxt would be to use smartmon tools to check smart error and to run tests on the drives. No sense fo doing a backup or reinstalling on drives that may be the problem, right? Here is where your PERC card can cause a challenge. Are you using HW RAID from the card? Or are you passing through the drives? I am not sure about the details of reflashing it as IT Mode... when it comes to how they usually work and jbod. I know usually PERC does not do jbod, so to pass through drives, you had to set them up as single-drive RAID-0 logical drives. How do you have the config of this PERC card?

---

### Post by MAFoElffen on 2023-04-12
Continued...

The problem usually with the PERC, is that smartmon tools can't see the firmware of the drives behind the PERC card. That is where the real challenge is going to be. This is what 'you' are going to have to test on your own to see if that is true, and how to get around that... I don't knw (not familiar with) IT mode, so don't know if that add 'jbod' to that so that they could be seen.

It won;t let me edit my last post, so a few variations of commands that might show other aspects:
```

sudo zpool status -v
sudo zpool iostat -v
sudo zpool list -H -o capacity

```
Yes, work got crazy last night, so I didn't get a chance to finish my post until this morning.

---

### Post by #&amp;thj^% on 2023-04-12
I concur  with MAFoElffen, in post # 30
Nor do I think a re-install is necessary.
Mike, this one is a first:
```
sudo zfs status -v <pool_name> | grep -i 'scrub'
```
Is this correct?
Never Mind: (I just use different syntax)
```
zpool status -v rpool | grep scrub
  scan: scrub in progress since Wed Apr 12 12:22:14 2023
###And
zpool status -v rpool | grep -i scrub
  scan: scrub repaired 0B in 00:00:46 with 0 errors on Wed Apr 12 12:23:00 2023

```

---

### Post by MAFoElffen on 2023-04-12
> **1fallen said:**
> I concur  with MAFoElffen, in post # 30
Nor do I think a re-install is necessary.
Mike, this one is a first:
```
sudo zfs status -v <pool_name> | grep -i 'scrub'
```
Is this correct?
Never Mind:(I just use different syntax)
```
zpool status -v rpool | grep scrub
  scan: scrub in progress since Wed Apr 12 12:22:14 2023
###And
zpool status -v rpool | grep -i scrub
  scan: scrub repaired 0B in 00:00:46 with 0 errors on Wed Apr 12 12:23:00 2023

```

No. The filter is "too" closed. I wanted to go back and change that, but the Forum wouldn't let me edit that post to change that...
instead try
```

sudo zpool status -v | grep -i 'scrub\|error'

```
Yes. Last night got slammed at work and didn't get home until after 1am... The cat woke me up to get his breakfast. LOL Not going to answer my phone today. I need at least one day off.

---

### Post by #&amp;thj^% on 2023-04-12
> **MAFoElffen said:**
> No. The filter is "too" closed. I wanted to go back and change that, but the Forum wouldn't let me edit that post to change that...
instead try
```

sudo zpool status -v | grep -i 'scrub\|error'

Bingo, now we are cooking in style: :)
[CODE]sudo zpool status -v | grep -i 'scrub\|error' 
errors: No known data errors
  scan: scrub repaired 0B in 00:00:46 with 0 errors on Wed Apr 12 12:23:00 2023
errors: No known data errors

```

---

### Post by MAFoElffen on 2023-04-12
I suspect with his, since he does not leave his on at night, cron.d kicks that off at midnight, so if it does not have a hit on scrub, then it hasn't been done, or checking the timestamp if it has, it may have been a while ago.

---

### Post by papriak on 2023-04-12
> **1fallen said:**
> Now we are on to something, Talking with a Developer last night, He asked me about something along those lines.
I'll give you his advice to me:

I flashed the card to IT mode because it has 8 ports and my motherboard only has 6.  Plus I've read that software RAID is easier to recover than hardware RAID, which would require an identical controller it happened to "blow up".

The drives appear to the system as /dev/sda through /dev/sdh, and I don't believe the card is caching anything.

---

### Post by papriak on 2023-04-12
> **MAFoElffen said:**
> 

try
```

sudo zpool status -v | grep -i 'scrub\|error'

```

That sounds like a good plan, but I wasn't able to boot my main PC today for remotely accessing my server from work.  (The POST codes suggest either the CMOS battery died or the graphics card needs to be re-seated.  Probably the former but no harm in trying both solutions tonight.)

---

### Post by #&amp;thj^% on 2023-04-12
Edit: just caught your last post:
> **papriak said:**
> That sounds like a good plan, but I wasn't able to boot my main PC today for remotely accessing my server from work.  (The POST codes suggest either the CMOS battery died or the graphics card needs to be re-seated.  Probably the former but no harm in trying both solutions tonight.)
Ignore the below then.
Can you now show us this: ?
```
sudo zpool status -v
sudo zpool iostat -v
sudo zpool list -H -o capacity
```
And this:
```
sudo zpool status -v | grep -i 'scrub\|error' 

```
i feel like willy wonka looking for the golden ticket...lol

---

### Post by papriak on 2023-04-12
> **1fallen said:**
> Can you now show us this: ?
```
sudo zpool status -v
sudo zpool iostat -v
sudo zpool list -H -o capacity
```
And this:
```
sudo zpool status -v | grep -i 'scrub\|error' 

```
i feel like willy wonka looking for the golden ticket...lol

Gladly, once I get home and have both machines running.

Also, I've been manually scrubbing the pool after transferring data in or out, but "zpool status" only reports errors after I boot the system.

In the meantime:  How quickly should the server be shutting down?  Last night I noticed the server turned off within a second or two of sending the command, might that be disabling the ZFS pool too quickly?

---

### Post by #&amp;thj^% on 2023-04-12
> **papriak said:**
> Gladly, once I get home and have both machines running.

Also, I've been manually scrubbing the pool after transferring data in or out, but "zpool status" only reports errors after I boot the system.

In the meantime:  How quickly should the server be shutting down?  Last night I noticed the server turned off within a second or two of sending the command, might that be disabling the ZFS pool too quickly?

Yep I edited my post, you was faster than me. :)
>  Last night I noticed the server turned off within a second or two of sending the command, might that be disabling the ZFS pool too quickly?
I truly believe this to be something with that card, even if it is SW flashed and not HW.
And the fact that you boot-up fine, I need to get my hands on one of those cards though.

---

### Post by papriak on 2023-04-12
> **1fallen said:**
> Yep I edited my post, you was faster than me. :)

I truly believe this to be something with that card, even if it is SW flashed and not HW.
And the fact that you boot-up fine, I need to get my hands on one of those cards though.

I have a second H310 card that I also flashed before I realized I had a faulty SAS 8087 to SATA breakout cable.  You can PM me if you'd like me to send it to you.

Both were flashed using the bootable tools in this guide:

[https://fohdeesha.com/docs/perc.html](https://fohdeesha.com/docs/perc.html)
[https://fohdeesha.com/docs/H310-full.html](https://fohdeesha.com/docs/H310-full.html)

---

### Post by #&amp;thj^% on 2023-04-12
Those links look right, but again i would need to have my eyes and hands on it.
I'll talk to my guy again tonite and see if there is anything we are missing here..BTW he Loves his H310.
he uses "DELL PERC H200 H310 LSI 9207-8I FW: P20 9211-8I IT Mode ZFS FreeNAS unRAID"

---

### Post by MAFoElffen on 2023-04-12
Mine in my storage are all PERC H710's. They were good cards when they were new and current. The reason I stopped using them is that they had a 2TB limit to each drive they would see... I didn't know that until I had put bigger drives in, but the cards would only recognize them as being 2TB drives. 

Dang. I hate when that happens. LOL My PE 740 had 16 2.5" drive bays. I loved that. But it sounded like an airplane with all those fans and the redundant PSU's.

Does re-flashing them get around that original/old size limit? And does it add jbod pass-through to the H710's?

---

### Post by papriak on 2023-04-12
> **MAFoElffen said:**
> Mine in my storage are all PERC H710's. They were good cards when they were new and current. The reason I stopped using them is that they had a 2TB limit to each drive they would see... I didn't know that until I had put bigger drives in, but the cards would only recognize them as being 2TB drives. 

Dang. I hate when that happens. LOL My PE 740 had 16 2.5" drive bays. I loved that. But it sounded like an airplane with all those fans and the redundant PSU's.

Does re-flashing them get around that original/old size limit? And does it add jbod pass-through to the H710's?

My cards are H310s, but they now appear to pass data through without any size limitations:

Webmin's partition manager said the drives had to be GPT since they're 4TB each, and the pool was listed at about 20TB capacity after formatting.


So the flashing supposedly bypasses the RAID functions and makes the H310 card a simple HBA without bells or whistles.

---

### Post by papriak on 2023-04-12
> **1fallen said:**
> Those links look right, but again i would need to have my eyes and hands on it.
I'll talk to my guy again tonite and see if there is anything we are missing here..BTW he Loves his H310.
he uses "DELL PERC H200 H310 LSI 9207-8I FW: P20 9211-8I IT Mode ZFS FreeNAS unRAID"

Thanks, I look forward to reading what he has to say.

---

### Post by papriak on 2023-04-12
Okay, this is just strange.

I've run the 'shutdown' command a few times, and the pool is coming back perfectly fine.

However, my main PC has developed an issue that makes it boot *extremely* slowly.  When my monitor comes to life it says something about the BIOS being in safe mode?


Its as if the gremlin "upgraded" to my gaming PC.

---

### Post by MAFoElffen on 2023-04-12
I have done Dev Ubuntu+1 testing for so many years, that installing bootchart is part of my goto's on installs. But with systemd-analyze...
```

systemd-analyze plot > plot_20230412.svg

```
Like the attached

---

### Post by papriak on 2023-04-13
Looks like installing the latest video card driver, a fresh CMOS battery, and performing a clean boot fixed my main PC's issues.

As for the server, I "destroyed" the old ZFS array and remade it in RAIDZ3 to be safe, I'm now transferring the data back to see if any errors are found.

Webmin found some updates as well, so I'll install those too and I'll update you after they're installed.

I can reboot the system from work,.  (Perhaps scrubbing will find an error when it comes back up with data) but I can't turn the system back on from a full shutdown form work.  I can try that later tonight.

---

### Post by papriak on 2023-04-13
All data imported and the scrub found no errors.

Crossing my fingers and rebooting now.

---

### Post by papriak on 2023-04-13
All drives are online and again a scrub found no errors.

I suppose those updates fixed something?

---

### Post by #&amp;thj^% on 2023-04-13
That's Great news, exactly what the Developer recommended.

---

### Post by MAFoElffen on 2023-04-13
@1fallen -- 

You mean that great minds think a like? LOL.

I think if you keep check when those two cron jobs are set for your ZFS, that would be good for them to complete regularly.

Once a month is actually less than recommended. For personal desktop type drives it's once a week. Enterprise drives are recommended for once a month.

---

### Post by #&amp;thj^% on 2023-04-13
> **MAFoElffen said:**
> @1fallen -- 

You mean that great minds think a like? LOL.

Indeed I do ;)
gee I wish I had a mind, let alone a great one...(come on now it was funny)

---

### Post by papriak on 2023-04-13
> **MAFoElffen said:**
> @1fallen -- 

You mean that great minds think a like? LOL.

I think if you keep check when those two cron jobs are set for your ZFS, that would be good for them to complete regularly.

Once a month is actually less than recommended. For personal desktop type drives it's once a week. Enterprise drives are recommended for once a month.

I assume the jobs you refer to are "zpool status"  and  "zpool scrub [Pool name]"?

Would daily be "too often" for them?

---

### Post by papriak on 2023-04-13
> **1fallen said:**
> Indeed I do ;)
gee I wish I had a mind, let alone a great one...(come on now it was funny)

*If he only had a brain...*

---

### Post by papriak on 2023-04-14
It seems that the "reboot" command is still corrupting my pool.

Where can I edit the parameters for this, and which ones would you recommend?

---

### Post by #&amp;thj^% on 2023-04-14
I'm speechless now, the  only constant is that DELL PERC H310 card, with a max of  20TB that your showing now....
The most I've attached to mine is three 4TB drives.
Where did you get the driver for that card, and what version is it?

RAIDz1, RAIDz2, and RAIDz3 are special varieties of what storage greybeards call "diagonal parity RAID." The 1, 2, and 3 refer to how many parity blocks are allocated to each data stripe. Rather than having entire disks dedicated to parity, RAIDz vdevs distribute that parity semi-evenly across the disks. A RAIDz array can lose as many disks as it has parity blocks; if it loses another, it fails, and takes the zpool down with it.

Another DEV "notnotluke " has chimed in with his 2 cents worth:
> 

You can't. The card is acting like an HBA, with no other option. Or you use the RAID option of the card, and using ZFS on top of hardware RAID is a recipe for data loss anyway.

What you want, if you really REALLY want protection form power failure is using a SLOG, built with two battery backed SSD (Intel is the way to go, you can even go for NVMe drives to avoid using the same HBA) in mirror. And you need to force all operations to use it with "sync=always" in ZFS options. This is the way to do it with ZFS.


Hardware RAID 5/6 arrays have what's called a write hole. It can cause the data to be corrupted if interrupted during a write. This is unique to hardware RAID 5/6 and the battery is only helpful in that situation. ZFS is copy on write so it's never overwriting existing data like hardware RAID 5/6 would do so there's no write hole and no need for battery backed caches.

If you're worried about writes not making it to the disk (like databases or other systems that need to know if a write worked) then use a SLOG device and synchronous writes. In that case ZFS will put the changes on a dedicated device before they written to the pool. If the write gets interrupted it'll go back to the SLOG to figure out what it was doing and finish it. Clients won't get a confirmation of the write until it's completely written to the SLOG.

Dang I was hoping for a better outcome.
How big is your PSU?

---

### Post by papriak on 2023-04-14
> **1fallen said:**
> I'm speechless now, the  only constant is that DELL PERC H310 card, with a max of  20TB that your showing now....
The most I've attached to mine is three 4TB drives.
Where did you get the driver for that card, and what version is it?

RAIDz1, RAIDz2, and RAIDz3 are special varieties of what storage greybeards call "diagonal parity RAID." The 1, 2, and 3 refer to how many parity blocks are allocated to each data stripe. Rather than having entire disks dedicated to parity, RAIDz vdevs distribute that parity semi-evenly across the disks. A RAIDz array can lose as many disks as it has parity blocks; if it loses another, it fails, and takes the zpool down with it.

Another DEV "notnotluke " has chimed in with his 2 cents worth:

Dang I was hoping for a better outcome.
How big is your PSU?

My PSU is 650w.


I followed the instructions and ran the tools provided on this page:  [https://fohdeesha.com/docs/perc.html](https://fohdeesha.com/docs/perc.html)

I'll see if a driver update is available when I get home, I think the DOS tool can read the current driver version.



The H310 cards don't have battery options, but I use external 1500va UPS units for each system.



Perhaps more information would help:

When  I reboot, I find a disk or two "faulted", which leaves the pool in a  "degraded" state, and I need to wipe and "replace" the disk(s) to get  the pool back to normal.


Perhaps the reboot/shutdown sequence is too quick, is it possible to make the system "wait" for each process to complete?  Or maybe add a delay after the pool is told to terminate?

---

### Post by #&amp;thj^% on 2023-04-14
> **papriak said:**
> My PSU is 650w.
I use an 850w on mine but yours should suffice.

> **papriak said:**
> 
I followed the instructions and ran the tools provided on this page:  [https://fohdeesha.com/docs/perc.html](https://fohdeesha.com/docs/perc.html)

I'll see if a driver update is available when I get home, I think the DOS tool can read the current driver version.

That would be a good idea, just to be sure

> **papriak said:**
> 
The H310 cards don't have battery options, but I use external 1500va UPS units for each system.
yep that was known going in.

> **papriak said:**
> 

Perhaps more information would help:

When  I reboot, I find a disk or two "faulted", which leaves the pool in a  "degraded" state, and I need to wipe and "replace" the disk(s) to get  the pool back to normal.


Perhaps the reboot/shutdown sequence is too quick, is it possible to make the system "wait" for each process to complete?  Or maybe add a delay after the pool is told to terminate?
Possible, but I'm doubtful, i have a dozen or more friends running zfs-root systems/servers, none of them report what you see, and 80% percent of them won't use that card....don't kill the messenger. This just screams hardware>>"a disk or two "faulted"
maybe have a peek at:
```
journalctl -b1 -r

```
to show the shutdown log messages (in reverse order) from the last shutdown. It all appears to be there with no tweaks from me.

---

### Post by MAFoElffen on 2023-04-14
I do have some more ideas, but I need a complete picture of what we are working with.

Please provide information 1fallen and I can visualize what you have going on there...
```

sudo add-apt-repository ppa:mafoelffen/system-info
sudo apt update
sudo apt install system-info
system-info --details

```
Ignore where is says you are missing any program's, I want to see what is comes up with that also. When it gets to the prompt where it asks to upload the report, says <Y><Enter> for yes. Copy down the URL and post it.

I do not think it is the H310, as you said it is passing the drives through, transparently as if they were jbod. That report will tell us that, as how it see's it in Linux Terms. Using it with the "--details" flag will put it into details mode and show more information on both the storage controllers and on ZFS.

---

### Post by #&amp;thj^% on 2023-04-14
+1 to the above, Dang i forget about that script far too much
With the OP's set up >>> wait for it to collect all the info.
Like Mine:
This may take 1-2 minutes...

        - Upload successful 

The link to the pastebin is saved in: '/home/me/system-info-link.log'

**_View at: [https://termbin.com/bimnt](https://termbin.com/bimnt)_**

---

### Post by papriak on 2023-04-14
The program originally said I was missing the Pastebin program, but I was able to add it.

Here you go:

[https://paste.ubuntu.com/p/mxMcFtTFRz/](https://paste.ubuntu.com/p/mxMcFtTFRz/)

---

### Post by #&amp;thj^% on 2023-04-14
> **papriak said:**
> The program originally said I was missing the Pastebin program, but I was able to add it.

Here you go:

[https://paste.ubuntu.com/p/mxMcFtTFRz/](https://paste.ubuntu.com/p/mxMcFtTFRz/)
I think I just found an issue>>>"SecureBoot enabled"
And I'm  still reading the link.
And >>> "Mem:           31980", have you thought about adding more RAM (Min recommend for me 8 Gigs)
One more:
```
HeaderLog: 00000000 00000000 00000000 00000000
	Capabilities: [138 v1] Power Budgeting <?>
	Kernel driver in use: mpt3sas
	Kernel modules: mpt3sas
```
EDIT: Just Notes to see here quickly:
Mine
```
----------  ZFS Information:
System has at least one ZFS type partition.

System has ZFS rpools activated.
```
Yours:
```
----------  ZFS Information:
System has at least one ZFS type partition.

System has no ZFS rpools activated.
###AND
gdm-wayland-ses

```

---

### Post by papriak on 2023-04-14
> **1fallen said:**
> I think I just found an issue>>>"SecureBoot enabled"

Easy enough to disable, I was running Windows on the build before.

> And >>> "Mem:           31980", have you thought about adding more RAM (Min recommend for me 8 Gigs)


The motherboard is maxed out at 32GB RAM.

> One more:
```
HeaderLog: 00000000 00000000 00000000 00000000
    Capabilities: [138 v1] Power Budgeting <?>
    Kernel driver in use: mpt3sas
    Kernel modules: mpt3sas
```
EDIT: Just Notes to see here quickly:
Mine
```
----------  ZFS Information:
System has at least one ZFS type partition.

System has ZFS rpools activated.
```
Yours:
```
----------  ZFS Information:
System has at least one ZFS type partition.

System has no ZFS rpools activated.
###AND
gdm-wayland-ses

```


So you're saying I should disable the power budgeting on the card?  That makes sense.

I can also see how that last section could be an issue. But what exactly *is* a rpool, and what does the last line mean?


Edit:  I did look up "rpool", but only got results for "root pools" and swimming pools.  I'm a bit fuzzy on the definition of "root pool" also.

---

### Post by #&amp;thj^% on 2023-04-14
> **papriak said:**
> Easy enough to disable, I was running Windows on the build before.
I wondered about that possibility, Good Thanks


> **papriak said:**
> 
The motherboard is maxed out at 32GB RAM.
That will work :)



> **papriak said:**
> 
So you're saying I should disable the power budgeting on the card?  That makes sense.
I'm just thinking that's a good thing to test.
> **papriak said:**
> 
I can also see how that last section could be an issue. But what exactly *is* a rpool, and what does the last line mean?

In a nut shell quick and simple: bpool=contains all the stuff needed to boot: 
rpool= where all user land resides. IE:
```
inxi -p | grep rpool
    logical: rpool/ROOT/ubuntu_w2q9ov
    logical: rpool/USERDATA/me_r6a7nm
    logical: rpool/USERDATA/root_r6a7nm
  ID-8: /run/keystore/rpool size: 437 MiB used: 28 KiB (0.0%) fs: ext4
    logical: rpool/ROOT/ubuntu_w2q9ov/srv
    logical: rpool/ROOT/ubuntu_w2q9ov/usr/local
    logical: rpool/ROOT/ubuntu_w2q9ov/var/games
    logical: rpool/ROOT/ubuntu_w2q9ov/var/lib
    fs: zfs logical: rpool/ROOT/ubuntu_w2q9ov/var/lib/AccountsService
    fs: zfs logical: rpool/ROOT/ubuntu_w2q9ov/var/lib/NetworkManager
    logical: rpool/ROOT/ubuntu_w2q9ov/var/lib/apt
    logical: rpool/ROOT/ubuntu_w2q9ov/var/lib/dpkg
    logical: rpool/ROOT/ubuntu_w2q9ov/var/log
    logical: rpool/ROOT/ubuntu_w2q9ov/var/mail
    logical: rpool/ROOT/ubuntu_w2q9ov/var/snap
    logical: rpool/ROOT/ubuntu_w2q9ov/var/spool
    logical: rpool/ROOT/ubuntu_w2q9ov/var/www

```
Or ```
ls /
bin   cdrom  etc   lib    lib64   media  opt   root  sbin  sys  usr
boot  dev    home  lib32  libx32  mnt    proc  run   srv   tmp  var

```
Hope that helps, if not just ask. :)
EDIT: I forgot this one:
> gdm-wayland-ses
Wayland is a newer display sever, and in my view it's not quite ready for primetime, it wouldn't hurt to try using a X11 session here.

---

### Post by papriak on 2023-04-14
> **1fallen said:**
> In a nut shell quick and simple: bpool=contains all the stuff needed to boot: rpool= where all user land resides. IE:
```
inxi -p | grep rpool
    logical: rpool/ROOT/ubuntu_w2q9ov
    logical: rpool/USERDATA/me_r6a7nm
    logical: rpool/USERDATA/root_r6a7nm
  ID-8: /run/keystore/rpool size: 437 MiB used: 28 KiB (0.0%) fs: ext4
    logical: rpool/ROOT/ubuntu_w2q9ov/srv
    logical: rpool/ROOT/ubuntu_w2q9ov/usr/local
    logical: rpool/ROOT/ubuntu_w2q9ov/var/games
    logical: rpool/ROOT/ubuntu_w2q9ov/var/lib
    fs: zfs logical: rpool/ROOT/ubuntu_w2q9ov/var/lib/AccountsService
    fs: zfs logical: rpool/ROOT/ubuntu_w2q9ov/var/lib/NetworkManager
    logical: rpool/ROOT/ubuntu_w2q9ov/var/lib/apt
    logical: rpool/ROOT/ubuntu_w2q9ov/var/lib/dpkg
    logical: rpool/ROOT/ubuntu_w2q9ov/var/log
    logical: rpool/ROOT/ubuntu_w2q9ov/var/mail
    logical: rpool/ROOT/ubuntu_w2q9ov/var/snap
    logical: rpool/ROOT/ubuntu_w2q9ov/var/spool
    logical: rpool/ROOT/ubuntu_w2q9ov/var/www

```
Or ```
ls /
bin   cdrom  etc   lib    lib64   media  opt   root  sbin  sys  usr
boot  dev    home  lib32  libx32  mnt    proc  run   srv   tmp  var

```
Hope that helps, if not just ask. :)
EDIT: I forgot this one:

Wayland is a newer display sever, and in my view it's not quite ready for primetime, it wouldn't hurt to try using a X11 session here.

My ZFS pool is separate from the rest of the system:  I boot from an SSD, and have another SSD for quickly transferring data.  (So it can then go from that SSD to the RAIDZ storage without tying up my main machine)

 I don't recall seeing an option to install directly onto the ZFS array when I was setting up the OS.

Also, I use Webmin to remotely access the server, or the default Gnome GUI when it's not running headless.  Is there a way to switch Webmin to X11, or perhaps another graphical remote access environment you would advise?

---

### Post by #&amp;thj^% on 2023-04-14
> **papriak said:**
> 
 I don't recall seeing an option to install directly onto the ZFS array when I was setting up the OS.

there is a way to avoid that, but I'll need to check with the Staff on this before posting in the public eye.
You dove into the Deep End with this set-up

---

### Post by papriak on 2023-04-14
> **1fallen said:**
> there is a way to avoid that, but I'll need to check with the Staff on this before posting in the public eye.
You dove into the Deep End with this set-up

I've been considering re-installing on the Server edition anyway, do you think having the pool be the root file system will help?

---

### Post by #&amp;thj^% on 2023-04-14
> **papriak said:**
> I've been considering re-installing on the Server edition anyway, do you think having the pool be the root file system will help?

I think it's easier with less formatted partitions, but that's just me, also naming the pools for human consumption makes it nicer to read.
Wait before you do that install though, I still haven't heard back from a staff member.

---

### Post by papriak on 2023-04-14
> **1fallen said:**
> I think it's easier with less formatted partitions, but that's just me, also naming the pools for human consumption makes it nicer to read.
Wait before you do that install though, I still haven't heard back from a staff member.

Alright, I'll disable Secure Boot and double-check the power-saving features of the hardware while I wait.

---

### Post by MAFoElffen on 2023-04-15
Thank you, thank you, thank you. This test at least found a bug in my code! LOL It broke my logic flow for that, and showed me I had to change the filter on it...

Lines 1120-1122
```

    zfs_fs_type=$(lsblk -o NAME,FSTYPE | \
        grep -m 1 'rpool') # Local Var

```
That assumes a user is using ZFS in a tradition ZFS-on-root install that followed OpenZFS.org's recommendations on installing... Including the default installs of ZFS in Ubuntu 20.04 and 22.04. The name 'rpool' only exists is the user followed their recommendations and used their own naming conventions to call a 'root pool' as being 'rpool'. In the real world, a user is free to call a pool whatever they want. Users can name tings that makes sense to them. The is no authority that say they have to name them a certain way. It still works.

ZFS is more open than that, and in real life, sh*t happens. I need to change the filter there to rather something like this
```

    zfs_fs_type=$(df -hT -x tmpfs -x devtmpfs | \
        grep -v '/snap/' | \
        grep -m 1 'zfs_member') # Local Var

```
Thank you for help finding that bug.

Please run these, that it skipped because of that
```

sudo zpool list
sudo zfs list

```

Should you have a root pool and have your raidz for data in their? My personal thoughts on that is a "No". I separate my data and other containers out in other pools. For example:
```

mafoelffen@Mikes-B460M:~$ sudo zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool     1.88G   293M  1.59G        -         -     0%    15%  1.00x    ONLINE  -
datapool  3.62T   719G  2.92T        -         -     9%    19%  1.00x    ONLINE  -
rpool      920G  15.5G   905G        -         -     1%     1%  1.00x    ONLINE  -
mafoelffen@Mikes-B460M:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              293M  1.46G       96K  /boot
bpool/BOOT                                         291M  1.46G       96K  none
bpool/BOOT/ubuntu_2cwpns                           291M  1.46G      291M  /boot
[COLOR=#ff0000]datapool                                           719G  2.81T       96K  none
datapool/DATA                                      719G  2.81T      719G  /data[/COLOR]
rpool                                             15.5G   876G       96K  /
rpool/ROOT                                        10.8G   876G       96K  none
rpool/ROOT/ubuntu_2cwpns                          10.8G   876G     4.80G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   876G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   876G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   876G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      6.05G   876G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   876G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  5.92G   876G     5.78G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   876G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    168K   876G      168K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              99.0M   876G     99.0M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             45.4M   876G     45.4M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   134M   876G      134M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   876G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.39M   876G     1.39M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 112K   876G      112K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   876G       96K  /var/www
rpool/USERDATA                                    4.60G   876G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  4.60G   876G     4.60G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        1.80M   876G     1.80M  /root
mafoelffen@Mikes-B460M:~$ sudo zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool     1.88G   293M  1.59G        -         -     0%    15%  1.00x    ONLINE  -
datapool  3.62T   719G  2.92T        -         -     9%    19%  1.00x    ONLINE  -
rpool      920G  15.5G   905G        -         -     1%     1%  1.00x    ONLINE  -
mafoelffen@Mikes-B460M:~$ sudo zpool status -v
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:00 with 0 errors on Sun Apr  9 00:24:01 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      0196ab45-3ee2-894e-b725-39560409109f  ONLINE       0     0     0

errors: No known data errors

  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 01:35:02 with 0 errors on Sun Apr  9 01:59:04 2023
config:

    NAME                                     STATE     READ WRITE CKSUM
    datapool                                 ONLINE       0     0     0
      ata-ST8000DM004-2U9188_ZR143PZD-part1  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:12 with 0 errors on Sun Apr  9 00:24:15 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      ae13efaa-d1cf-ec40-86a6-2883f0e07102  ONLINE       0     0     0

errors: No known data errors
mafoelffen@Mikes-B460M:~$ lsblk /dev/disk/by-id/ata-ST8000DM004-2U9188_ZR143PZD
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda      8:0    0  7.3T  0 disk 
&#9492;&#9472;sda1   8:1    0  3.6T  0 part 

```
You can see that, just like experience I learned from LVM2 and my past experience of using ZFS with Solaris and OpenSolaris, that disk is 8TB, but I have only allocated 3TB for my data pool there... (At least so far.) If I need more room or if I need to create another pool, I have unallocated space there to grow.

Now what I see in the details is this:
```

---------- Disk/Partition Information From 'fdisk': (editted for space>

Disk /dev/nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors

Device           Start       End   Sectors  Size Type
/dev/nvme0n1p1    2048   1050623   1048576  512M EFI System
/dev/nvme0n1p2 1050624 500117503 499066880  238G Linux filesystem

Disk /dev/nvme1n1: 1.86 TiB, 2048408248320 bytes, 4000797360 sectors

Device         Start        End    Sectors  Size Type
/dev/nvme1n1p1  2048 4000797326 4000795279  1.9T Linux filesystem

Disk /dev/sdf: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors

Device          Start        End    Sectors  Size Type
/dev/sdf1        2048 7814019071 7814017024  3.6T [COLOR=#ff0000]Solaris /usr & Apple ZFS[/COLOR]
/dev/sdf9  7814019072 7814035455      16384    8M Solaris reserved 1

Disk /dev/sdg: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors

Device          Start        End    Sectors  Size Type
/dev/sdg1        2048 7814019071 7814017024  3.6T [COLOR=#ff0000]Solaris /usr & Apple ZFS[/COLOR]
/dev/sdg9  7814019072 7814035455      16384    8M Solaris reserved 1

Disk /dev/sdb: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors

Device          Start        End    Sectors  Size Type
/dev/sdb1        2048 7814019071 7814017024  3.6T [COLOR=#ff0000]Solaris /usr & Apple ZFS[/COLOR]
/dev/sdb9  7814019072 7814035455      16384    8M Solaris reserved 1

Disk /dev/sdc: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors

Device          Start        End    Sectors  Size Type
/dev/sdc1        2048 7814019071 7814017024  3.6T [COLOR=#ff0000]Solaris /usr & Apple ZFS[/COLOR]
/dev/sdc9  7814019072 7814035455      16384    8M Solaris reserved 1

Disk /dev/sda: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors

Device          Start        End    Sectors  Size Type
/dev/sda1        2048 7814019071 7814017024  3.6T [COLOR=#ff0000]Solaris /usr & Apple ZFS[/COLOR]
/dev/sda9  7814019072 7814035455      16384    8M Solaris reserved 1

Disk /dev/sde: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors

Device          Start        End    Sectors  Size Type
/dev/sde1        2048 7814019071 7814017024  3.6T [COLOR=#ff0000]Solaris /usr & Apple ZFS[/COLOR]
/dev/sde9  7814019072 7814035455      16384    8M Solaris reserved 1

Disk /dev/sdh: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors

Device          Start        End    Sectors  Size Type
/dev/sdh1        2048 7814019071 7814017024  3.6T [COLOR=#ff0000]Solaris /usr & Apple ZFS[/COLOR]
/dev/sdh9  7814019072 7814035455      16384    8M Solaris reserved 1

Disk /dev/sdd: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors

Device          Start        End    Sectors  Size Type
/dev/sdd1        2048 7814019071 7814017024  3.6T [COLOR=#FF0000]Solaris /usr & Apple ZFS[/COLOR]
/dev/sdd9  7814019072 7814035455      16384    8M Solaris reserved 1

```
Let me spin up one of my ZFS test VM's with DRAIDZ

---

### Post by papriak on 2023-04-15
> **MAFoElffen said:**
> Thank you, thank you, thank you. This test at least found a bug in my code! LOL It broke my logic flow for that, and showed me I had to change the filter on it...

Lines 1120-1122
```

    zfs_fs_type=$(lsblk -o NAME,FSTYPE | \
        grep -m 1 'rpool') # Local Var

```
That assumes a user is using ZFS in a tradition ZFS-on-root install that followed OpenZFS.org's recommendations on installing... Including the default installs of ZFS in Ubuntu 20.04 and 22.04. The name 'rpool' only exists is the user followed their recommendations and used their own naming conventions to call a 'root pool' as being 'rpool'. In the real world, a user is free to call a pool whatever they want. Users can name tings that makes sense to them. The is no authority that say they have to name them a certain way. It still works.

ZFS is more open than that, and in real life, sh*t happens. I need to change the filter there to rather something like this
```

    zfs_fs_type=$(df -hT -x tmpfs -x devtmpfs | \
        grep -v '/snap/' | \
        grep -m 1 'zfs_member') # Local Var

```
Thank you for help finding that bug.

You're welcome.  Being that I'm still fairly new to Linux, I did things my own way.  :P


>  Please run these, that it skipped because of that
```

sudo zpool list
sudo zfs list

```

Screen snip attached.

> Should you have a root pool and have your raidz for data in their? My personal thoughts on that is a "No". I separate my data and other containers out in other pools. For example:
```

mafoelffen@Mikes-B460M:~$ sudo zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool     1.88G   293M  1.59G        -         -     0%    15%  1.00x    ONLINE  -
datapool  3.62T   719G  2.92T        -         -     9%    19%  1.00x    ONLINE  -
rpool      920G  15.5G   905G        -         -     1%     1%  1.00x    ONLINE  -
mafoelffen@Mikes-B460M:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              293M  1.46G       96K  /boot
bpool/BOOT                                         291M  1.46G       96K  none
bpool/BOOT/ubuntu_2cwpns                           291M  1.46G      291M  /boot
[COLOR=#ff0000]datapool                                           719G  2.81T       96K  none
datapool/DATA[/COLOR]                                      719G  2.81T      719G  /data
rpool                                             15.5G   876G       96K  /
rpool/ROOT                                        10.8G   876G       96K  none
rpool/ROOT/ubuntu_2cwpns                          10.8G   876G     4.80G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   876G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   876G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   876G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      6.05G   876G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   876G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  5.92G   876G     5.78G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   876G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    168K   876G      168K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              99.0M   876G     99.0M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             45.4M   876G     45.4M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   134M   876G      134M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   876G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.39M   876G     1.39M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 112K   876G      112K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   876G       96K  /var/www
rpool/USERDATA                                    4.60G   876G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  4.60G   876G     4.60G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        1.80M   876G     1.80M  /root
mafoelffen@Mikes-B460M:~$ sudo zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool     1.88G   293M  1.59G        -         -     0%    15%  1.00x    ONLINE  -
datapool  3.62T   719G  2.92T        -         -     9%    19%  1.00x    ONLINE  -
rpool      920G  15.5G   905G        -         -     1%     1%  1.00x    ONLINE  -
mafoelffen@Mikes-B460M:~$ sudo zpool status -v
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:00 with 0 errors on Sun Apr  9 00:24:01 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      0196ab45-3ee2-894e-b725-39560409109f  ONLINE       0     0     0

errors: No known data errors

  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 01:35:02 with 0 errors on Sun Apr  9 01:59:04 2023
config:

    NAME                                     STATE     READ WRITE CKSUM
    datapool                                 ONLINE       0     0     0
      ata-ST8000DM004-2U9188_ZR143PZD-part1  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:12 with 0 errors on Sun Apr  9 00:24:15 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      ae13efaa-d1cf-ec40-86a6-2883f0e07102  ONLINE       0     0     0

errors: No known data errors
mafoelffen@Mikes-B460M:~$ lsblk /dev/disk/by-id/ata-ST8000DM004-2U9188_ZR143PZD
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda      8:0    0  7.3T  0 disk 
&#9492;&#9472;sda1   8:1    0  3.6T  0 part 

```
You can see that, just like experience I learned from LVM2 and my past experience of using ZFS with Solaris and OpenSolaris, that disk is 8TB, but I have only allocated 4TB for my data pool there... (At least so far.) If I need more room or if I need to create another pool, I have unallocated space there to grow.

Always good to have room to grow.  Much better than running out of room.

---

### Post by #&amp;thj^% on 2023-04-15
Ok I got the go ahead, Thanks coffecat.
****Please know this going in or forward with these instructions**:**
1.More for Advanced or Power-users.(Far too much to define here)
2.This method :!:will use the entire disk:!:
3.I just can not word this any better than this:
> The only other consideration that I can think of is that threads are viewed by people, some inexperienced newbies, other than the thread OP, and if anything has the potential to bork one's system, then a cautionary note might be a good idea. That being said, the OP seems to have sufficient experience to recognise potential pitfalls, and what you are suggesting is for a new installation that can be redone if it goes wrong anyway.
Please forgive me if I overstepped my place for the quote, but it's perfect.
Now here we go, Boot to the live installer and once opened, now use a terminal and run:
```

sudo apt update

sudo apt install zfsutils-linux zfs-initramfs zfs-zed
```
Now proceed to the installer as normal.
wheniit come to the part for partioning layout or Installation type, use Erase disk, now click the tab Advanced Features and that will allow you to install on a zfs-root with Encryption*(optional)*(See Screenshot)
and if all goes well boot to your new zfs-root system. Good Luck, I'm off to work for a very short time.

---

### Post by papriak on 2023-04-15
> **1fallen said:**
> Ok I got the go ahead, Thanks coffecat.
****Please know this going in or forward with these instructions**:**
1.More for Advanced or Power-users.(Far too much to define here)
2.This method :!:will use the entire disk:!:
3.I just can not word this any better than this:

Please forgive me if I overstepped my place for the quote, but it's perfect.
Now here we go, Boot to the live installer and once opened, now use a terminal and run:
```

sudo apt update

sudo apt install zfsutils-linux zfs-initramfs zfs-zed
```
Now proceed to the installer as normal.
wheniit come to the part for partioning layout or Installation type, use Erase disk, now click the tab Advanced Features and that will allow you to install on a zfs-root with Encryption*(optional)*(See Screenshot)
and if all goes well boot to your new zfs-root system. Good Luck, I'm off to work for a very short time.

My thanks to both of you.  I'll try re-installing after I make a backup.

---

### Post by MAFoElffen on 2023-04-15
Relook at the edit to my last post on what I found as 'questionable'... I'm sorry. I was editting it an it boinked... LOL This is what I was trying to point out and compare with mine...<br><br>On your ZFS pool data disks, What partition type code are you using from this list?
```

mafoelffen@Mikes-B460M:~$ sudo sgdisk -L | grep 'Solaris'
be00 Solaris boot                        bf00 Solaris root                      
bf01 Solaris /usr & Mac ZFS              bf02 Solaris swap                      
bf03 Solaris backup                      bf04 Solaris /var                      
bf05 Solaris /home                       bf06 Solaris alternate sector          
bf07 Solaris Reserved 1                  bf08 Solaris Reserved 2                
bf09 Solaris Reserved 3                  bf0a Solaris Reserved 4                
bf0b Solaris Reserved 5                                          

```
I would say bf01. Not sure if it matters at all and when ZFS see's that partition type, what it does under the covers, but If I look at what I do as a general rule of thumb, I use type 'be00' for a boot partition, type 'bf00' for a root partition, type 'bfo2 for swap, type 'bf03' for Home, and type 'bf05' for ZFS RAID members... (that is my choice for those)

ZFS really doesn't hve a type reserved just for RAID Members like BSD does, but /usr??? When I see that, and there are somehow some filesystem shut down problems where writes might be pending, I see that as a RED Flag.

POSIX, UNIX, Linux guidance for /usr is:
> 
The /usr file system contains read-only commands, libraries, and data. 

So assumptions of ZFS, if 'per se' it looks at the partition type and see's /usr, it is going to assume that whatever is there is read-only data and not need to look for pending writes before it is shutdown.

Does that logic make sense to you? That might not be the case here. I may be overthinking that, but a possible gray area, if I were coding that and looking for some ways to make shutdown processes faster... (And, for some reason, that special /usr type 'exists' for ZFS.) So, for the 'just-in-cases' I would change the partition type for those.

---

### Post by papriak on 2023-04-15
> **MAFoElffen said:**
> Relook at the edit to my last post on what I found as 'questionable'... I'm sorry. I was editting it an it boinked... LOL This is what I was trying to point out and compare with mine...<br><br>On your ZFS pool data disks, What partition type code are you using from this list?
```

mafoelffen@Mikes-B460M:~$ sudo sgdisk -L | grep 'Solaris'
be00 Solaris boot                        bf00 Solaris root                      
bf01 Solaris /usr & Mac ZFS              bf02 Solaris swap                      
bf03 Solaris backup                      bf04 Solaris /var                      
bf05 Solaris /home                       bf06 Solaris alternate sector          
bf07 Solaris Reserved 1                  bf08 Solaris Reserved 2                
bf09 Solaris Reserved 3                  bf0a Solaris Reserved 4                
bf0b Solaris Reserved 5                                          

```
I would say bf01. Not sure if it matters at all and when ZFS see's that partition type, what it does under the covers, but If I look at what I do as a general rule of thumb, I use type 'be00' for a boot partition, type 'bf00' for a root partition, type 'bfo2 for swap, type 'bf03' for Home, and type 'bf05' for ZFS RAID members... (that is my choice for those)

ZFS really doesn't hve a type reserved just for RAID Members like BSD does, but /usr??? When I see that, and there are somehow some filesystem shut down problems where writes might be pending, I see that as a RED Flag.

POSIX, UNIX, Linux guidance for /usr is:

So assumptions of ZFS, if 'per se' it looks at the partition type and see's /usr, it is going to assume that whatever is there is read-only data and not need to look for pending writes before it is shutdown.

Does that logic make sense to you? That might not be the case here. I may be overthinking that, but a possible gray area, if I were coding that and looking for some ways to make shutdown processes faster... (And, for some reason, that special /usr type 'exists' for ZFS.) So, for the 'just-in-cases' I would change the partition type for those.

I just had the pool mounted as if it were another drive, separate from the "root" file system.

---

### Post by papriak on 2023-04-15
I was able to recreate the screen shown in the attachment, but I wasn't able to find my existing RAIDZ3 pool, nor recreate it in Terminal then find it in the installer afterward.

Please advise?


Also, is there a way to make it work in the Server edition of Jammy?

---

### Post by papriak on 2023-04-15
> **1fallen said:**
> Ok I got the go ahead, Thanks coffecat.
****Please know this going in or forward with these instructions**:**
1.More for Advanced or Power-users.(Far too much to define here)
2.This method :!:will use the entire disk:!:
3.I just can not word this any better than this:

Please forgive me if I overstepped my place for the quote, but it's perfect.
Now here we go, Boot to the live installer and once opened, now use a terminal and run:
```

sudo apt update

sudo apt install zfsutils-linux zfs-initramfs zfs-zed
```
Now proceed to the installer as normal.
wheniit come to the part for partioning layout or Installation type, use Erase disk, now click the tab Advanced Features and that will allow you to install on a zfs-root with Encryption*(optional)*(See Screenshot)
and if all goes well boot to your new zfs-root system. Good Luck, I'm off to work for a very short time.

Sorry, I meant to reply to this directly, but apparently I can't delete the other post.

---

### Post by MAFoElffen on 2023-04-16
> **papriak said:**
> Also, is there a way to make it work in the Server edition of Jammy?
Yes there is... Sort of*.

Both 1fallen and I create our installs using a LiveUSB Installer and do a lot of manual commands to create our ZFS installs. Both of us sort of use this as a guide for the foundation of it:
[https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html)

Both of us have created a list of commands that we use normally to do various installs, so we don't have to start cold each time. How do I know he does this also? We compare notes on what works for each, and what fails. It's a challenge and fun to us.

Disclaimer; These instructions are not for a new user, and requires some advanced Linux skills to do. This is for the OP, who has ZFS and Linux Experience.

I start the Ubuntu Server 22.04.2 Server Edition Live Installer. Once I get past the keyboard and language screens, you will notice a "Help" button in the upper right of the panel. Select that, and choose Command Prompt. (I have posted these instructions on this Forum... and it is detailed and long... LOL)

I then install openssh-server and set a static IP for the Live Session. I then connect to it via ssh from one of my workstations with a GUI ( graphical terminal session ). I have done it straight from the command prompt, but is a lot of typing. Doing that a few too many times... It's a lot easier to cut-and-paste from a script I created.

Once connected, the first thing I do is install zfs-intramfs and zfs-utils, after that, the Live Installer can see and work with ZFS. Then I pretty much follow that guide above, adding in another pool and datasets for my home, and another pool and datasets for my data. I work out the mounts like they have for bpool and rpool in that guide, for my other added pools/datasets. I create the pools and datasets fof ehat I want it to be... Then I mount everything, then I install into the data structure, usually by using either debootstrap, or rsync. Then I chroot into it to configure it, install any other packages I want there, and install/configure Grub.

For the user creation, I usually do that after the first boot, or create a cloud config to do that for me on the first boot. Some times just creating the user manually is faster and less work just doing it manually.

* So the sort of, is that it is a manual affair.

---

### Post by MAFoElffen on 2023-04-16
Hmmm. We talked about this, but we should probably check it just to make sure. You say you have 32GB of RAM. ARC, by default uses50% of RAM, though rule of thumb is 2GB for ZFS base, and 1GB per 1TB of pool. You are running an 18TB RAIDZ3 pool, so 20GB...
```

/usr/sbin/arc_summary > ./arc_summary.txt

```
Mine was too large to post or upload as a text file, so I copied it to a PasteBin: [https://paste.ubuntu.com/p/Nyf48BRw3G/](https://paste.ubuntu.com/p/Nyf48BRw3G/)

Also a quick summarized look at that
```

mafoelffen@Mikes-B460M:~$ arcstat
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
04:31:53     0     0      0     0    0     0    0     0    0   31G   31G    21G
mafoelffen@Mikes-B460M:~$ sudo zpool get cachefile datapool
NAME      PROPERTY   VALUE      SOURCE
datapool  cachefile  -          default
mafoelffen@Mikes-B460M:~$ sudo zdb -C datapool

MOS Configuration:
        version: 5000
        name: 'datapool'
        state: 0
        txg: 1902951
        pool_guid: 16005144428317223960
        errata: 0
        hostid: 1532761246
        hostname: 'Mikes-B460M'
        com.delphix:has_per_vdev_zaps
        vdev_children: 1
        vdev_tree:
            type: 'root'
            id: 0
            guid: 16005144428317223960
            create_txg: 4
            children[0]:
                type: 'disk'
                id: 0
                guid: 13881315049474949688
                path: '/dev/disk/by-id/ata-ST8000DM004-2U9188_ZR143PZD-part1'
                whole_disk: 0
                metaslab_array: 256
                metaslab_shift: 34
                ashift: 12
                asize: 4000776192000
                is_log: 0
                DTL: 2975
                create_txg: 4
                com.delphix:vdev_zap_leaf: 129
                com.delphix:vdev_zap_top: 130
        features_for_read:
            com.delphix:hole_birth
            com.delphix:embedded_data

```

---

### Post by #&amp;thj^% on 2023-04-16
> **papriak said:**
> I was able to recreate the screen shown in the attachment, but I wasn't able to find my existing RAIDZ3 pool, nor recreate it in Terminal then find it in the installer afterward.

Please advise?
Don't give up on this yet! *or let me know if you have already

> **papriak said:**
> 
Also, is there a way to make it work in the Server edition of Jammy?

Yes Sir but this will test your skills: [https://github.com/Sithuk/ubuntu-server-zfsbootmenu/blob/main/ubuntu_server_encrypted_root_zfs.sh](https://github.com/Sithuk/ubuntu-server-zfsbootmenu/blob/main/ubuntu_server_encrypted_root_zfs.sh)
Read through the script very carefully, change a few things like timezone and locale for one.
Another is the user name and password.
I think or would advise you to stay with a minimal GUI Desktop.
Maybe later try in a KVM for the server script. (I can't help but nanny suggest here)

---

### Post by papriak on 2023-04-16
> **1fallen said:**
> Don't give up on this yet! *or let me know if you have already



Yes Sir but this will test your skills: [https://github.com/Sithuk/ubuntu-server-zfsbootmenu/blob/main/ubuntu_server_encrypted_root_zfs.sh](https://github.com/Sithuk/ubuntu-server-zfsbootmenu/blob/main/ubuntu_server_encrypted_root_zfs.sh)
Read through the script very carefully, change a few things like timezone and locale for one.
Another is the user name and password.
I think or would advise you to stay with a minimal GUI Desktop.
Maybe later try in a KVM for the server script. (I can't help but nanny suggest here)

I'm not giving up on this yet, but I've decided to go with a minimal desktop installation.

I configured the script in the page you linked for the desktop version of Jammy, but running it keeps telling me that the "pool topology" isn't recognized and to check the pool topology variable.

How should I configure the script so there's only one pool, used as the root file system?

---

### Post by papriak on 2023-04-16
> **MAFoElffen said:**
> Hmmm. We talked about this, but we should probably check it just to make sure. You say you have 32GB of RAM. ARC, by default uses50% of RAM, though rule of thumb is 2GB for ZFS base, and 1GB per 1TB of pool. You are running an 18TB RAIDZ3 pool, so 20GB...

Yes, my server has 32GB of RAM which should be enough for eight 4TB drives in RAIDz3.

---

### Post by MAFoElffen on 2023-04-16
I am still missing something somewhere. Such as this was asked a few times here:
> **1fallen said:**
> Can you now show us this: ?
```
sudo zpool status -v
sudo zpool iostat -v
sudo zpool list -H -o capacity
```

Have we actually seen the output of these, especially while the pool is degraded? I think you said that you would do that when you got home, but when you got home, I think things got distracted... I went through the thread and do not see any output to those(???) If there somewhere, please point me to the post.

And i asked if you could install smartmon-tools and do long tests on the pool disks, but haven't heard back if they tested out as good or had errors. No sense in reinstalling or restoring pools to disks that are bad. 

Just thinking out loud, and thinking about what may be going on.

---

### Post by papriak on 2023-04-16
> **MAFoElffen said:**
> I am still missing something somewhere. Such as this was asked a few times here:

Have we actually seen the output of these, especially while the pool is degraded? I think you said that you would do that when you got home, but when you got home, I think things got distracted... I went through the thread and do not see any output to those(???) If there somewhere, please point me to the post.

And i asked if you could install smartmon-tools and do long tests on the pool disks, but haven't heard back if they tested out as good or had errors. No sense in reinstalling or restoring pools to disks that are bad. 

Just thinking out loud, and thinking about what may be going on.

I've destroyed and rebuilt that pool at least twice now, I'm afraid any data that may have helped is gone.

I got 9 of these disks after a company retired them, but they only give me problems when I send the reboot command through Webmin, and I know better than to press the reboot button on the case unless it's truly necessary.


Cockpit may be a more stable option, but right now I'm focusing on installing Ubuntu on a ZFS pool.


Do you think the problem could have been that the pool wasn't part of a root file system?  My current focus is to reinstall Ubuntu on the root pool as "/", instead of having Ubuntu on its own boot drive with RAIDZ on a separate root mount point.

---

### Post by MAFoElffen on 2023-04-16
I think that now finding out that you got nine used disks that had been retired is reinforcement to test them. Please do. The RAIDZ is being degraded for a reason. We just haven't found out why yet.

To me, a pool is a pool, whether it is alone or not. I will say again that I do not feel it is a good idea to put all your eggs in one basket. Meaning, I separate out my home and data pools. If you are doing this just to have ZFS-On-Root, then go for it. I promote ZFS and it overall is safer for me, but I think it is unrelated to your current problem. Do I think is is safer to have "everything" on root? No.

On most systems, I will setup my root OS and try to keep it somewhat separate from other things... Why? If you have a problem, such as your current problem of the data pool degraded, because the root was separate, the machine booted for you, and you were able to work on the problem. If you had a problem with your root OS, and your data pool is separate, then you just restore your root and import your data pool and you go on. This makes sense to me. This seems safer to my than having everything go south at one time and having no separation between potential problems...

Possible reasons that I can think of that might cause the degrade? Disk errors. File system errors. Memory faults. Cache faults. Even something as simple as that you created your RAIDZ with generic device names (/dev/sdX) instead of soecifc unique ID's (/dev/disk/by-id or /dev/disk-by-uuid)...

So do I think the information that is still remains there is useless? No.

---

### Post by #&amp;thj^% on 2023-04-16
EDIT: for this:
> **MAFoElffen said:**
> I think that now finding out that you got nine used disks that had been retired is reinforcement to test them. Please do. The RAIDZ is being degraded for a reason. We just haven't found out why yet.
+1
We really need to see something here or this marathon, will quickly turn into a TL:Dr
When I shutdown from a remote I just do a "shutdown -p now".
These are just some pointers/reminders.
I'm pretty sure the ZFS man pages give good information on what all the commands do, but here's the quick version

```
zpool export
```

Removes the pool from the system (but the pool is still intact). You will usually only do this when you want to move the pool to another system. Do not do this just to reboot the computer.
```

zpool attach/detach
```

These commands allow to to attach or detach devices from a ZFS mirror. If you build a ZFS pool with a single disk, you can attach a second disk to make it a mirror. You can then attach a third to make a 3-way mirror if you want. detach does the opposite and lets you remove disks from a mirror. A mirror is the only type of vdev that allows this. You *cannot* attach or detach disks from RAID-Z.
```

zpool replace
```

Fairly obvious. Used to replace a disk in the pool with a new one.

```

zpool remove
```

Removes a disk from the pool. As mentioned you cannot remove disks from RAID-Z, you can only remove disks from a mirror, and you use detach to do that. This command is only used to remove cache or log devices.

```

zpool offline
```

Takes a disk offline, so it's still part of the pool but temporarily unused. Obviously you must have redundancy to do this and ZFS will use the redundancy to keep the pool running. Most people will only use this rarely. Sun/Oracle say the following:
> 
    ZFS allows individual devices to be taken offline or brought online. When hardware is unreliable or not functioning properly, ZFS continues to read data from or write data to the device, assuming the condition is only temporary. If the condition is not temporary, you can instruct ZFS to ignore the device by taking it offline. ZFS does not send any requests to an offline device.


Another use mentioned by Sun/Oracle is to allow you to move disks around in the server (or between disk shelves in a large system) without any downtime. For instance if you attached a new disk shelf to a system, you could offline the disks one-by-one, move them to the new shelf, then bring them online again.

---

### Post by papriak on 2023-04-16
> **MAFoElffen said:**
> I think that now finding out that you got nine used disks that had been retired is reinforcement to test them. Please do. The RAIDZ is being degraded for a reason. We just haven't found out why yet.

To me, a pool is a pool, whether it is alone or not. I will say again that I do not feel it is a good idea to put all your eggs in one basket. Meaning, I separate out my home and data pools. If you are doing this just to have ZFS-On-Root, then go for it. I promote ZFS and it overall is safer for me, but I think it is unrelated to your current problem. Do I think is is safer to have "everything" on root? No.

On most systems, I will setup my root OS and try to keep it somewhat separate from other things... Why? If you have a problem, such as your current problem of the data pool degraded, because the root was separate, the machine booted for you, and you were able to work on the problem. If you had a problem with your root OS, and your data pool is separate, then you just restore your root and import your data pool and you go on. This makes sense to me. This seems safer to my than having everything go south at one time and having no separation between potential problems..

I agree that I would prefer to have my pool separate from the OS drive, but not if it makes the data unstable on reboot.


...I suppose I could simply not use reboot, and just shut down and restart the system.

Won't hurt anything to try, I suppose.  And I can give Cockpit a test as well.

---

### Post by MAFoElffen on 2023-04-16
I am sorry that I edit my posts, after I initially post them. I see what i said, and add what would make it more clear.... so it is a good idea to see what I added to that last post. There are things that I said that should be looked into further.

---

### Post by papriak on 2023-04-16
> **MAFoElffen said:**
> Possible reasons that I can think of that might cause the degrade? ...something as simple as that you created your RAIDZ with generic device names (/dev/sdX) instead of soecifc unique ID's (/dev/disk/by-id or /dev/disk-by-uuid)

That may have been the culprit...

I'll redo the "side-mounted ZFS" install using proper device IDs, load my backup onto it and let you guys know how it does after a reboot or two.

I have some errands to run too, so I'll report back this evening.


Thanks again for all your continued help!

---

### Post by MAFoElffen on 2023-04-16
I'm about to leave for work... 10 hours shift tonight. Same tomorrow night. But tomorrow is my Friday... (Hopefully I'll actually have days off this week. LOL)

---

### Post by papriak on 2023-04-16
> **MAFoElffen said:**
> I am still missing something somewhere. Such as this was asked a few times here:

Have we actually seen the output of these, especially while the pool is degraded? I think you said that you would do that when you got home, but when you got home, I think things got distracted... I went through the thread and do not see any output to those(???) If there somewhere, please point me to the post.

And i asked if you could install smartmon-tools and do long tests on the pool disks, but haven't heard back if they tested out as good or had errors. No sense in reinstalling or restoring pools to disks that are bad. 

Just thinking out loud, and thinking about what may be going on.


I got Ubuntu Desktop reinstalled (With RAIDZ3 as a side mount point this time) and used Cockpit instead of Webmin.

Still getting pool degradation when I click "Reboot", but not "Shutdown", and I got a screenshot of the Terminal commands this time for you guys.

---

### Post by MAFoElffen on 2023-04-17
There it is and that is your problem... See where the error says it can't find the label?

When you created your RAIDZ you specified in your list the devices /dev/sda,/dev/sdb,dev/sdc,/dev/sdd,/dev/sde,/dev/sdf,/dev/sdg./dev/sdh... On bootup, linus sometimes, if you have disks specified like that, looses track of which disk is which, and reassigns it differently. That is why fstab files now use UUID's.

When your do your create, use /dev/disk/by-id/<disk_name>-partX or /dev/disk-by-uuid/<disk_name>-partX... for each disk instead.

Look at this:
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls /dev/disk
by-id  by-label  by-partlabel  by-partuuid  by-path  by-uuid
mafoelffen@Mikes-ThinkPad-T520:~$ ls /dev/disk/by-id
ata-Dogfish_SSD_1TB_KC20210827738                  ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part1  wwn-0x5002538f31610c43        wwn-0x5002538f31610c43-part6
ata-Dogfish_SSD_1TB_KC20210827738-part1            ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part2  wwn-0x5002538f31610c43-part1  wwn-0x5002538f31a0aff1
ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N        ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part3  wwn-0x5002538f31610c43-part2  wwn-0x5002538f31a0aff1-part1
ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N-part1  ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part4  wwn-0x5002538f31610c43-part3  wwn-0x5002538f31a0aff1-part2
ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N-part2  ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part5  wwn-0x5002538f31610c43-part4
ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W        ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part6  wwn-0x5002538f31610c43-part5

```
Doing it that way, will change to the pointer to unique, instead of ambiguous. That way the pieces of the puzzle are always found, and put together in the correct order.

That will resolve your problem.

---

### Post by papriak on 2023-04-17
> **MAFoElffen said:**
> There it is and that is your problem... See where the error says it can't find the label?

When you created your RAIDZ you specified in your list the devices /dev/sda,/dev/sdb,dev/sdc,/dev/sdd,/dev/sde,/dev/sdf,/dev/sdg./dev/sdh... On bootup, linus sometimes, if you have disks specified like that, looses track of which disk is which, and reassigns it differently. That is why fstab files now use UUID's.

When your do your create, use /dev/disk/by-id/<disk_name>-partX or /dev/disk-by-uuid/<disk_name>-partX... for each disk instead.

Look at this:
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls /dev/disk
by-id  by-label  by-partlabel  by-partuuid  by-path  by-uuid
mafoelffen@Mikes-ThinkPad-T520:~$ ls /dev/disk/by-id
ata-Dogfish_SSD_1TB_KC20210827738                  ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part1  wwn-0x5002538f31610c43        wwn-0x5002538f31610c43-part6
ata-Dogfish_SSD_1TB_KC20210827738-part1            ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part2  wwn-0x5002538f31610c43-part1  wwn-0x5002538f31a0aff1
ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N        ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part3  wwn-0x5002538f31610c43-part2  wwn-0x5002538f31a0aff1-part1
ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N-part1  ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part4  wwn-0x5002538f31610c43-part3  wwn-0x5002538f31a0aff1-part2
ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N-part2  ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part5  wwn-0x5002538f31610c43-part4
ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W        ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part6  wwn-0x5002538f31610c43-part5

```
Doing it that way, will change to the pointer to unique, instead of ambiguous. That way the pieces of the puzzle are always found, and put together in the correct order.

That will resolve your problem.

While were editing that post, I found a command to import my existing pool using the UUIDs.  (See attachment)

When it's done scrubbing itself, I'll reboot the machine and see if the pool survives intact, and also whether its performance is any better than it was last night.

(It was getting transfer speeds up to 500MB/s to and from the pool when I made this thread, but this latest attempt was struggling to get to 50MB/s from an SSD in the same server last night.)

---

### Post by MAFoElffen on 2023-04-17
Yesssss. :P That looks much better. Crossing fingers and waiting. I know it can take a while for 18T's. LOL

---

### Post by #&amp;thj^% on 2023-04-17
Bazinga, by George i think that should do it..
Transfer speeds will vary, especially 18TB's worth. LOL

---

### Post by papriak on 2023-04-17
> **MAFoElffen said:**
> Yesssss. :P That looks much better. Crossing fingers and waiting. I know it can take a while for 18T's. LOL

Rebooted, and all the drives are Online this time, and scrubbed without errors.  :D

The transfer speed isn't much better though, averaging 50MB/s for a single 15GB file.

I'll make a new thread for that, this one seems to be resolved.


Thank you and 1Fallen both so much!

---

### Post by #&amp;thj^% on 2023-04-17
> **papriak said:**
> 
The transfer speed isn't much better though, averaging 50MB/s for a single 15GB file.

Don't make the mistake of judging ZFS performance on a fresh pool. The real torture test is on a well-used aged pool, and then it gets really interesting to see how performance is affected. Let it settle for a little more time.

Crap I forgot this as well, ZFS can attain SSD-like write speeds for a HDD pool when the pool is relatively empty. The reason for this is that large contiguous runs of free space are allocated for the transaction group, so when the txg is laid down, it's a largely sequential write. It doesn't matter if you *think* you are writing sequential data (like a media file) or random data (like a database or VM block store). ZFS is a copy-on-write filesystem so any filesystem write is never overwriting existing data in its existing location, and is always allocating free space somewhere else.

---

### Post by papriak on 2023-04-17
> **1fallen said:**
> Don't make the mistake of judging ZFS performance on a fresh pool. The real torture test is on a well-used aged pool, and then it gets really interesting to see how performance is affected. Let it settle for a little more time.
Crap I forgot this as well, ZFS can attain SSD-like write speeds for a HDD pool when the pool is relatively empty. The reason for this is that large contiguous runs of free space are allocated for the transaction group, so when the txg is laid down, it's a largely sequential write. It doesn't matter if you *think* you are writing sequential data (like a media file) or random data (like a database or VM block store). ZFS is a copy-on-write filesystem so any filesystem write is never overwriting existing data in its existing location, and is always allocating free space somewhere else.

Alright, thanks for clarifying that.  :)

---

### Post by MAFoElffen on 2023-04-17
Glad that everything worked out well. LOL

When you open that new thread to look and performance and tuning... Please attach a copy of the "arc_summary" report. 

Tuning for ZFS pools are done by playing with the size limits of the ARC cache sizes.

---

