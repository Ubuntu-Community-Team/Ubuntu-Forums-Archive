---
title: "fsck being run at EVERY boot is driving me crazy - just like this debian guy"
date: 2016-01-25
forum: General Help
---

### Post by bmullan2 on 2016-01-25
I've been having this problem ever since I upgraded to 15.10 months ago.

On every boot I see:

Scanning for BTRFS file system
fsck from util-linux 2.26.2

The above takes nearly 1 minute to run which accounts for nearly all the delay in my boot time.    I've done probably a hundred google searches and see LOTS of people asking WHY fsck is running on every boot.

Those people are using all sorts of distro's from Ubuntu & Debian to Arch, and Suse

I have read the Man pages on  -[ systemd-fsck@.service, systemd-fsck-root.service, systemd-fsck]("http://manpages.ubuntu.com/manpages/vivid/man8/systemd-fsck.8.html").   -   I added the boot command line option   **fsck.mode=skip** to the line in **/etc/default/grub** changing 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"   
to...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash fsck.mode=skip" 

then doing a "sudo update-grub" and reboot...   **fsck still ran at every boot**

I tried setting the PassNo to 0 for the BTRFS  "/" and "/home" entries in my /etc/fstab ...  **the fsck still ran at every boot**.

Finally I was going to just give up and live with the extra minute+ delay in boot time when I[URL="https://lists.debian.org/debian-user/2015/01/msg00196.html"]**found a thread on the Debian mailer list that made me laugh as the guy posting it was having the same problems & had tried the same solutions all to no avail & its driving him CRAZY too.**
[/URL]
NOTE:   make sure you read the whole thread....!

He like myself can't find a reason the fsck is being run (my disks report clean if I check them... so does his).

my /boot is EXT4
my / and /home are BTRFS

Does anyone have a clue why this is happening or anything else to try?   

There seems to be no apparent way to stop the FSCK from running at every boot.
[B]
I would like to add that for BTRFS file systems there seems to be a consensus that FSCK is not required ...  so should it even be automatically run against BTRFS file systems at boot or any other time??   Maybe it should be a User decision??

On the [Linux Kernel BTRFS Wiki]("https://btrfs.wiki.kernel.org/index.php/Btrfsck") they point to Marc Merlin's as a source for BTRFS use guidance [and on Marc's wiki he says the following]("http://marc.merlins.org/perso/btrfs/post_2014-03-19_Btrfs-Tips_-Btrfs-Scrub-and-Btrfs-Filesystem-Repair.html"):
[/B]
**[B][SIZE=3]You mostly don't need fsck on btrfs[/SIZE]**

[/B]** Btrfs does not have a really useful fsck, which many people think is  horrible and make btrfs unsafe. In real life, there are many ways to  mount btrfs filesystems with problem, or extra data out of them if they  are too corrupted to mount. **

---

### Post by Dennis N on 2016-01-26
The details of file system checks by systemd are explained here:

[http://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html](http://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html)

This seems to be saying file systems in fstab are checked _every_ boot* if pass no. > 0. I looked at journalctl, and that appears to be so. The time on my system is less than a second total for all checks**. This system has two drives, an SSD and a standard HD. Only the ESP is indicated as checked on the SSD, not the Root file system - I assume it was checked in the initramfs. The standard HD has a check indicated of it's single file system, used for data.

* rereading more carefully, I gather the check service is run each boot, but whether the service actually does a check depends on other factors:
> This helper will decide if the filesystem should actually be checked based on the time since last check, number of mounts, unclean unmount, etc.

(so, in journalctl: "Starting File System Check on /dev/disk/by-uuid/8395cc9b..." does not mean by itself that a check was done, only that the service was started.)

** probably because the service determined not to do any actual checks.

---

### Post by ajgreeny on 2016-01-26
I have used 15.10 and 16.04 only in VBox VMs, but at every boot I get the quick mention of **fsck from util-linux 2.27.1; /dev/sda1 clean** but it does not appear to actually run; it just mentions it.  This takes only a second or less to happen so my transcript of what it says may be slightly incoerrect.

This is also borne out by running ```
sudo tune2fs -l /dev/sda1
``` which shows that the last time the filesystem was checked was a few  days ago (I have it set to check once a month).Here is my tune2fs output from Lubuntu 16.04, installed 22 Jan and booted several times every day since.  It was checked only at first boot after installing and has not been checked since in spite of that message at every boot.
```
Filesystem created:       Fri Jan 22 18:54:24 2016
Last mount time:          Tue Jan 26 11:49:09 2016
Last write time:          Tue Jan 26 11:49:07 2016
Mount count:              10
Maximum mount count:      -1
Last checked:             Fri Jan 22 18:54:24 2016
Check interval:           0 (<none>)
```

---

### Post by bmullan2 on 2016-01-26
Thanks Dennis.... yeah I'd read that same info on freedesktop.org about this.   

I think the whole process at boot is hard to untangle.  I guess part of the problem of the developing & increasing use of systemd.

**One post I read made a lot of sense to me though regarding whether even doing an FSCK on BTRFS makes any sense !!**

The post referenced the BTRFS website's own warning about BTRFSCK... re fsck for btrfs.

On the [BTRFS web site they warn that using BTRFSCK should always be a last resort]("https://btrfs.wiki.kernel.org/index.php/Btrfsck") because:

[I]If you have a broken filesystem, you should probably look at the recovery or [repair]("https://btrfs.wiki.kernel.org/index.php/FAQ#When_will_Btrfs_have_a_fsck_like_tool.3F") tools or you can read [Marc MERLIN's page that explains the different ways to check and fix a btrfs filesystem]("http://marc.merlins.org/perso/btrfs/post_2014-03-19_Btrfs-Tips_-Btrfs-Scrub-and-Btrfs-Filesystem-Repair.html"). 
[/I]
[I]In a nutshell, you should look at: 
[/I]

[LIST]
[*]* btrfs scrub to detect issues on live filesystems *
[*]* look at btrfs detected errors in syslog (look at Marc's blog above on how to use sec.pl to do this) *
[*]* mount -o ro,recovery to mount a filesystem with issues *
[*]* btrfs-zero-log might help in specific cases. Go read [Btrfs-zero-log]("https://btrfs.wiki.kernel.org/index.php/Btrfs-zero-log") *
[*]* btrfs restore will help you copy data off a broken btrfs filesystem. See its page: [Restore]("https://btrfs.wiki.kernel.org/index.php/Restore") *
[*]* **btrfs check --repair, aka btrfsck is your last option if the ones above have not worked**. *
[/LIST]

[I]Note that while this tool should be able to repair broken filesystems,  it is still relatively new code, and has not seen widespread testing on a  large range of real-life breakage. It is possible (but highly unlikely  in the most recent versions) that it may cause additional damage in the  process of repair. btrfs check --repair received significant updates prior to v4.0. You are  strongly recommended to use a version after v4.0 when trying to recover  a filesystem. 

[/I]**I wonder if Ubuntu/Debian might be better off NOT running BTRFSCK automatically at any time because of the above and maybe just issue a Message to the user that they might want to consider doing it ???**[I]

Brian
[/I]

---

### Post by bmullan2 on 2016-01-26
Thanks AJ ... but I use BTRFS and as far as I know Tune2FS doesn't work with BTRFS (according to man page -  man tune2fs)...

---

### Post by Dennis N on 2016-01-26
I get a similar read, and it seems to confirm it has not run. Dec 4 in this case is the day and time of installation of the OS!

```
[dmn@Zotac ~]$ sudo dumpe2fs /dev/sda4 | grep check
dumpe2fs 1.42.13 (17-May-2015)
Last checked:             Fri Dec  4 13:31:02 2015

```

My journal always contains a message:

```
Zotac systemd-fsck[258]: Common-Files: clean, 15446/7684096 files, 9661636/30720000 blocks
```

Sometimes it shows briefly on the monitor, but that depends on what OS is running. This is my separate data partition on a separate HD. No message like the above about the root fs on my SSD, or the EFI system partition on the SSD, although the latter has an indication the service is started (below). Perhaps lack of message is because it is FAT32. For the root fs, I gather it is checked by another service in initramfs. Nothing recorded in the journal about that.


```
Jan 25 20:08:27 Zotac systemd[1]: Found device Samsung_SSD_850_EVO_250GB 1.
Jan 25 20:08:27 Zotac systemd[1]: Starting File System Check on /dev/disk/by-uuid/94C3-7016...

```

Again, from my interpretation of the article, seeing a message like this doesn't mean a check was done, just that the service was started. It then checks the various conditions that warrant a check, and then cancels checks if not warranted.

All this is not yet completely understood.

..............................................
**@bmullan2**

I suggest you see when the file system was last checked by the commands shown by me or ajgreeny. Look at your journal and see what messages pertain to file system checks:

To display the journal for the most recent boot:

**journalctl -b**

no sudo required.

The time being consumed may indicate a problem, and the journal may reveal something in it's messages. Is it related to you using a different fs? I don't know.

EDIT: [COLOR="#FF0000"]This post was written before seeing your two posts (which were not there when I started it), so doesn't reflect anything you said there.[/COLOR]

---

### Post by bmullan2 on 2016-01-26
I'd already looked at the journal before and there is nothing that indicates any problem...

$ journalctl -b | grep boot

Jan 26 07:28:01 server1 kernel: smpboot: Allowing 8 CPUs, 0 hotplug CPUs
Jan 26 07:28:01 server1 kernel: smpboot: CPU0: AMD FX(tm)-8350 Eight-Core Processor (fam: 15, model: 02, stepping: 00)
Jan 26 07:28:01 server1 kernel: smpboot: Total of 8 processors activated (64215.23 BogoMIPS)
Jan 26 07:28:01 server1 kernel: vgaarb: setting as boot device: PCI:0000:01:00.0
Jan 26 07:28:09 server1 systemd[1]: boot.mount: Directory /boot to mount over is not empty, mounting anyway.
Jan 26 07:28:09 server1 systemd[1]: Mounting /boot...
Jan 26 07:28:09 server1 systemd[1]: Mounted /boot.
Jan 26 07:28:25 server1 systemd[1]: Starting Seed the pseudo random number generator on first boot...
Jan 26 07:28:26 server1 systemd[1]: Starting Container hypervisor based on LXC - boot time check...
Jan 26 07:28:26 server1 cron[872]: (CRON) INFO (Running @reboot jobs)
Jan 26 07:28:26 server1 systemd[1]: Starting LSB: Record successful boot for GRUB...
Jan 26 07:28:26 server1 systemd[1]: Started Seed the pseudo random number generator on first boot.
Jan 26 07:28:28 server1 systemd[1]: Started Container hypervisor based on LXC - boot time check.
Jan 26 07:28:31 server1 systemd[1]: Started LSB: Record successful boot for GRUB.
Jan 26 07:29:08 server1 systemd[1]: Starting LXC Container Initialization and Autoboot Code...
Jan 26 07:29:08 server1 systemd[1]: Started LXC Container Initialization and Autoboot Code.

$ journalctl -b | grep fsck

Jan 26 07:28:01 server1 systemd[1]: Listening on fsck to fsckd communication Socket.
Jan 26 07:28:01 server1 systemd[1]: Created slice system-systemd\x2dfsck.slice.
Jan 26 07:28:09 server1 systemd-fsck[613]: /dev/sda1: clean, 315/488640 files, 103047/1952768 blocks

---

