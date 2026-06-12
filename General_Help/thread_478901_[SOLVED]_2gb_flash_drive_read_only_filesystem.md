---
title: "[SOLVED] 2gb flash drive read only filesystem?"
date: 2007-06-19
forum: General Help
---

### Post by strabes on 2007-06-19
I'm getting this message: > alex@alex-laptop:~$ sudo rm -r /media/702-2029690/.dmrc
rm: cannot remove `/media/702-2029690/.dmrc': Read-only file system

The filesystem is fat16. What is going on? How can I fix this? I tried to delete the partition in qtparted and it wouldn't let me. Yes, qtparted was opened as root, and yes it was unmounted at the time.

If I try chmodding it, here's what happens. It looks like something's wrong with the firefox profile that I backed up. > alex@alex-laptop:~$ sudo chmod -R 777 /media/702-2029690/
chmod: changing permissions of `/media/702-2029690/': Read-only file system
chmod: changing permissions of `/media/702-2029690/.Trash-strabala': Read-only file system
chmod: changing permissions of `/media/702-2029690/.Trash-strabala/avj9x1z9.default': Read-only file system
chmod: changing permissions of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions': Read-only file system
chmod: changing permissions of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}': Read-only file system
chmod: changing permissions of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults': Read-only file system
chmod: changing permissions of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences': Read-only file system
chmod: changing permissions of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn': Read-only file system
chmod: changing permissions of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base': Read-only file system

---

### Post by Qu4k3R on 2007-06-20
Do a:
cat /etc/fstab

And list your mounted filesystems:
sudo fdisk -l

:s

---

### Post by johntkucz on 2007-06-21
Hi, I'm having the same problem, and got this as a result (with a flash drive)

Disk /dev/sda: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         967      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7872     2015216    e  W95 FAT16 (LBA)


Both of those, the 2gb and 1gb flash drives give the read-only disk error!

---

### Post by Qu4k3R on 2007-06-21
Have you tried to "chown" it ?

sudo chown alex -R /media/702-2029690/

Maybe this topic can help you:
[http://ubuntuforums.org/showthread.php?t=480151](http://ubuntuforums.org/showthread.php?t=480151)

---

### Post by strabes on 2007-06-21
> alex@alex-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2   *        2433        4344    15358140   83  Linux
/dev/sda3            4345        4466      979965   82  Linux swap / Solaris
/dev/sda4            4467       11978    60340140   83  Linux

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7872     2015216    6  FAT16

I never put it in fstab because it's a removable flash drive; it mounts automagically.

Here's the output of sudo chown alex -R /media/702-2029690/:

> 
alex@alex-laptop:~$ sudo chown alex -R /media/702-2029690/
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/5d8v.def.aul': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/default/.ext': No such file or directory
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/s/langpa.ck-': No such file or directory
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/.org\r\nex.ten': Input/output error
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/.mozilla./fi': No such file or directory
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/t/extens.ion': No such file or directory
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/-8cd6-08.002': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;//home/st.rab': No such file or directory
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/kphf5d8v..de': Read-only file system
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/195f5-92.e7-': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/ozilla/f.ire': No such file or directory
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/ba5-2e5e.206': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/ome/stra.bal': No such file or directory
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/hf5d8v.d.efa': Input/output error
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/aaa-ae26.-44': Input/output error
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/\r\n[theme.dir': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/ib/firef.ox/': No such file or directory
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/7e08-447.4-a': Input/output error
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/8&#402;{û&#9554;|&#8730;&#966;.\006\023&#9484;': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/x&#8804;ö\tÿb&#9560;f.ü&#9632;&#8319;': Read-only file system
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/n\\pù<9äu.6&#8729;l': Input/output error
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/&#9524;&#9608;í²çñ\001p.&#9556;&#9579;\025': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/±8²&#8805;é=\030&#9532;.\a!z': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/\fx&#963;æ6&#9619;n\027.$\022ä': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/&#9562;: ÿ2\b&#9557;&#9570;.ú&#8359;\r': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/é&#9573;3&#9570;y\005&#8976;x.&#9617;&#8730;&#945;': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/&#9561;\rvl\030&#9604;x).\vü&#9580;': Read-only file system
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/&#402;ô&#9618;yb&#9616;ê&#9558;.&#8993;\033"': Input/output error
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/¥x&#963;\025ñ6ï&#9578;.é\t¬': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/&#9580;&#9552;=\t&#9474;ÿ\rö.&#9604;&#9604;&#9492;': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/¥w&#9554;&#9612;&#9619;3n\031.\022<q': Read-only file system
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/ß*.&#9568;ß&#9578;': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/e<&#8729;lrºeç.±|}': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/&#9496;&#9524;\033s&#9573;&#9578;&#9572;\005.ê&#966;4': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/£$\025°ngk).4x½': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/d&#8993;&#8359;&#9472;shs(.÷t&#9616;': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/&#9579;:æ#]:&#9563;ì.\023&#9566;&#9619;': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/k&#9569;&#9574;\002&#9496;ç&#963;æ.q\tt': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/\t5&#8993;ï,ën\002.&#9492;ü`': Read-only file system
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/&#963;kd&#9573;&#9632;\nw..&#963;\\&#8805;': Input/output error
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/µ&#949;k&#966;\035&#9492;&#9565;&#9600;': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/²9&#9608;\n&#9632;æ&#9577;\022.j&#8801;&#9552;': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/º\031&#9484;»&#9574;\n&#9554;ñ.&#9608;¼1': Read-only file system
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/f\003i&#8801;:y\036-.z7,': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/¼&#915;é&#402;9-2&#8319;.=h': Read-only file system
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/v\020&#9619;¬æ&#9524;ìg.&#9612;\026&#9577;': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/ö\024gbm\021è&#9567;.&#8804;ñ&#9580;': Read-only file system
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/\031lê¢#\026&#9616;g.é&#9580;ß': Read-only file system
chown: cannot access `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/\020&#937;&#8745;&#9612;&#9572;&#964;&#966;n.æ\004:': Input/output error
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/\006&#8805;&#9617;&#9608;de`¡./\033\f': No such file or directory
chown: changing ownership of `/media/702-2029690/.Trash-strabala/avj9x1z9.default/extensions/{DDC359D1-844A-42a7-9AA1-88A850A938A8}/defaults/preferences/.svn/text-base/_&#9570;&#9617;ùi=&#8319;m.h\033&#8804;/}c&#9492;k&#9576;&\004&#9617;.ç÷â': Read-only file system


Looks a little corrupt to me.

---

### Post by strabes on 2007-06-29
bump

---

### Post by Qu4k3R on 2007-06-30
I would force the mount.
PS: Don't forget to backup your files..

---

### Post by strabes on 2007-07-31
This fixed it: ```
sudo mkfs.vfat -F 16 -n UbuntuUSB /dev/sdb1
```

Basically I just removed the old vfat file system and created a new vfat one. The "-n UbuntuUSB" part is the name/label of the filesystem. It also determines its mount location in /media.

Warning: This will erase all the data on your usb drive.

---

