---
title: "Add new ssd as 2 drive to system can't write to it after first use"
date: 2024-04-22
forum: General Help
---

### Post by linuxmic007 on 2024-04-22
Hello All,

I am running Ununtu 22.04.4 LTS and in dual boot with Windows 11. All is working well with the dual boot.  I add a new ssd as a 2nd drive for storage.  I wanted to use it between ubuntu and Windows 11 so i formatted it FAT (32-bit-version).  I was able to access / copy data files and folders to the drive without issue. After a day or so and a reboot. I went to copy more data over and was unable to. In researching it. root is the owner and the only one with permissions to the drive.  I have tried to  sudo chown  username:username Downloads   and I get chown: changing ownership of 'Downloads': Operation not permitted.  i have tried to take ownership of folders too by  sudo chown username:username teamviewer_qs.tar.gz   i get error  chown: changing ownership of 'teamviewer_qs.tar.gz': Operation not permitted What I need to do it take ownership and control or have full permissions to the drive just as i do to my home/Downloads.  I have some data that is not copying off correctly and need to see what full permissions rights may change about that.  A few screenshots are provided to help show what is going on. Any help out of this would be great!

Thx,

---

### Post by oldfred on 2024-04-22
You can only chown or chmod Linux formatted partitions, not Windows partitions like FAT32 or NTFS.
You set defaults by how you muount partition. Typically still owned by root, but with open permissions for read & write.
But if Windows fast start up is on, it may set hibernation flag preventing write. So default mount does not work. You may be able to manually mount read only.

Also FAT32 only recommended for smaller partitions. It does not support any file over 4GB and has no journal for recovery. Better to use NTFS if you mst write from Windows.

---

### Post by linuxmic007 on 2024-04-23
[SIZE=4][COLOR=#000000][COLOR=#222222][FONT=Verdana]Well thank you for the information I appreciate the quick response. It's very helpful.  It so happens today I found out i do NOT need one bit or byte of data on that drive so i can just re format it with NTFS. Lesson learned.[/FONT][/COLOR][/COLOR][/SIZE]

---

### Post by MAFoElffen on 2024-04-23
> **oldfred said:**
> You can only chown or chmod Linux formatted partitions, not Windows partitions like FAT32 or NTFS.
You set defaults by how you muount partition. Typically still owned by root, but with open permissions for read & write.
But if Windows fast start up is on, it may set hibernation flag preventing write. So default mount does not work. You may be able to manually mount read only.

Also FAT32 only recommended for smaller partitions. It does not support any file over 4GB and has no journal for recovery. Better to use NTFS if you mst write from Windows.
Yes... And no...

Do not format it as FAT32. That "is" for small filesystems.

Shared between Windows and Linux, I choose and recommend using NTFS. Their may be haters, but I've been doing this since 2005, for shared ta between Linux, Windows, Unix and MAC OSX.

If it were only Linux involved, then I recommend a native Linux Filesystem. But if multiple OS'es are involved, I recommend NTFS. It has been a universal go-between for over a decade.

You can chown and set permissions on a permanently mounted NTFS filesystem. Here is one of the fstab mounts to one of my ntfs filesystems that I mount on every boot:
```

UUID=828C01738C016351  /Media_H  ntfs  defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw  0  0

```
What oldfred said about Windows "fastboot" is 100%. I feel, even with my pure Windows only-customers, Windows fastboot is "evil". I don't recommend hibernation on Winodws... or anything that keeps the filesystem in an open-state on Windows. If you want a "fast" boot (when it works) and can afford to lose any files or changes, go for it. If not, then you can use Linux tools to help repair any Windows errors... but not if you have fastboot turned on.

People have paid me for data-recovery services, but if fastboot is turned on... sorry. Not going to happen.

---

### Post by linuxmic007 on 2024-04-23
Well thank you Sir.  I will be adding it to fstab.  Do i have to edit fstab in vim or can I do it  in nano?   Do I add the exact line you did or do I have to replace some of the identifying info such as  Screenshot attached of my mounted NTFS formatted 1TB drive. Would you mind giving me a good idea of what I should put in fstab and where in fstab for my drive in the screenshot?   Any hints on learning vim?

---

### Post by oldfred on 2024-04-23
You can see fstab
cat /etc/fstab

You have to use your UUID and create a mount point.
Check UUID:
lsblkt -f
sudo mkdir/Media_H # just to use MAFoElffen's example.
sudoedit /etc/fstab

More examples
Mount parameter examples, ext4, NTFS, exFAT:
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
NTFS example fstab entry - TheFu
[https://ubuntuforums.org/showthread.php?t=2493845](https://ubuntuforums.org/showthread.php?t=2493845)
exfat example - TheFu
[URL="https://ubuntuforums.org/showthread.php?t=2479368&p=14113300#post14113300"]https://ubuntuforums.org/showthread.php?t=2479368&p=14113300#post14113300

[https://wiki.archlinux.org/title/fstab](https://wiki.archlinux.org/title/fstab)

[/URL]

---

### Post by linuxmic007 on 2024-04-23
Hello,


I did a cat command for fstab and this is the last line in fstab.
/dev/disk/by-uuid/6ABD-4C49 /mnt/6ABD-4C49 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=WD_1TB_INT_SSD 0 0




Screenshot is my disk 1TB NTFS Drive   i notice the UUID is different. Yet, I did a full power down power up and my drive is read and writable.  Does this mean it's right in fstab or not?  Do need to add anything or replace a line to have full protection / access? Do I need to install any NTFS v4 tools in Ubuntu?

------ screenshots ----

---

### Post by oldfred on 2024-04-24
You are showing the automount that clicking on it from a gui app like file browser gives, not a correct mount in fstab. It defaults to the label you added to partition. I do suggest labels, particularly for partitions you do not mount in fstab. But I have labeled a partition Data and mounted in fstab using data. 
fstab is very specific on requirements. Go back to examples and copy & change to your UUID and mount point.

---

