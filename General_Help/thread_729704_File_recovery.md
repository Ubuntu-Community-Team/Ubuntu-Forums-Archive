---
title: "File recovery"
date: 2008-03-20
forum: General Help
---

### Post by HeliClimber on 2008-03-20
I accidentally deleted my entire video collection. It is on an external harddrive, and now the drive doesn't want to mount. When I plug it in, I get the message that the ntfs is marked in use. I can manage to run photorec on it, but it only gives me a bunch of files, and none of them are the complete video files. Can anyone please help me here. Thanks in advance.

---

### Post by ajgreeny on 2008-03-20
If you have a windows install, you should get it up and running and then plug in the drive, wait for it to be recognised, and then do a proper safe removal; don't just pull it out before you do that or you will still have the problem.  If you don't have windows yourself, find someone else who does.

---

### Post by HeliClimber on 2008-03-20
I don't have access to a windows comp right now(the desktop crashed completely, cmos went bad). Is there a command or program that I can run in order to clear this up. I know that the first step in recovering this drive is to be able to mount it. Thanks for the advice, and I wish that the desktop was up and going because I have windows based programs that would already have this data back in my hands.

EDIT: I finally got the drive to mount from the terminal with the read only option(just to be on the safe side. Does anyone have any suggestions on software to use for the recovery of the lost files.

---

### Post by Herman on 2008-03-21
I haven't tried it, but I would guess the ntfsundelete might be useful.

ntfsundelete comes from the ntfsprogs package, so you'll need to install ntfsprogs first,
```
sudo apt-get install ntfsprogs
```You might just want to start with an ordinary file system check first, and see if that helps,
```
sudo umount /dev/sda1
```Where /dev/sda1 is the hard disk and partition of your USB disk. Please change that to suit whatever yours comes up as in a partition editor, or run 'sudo fdisk -lu' to find out.
```
sudo ntfsfix /dev/sda1
```

Then if you still need to, you can run ntfsundelete and keep your fingers crossed for best results, first tkae a look at the man page for ntfsundelete to decide what options you might want to use,
```
man ntfsundelete
```
I think you''ll need to run this with the file system unmounted as you would with a file system check, I'm not sure.
Good luck,
Regards, Herman :)

---

