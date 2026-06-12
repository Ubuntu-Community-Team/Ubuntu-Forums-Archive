---
title: "4 years using Ubuntu ... 2 problems not related with Ubuntu ..."
date: 2024-04-16
forum: General Help
---

### Post by aug7744 on 2024-04-16
Thanks for reading my topic.
I use Lubuntu since 2020 being Ubuntu with LXQT. Good OS even.
What is the only problem ? The terrible fatal error parent transid in BTRFS.
I lose the count of number of times that fatal error has happened.
The BTRFS partition goes to an point not being possible mount or fix it.
I never had used an file system with fatal errors at point impossible to fix or even recover files.
BTRFS when working without error is amazing, but when an problem happen need pray.

Anyone known an fstab setting or other settings for avoid that type of error with better chances for mounting when happen that parent transid error ?


The other problem is related with date and hour.
Lubuntu allow select RTC hour in local computer BIOS hour.
The problem is when you does an hour date sync in internet. Wil be done an correc sync for OS, but the RTC and synced hour not are the same value being as internally the kernel use some minutes or seconds ahed of RTC time.
You understand it ? How disable that feature and when doing an manual date hour sync using internet is done an sync in RTC too ?

I had used an USB drive to start boot Lubuntu OS for try fix the btrfs partition and when finished the boot process was done an automatic date hour sync.
After was done an OS start boot using the computer disk and strangely the hour was 3 hours ahead of RTC. Possibly when was done an usb drive os boot an action was done in OS disk installation and changed some files date.
I not want the OS doing it.

Have an nice week for you.

---

### Post by TheFu on 2024-04-16
BTRFS hasn't been known as the 100% trouble-free file system, ever.  If you care about your data, choose a different file system.  It is fine to play around with BTRFS, but do it with play data, nothing critical.  Also, having versioned, daily, automatic, backups for any data, regardless of the file system use, is required, but even more required when using a file system that has issues.

For clock stuff, UNIX is designed to have UTC used internally and in the CMOS.  You should choose that for all time settings and have only the TZ used to change the displayed timezone information based on your local place in the world.  

Think of the display settings as being internal computer and GUI versions.  You'll need to set the clock for both your GUI with the correct timezone and for the console with the correct timezone.  
Use **sudo timedatectl** to set the non-GUI date/time for the computer. This will write that information to the CMOS clock at shutdown automatically.   [https://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt](https://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt) has more details if that doesn't "just work".

For how to do it in your GUI, find the GUI Desktop Manual and follow those instructions.  I use a very simple GUI and just set the TZ environment variable in my ~/.bashrc, like this:
```
export TZ="America/New_York"
```
If everyone on the system is located in the same place, I'd set /etc/timezone with a line like this:
```
America/New_York
```

The list of approved timezones can be seen by running **tzselect**

As for keeping your time synchronized, there are multiple ways.  I think ubuntu still uses ntp as implemented in the systemd-timed.system unit file.  I found that tool drifted way to much for my needs, so I use chrony instead.  Chrony supports legacy NTP and newer PTP protocols.  On my clients running **chronyc**, I see very accurate time - ±21µsec.  That's  ±0.000021sec, yep, close enough.  Some are in the hundreds of nanoseconds, so even more accurate!  Yeah!

MSFT started this problem by defaulting to localtime as the only time used on PCs in the old days.  I don't recall when, but I think around Win95, they finally got the idea of NTP and accurate time.  Sadly, the MSFT infrastructure services included with DHCP and DNS and ActiveDirectory have always done a crappy job of keeping time.  I opened a bug with them around 2003 and was told through our corporate MSFT SEs that ±5min was considered accurate enough.  So I started using my Windows laptop's wrong time to show up to meetings3-5 minutes late, when that was the clock.  My little protest didn't get anything changed.  In the UNIX world, sub-second, synchronized, accurate time has been solved since the mid-1980s.  It is am embarrassment for MSFT not to have this stuff all solved40+ yrs later.  An embarrassment, I say.  

As late as 2010, I had some MSFT systems that couldn't keep time. Even updating hourly they would drift multiple minutes in less than 60 minutes.  I know the hardware was fine. I loaded Linux onto one of the systems AND used it as my LAN time server for all other systems.  All of those kept sub-second, accurate time.  The only difference was WinNT Server compared to Linux. Linux kept correct time. Windows didn't.  Finally, I setup the Windows systems on the LAN to sync their time every 10 minutes to keep the drift under control.

Nobody should need to run their own time server at home, but I had to just for the Windows computers.

Sorry about the rant.  Time isn't supposed to be this hard.  systemd-timed should easily be able to maintain sub-second accurate time, but if it had, I wouldn't have replaced it with chronyd.  I only swap out the default solutions when they fail me.  YMMV, of course.

---

### Post by #&amp;thj^% on 2024-04-16
On Ubuntu I can not create a descent "fstab file" when installing the system, but with my Arch system I can create a very solid fstab file:
```
 /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=2AA0-BB28                            /boot/efi      vfat    defaults,noatime 0 2
UUID=dd589524-f570-469d-b35d-3e5e814c0ee3 /              btrfs   subvol=/@,defaults,noatime,compress=zstd,commit=120 0 0
UUID=dd589524-f570-469d-b35d-3e5e814c0ee3 /home          btrfs   subvol=/@home,defaults,noatime,compress=zstd,commit=120 0 0
UUID=dd589524-f570-469d-b35d-3e5e814c0ee3 /root          btrfs   subvol=/@root,defaults,noatime,compress=zstd,commit=120 0 0
UUID=dd589524-f570-469d-b35d-3e5e814c0ee3 /srv           btrfs   subvol=/@srv,defaults,noatime,compress=zstd,commit=120 0 0
UUID=dd589524-f570-469d-b35d-3e5e814c0ee3 /var/cache     btrfs   subvol=/@cache,defaults,noatime,compress=zstd,commit=120 0 0
UUID=dd589524-f570-469d-b35d-3e5e814c0ee3 /var/tmp       btrfs   subvol=/@tmp,defaults,noatime,compress=zstd,commit=120 0 0
UUID=dd589524-f570-469d-b35d-3e5e814c0ee3 /var/log       btrfs   subvol=/@log,defaults,noatime,compress=zstd,commit=120 0 0

```

Again I can not use this type of install on Buntu, I'm not saying it's impossible, but it escapes me presently.

For Ubuntu I agree with TheFu best to use a different FS

---

### Post by aug7744 on 2024-04-16
Thanks for all replies.

@TheFu
"BTRFS hasn't been known as the 100% trouble-free file system"
Correct.
If happen an file system damage in FAT32, ntfs, ext2 , ext4 and exfat at point not is possible mount has easy tools to recover data.
About repair BTRFS is good in paper. In reality is terrible. Search in internet "btrfs parent transid how recover" and see the links. Terrible in most cases not is possible fix it or even read the data.

Have another file system doing automatic file compression compatible with Ubuntu ?

Thanks for your reply about time sync.

@1fallen
"On Ubuntu I can not create a descent "fstab file" when installing the system"
I use the setting below and works.
defaults,noatime,nodiratime,lazytime,acl,noautodefrag,barrier,commit=6,compress-force=zlib:9,datacow,datasum,noflushoncommit,max_inline=0,metadata_ratio=0,nospace_cache,treelog 0 0

compress-force being zlib has more high compression.


Other being the more worst problem is when happen OOM. Is an the more bizarre details in Linux.
Good sense if you try use an software doing more allocation than the ram size plus swap the correct is automatically close the software.
The bizarre detail is need to be configured to close software when happen an OOM. Even windows has that same problem.
Nohang help to avoid it, but if using zram the zram settings not work, At least ram settings works.
Today I lose again an btrfs partition because OOM when flushing data in btrfs partition so being an partial writen destroying file metadata an ctree.

You being an user want use an setting or software to avoid useless writen in disk or even better memory management and really the setting does the work plus risk of fatal errors. Not perfect path used, but you continue using the settings because not has another solution in moment.

---

### Post by TheFu on 2024-04-16
The way to prevent data loss is to have backups.  Daily, versioned, backups.  If anything bad happens, wipe the disk and restore from backups.

---

### Post by #&amp;thj^% on 2024-04-16
+1 with TheFu plain and simple.

---

