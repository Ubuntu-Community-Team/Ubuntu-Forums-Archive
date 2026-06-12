---
title: "Ubuntu 24.04 &gt;&gt;&gt; I only have ReadOnly permission to blanck CD"
date: 2024-06-10
forum: General Help
---

### Post by BrassCat on 2024-06-10
Hello the forum. I am trying to write an ISO of Clonzilla to a CD. 
The drive is CD/DVD/Blu-ray. Problem probably exists for all 3
media types. The CD/DVD.. drive shows up in Drives screen and
reports Folder is Empty. In Permissions it reports [B]Unknown Permissions.
[/B]The drive is good, I wrote on it in 23.xx It also reads fine.
How do I get permission for my user account (administrator enabled) ??
Thanks for any help.

Stan

---

### Post by TheFu on 2024-06-10
Optical media generally can be written into just once. This is called "burning".  A "master" ISO file has to be created first containing everything you want AND that ISO file must be smaller than the largest size of the blank media.

You'll need to look at the optical device file permissions to determine if your userid is a member of the correct group that has write permissions.  On my systems, that file is usually something like /dev/sr0.  Usually the group would have write permissions, so you'd just need to add your normal userid to the group for the device file to have write permissions.  I don't have any optical devices connected now, so I can't show the exact file or permissions as an example from my system.

Then you'll need to use some burning software - I think Kb3 was the last software I used. It has been at least a decade since I "burned" any optical disks as either an ISO or purely as data.

---

### Post by Holger_Gehrke on 2024-06-11
To add the details TheFu couldn't provide:
The permissions on my DVD-writer are rw- rw- --- with owner root and group cdrom. My primary user id is a member of the group cdrom and I have had no problems burning CD or DVD discs using xfburn.

Holger

---

### Post by BrassCat on 2024-06-12
Thanks for the responses. Steps taken **before** my original post.

Downloaded ISO file for Clonezilla as source for burning CD, so its on my disk. Not the problem.
Have a supply of BLANK CDs and DVDs. BLANKS.
I have burned CD / DVD before. 
Drive icon for CD drive STATES IT IS A BLANK CD.
Optical Drive (CD) Right click on screen. select permissions, 

After reading the 2 responses: 

1)  Located  drive/cdrom

2)  brasscat@Ryzen56G:/dev$ ls -l cdrom
     lrwxrwxrwx 1 root root 3 Jun 12 11:47 cdrom -> sr0

3)  I also **am** a member of cdrom group.

4)  It seems I have permissions as member of group,  "RWX" read write execute.

5)  Tried with **K3B**, can not select CD as destination.

6)  Drive screen for CD/DVD under permissions states UNKNOWN PERMISSIONS
    also: the permissions of "CD/DVD Creator" could not be determined.
    Checked "CD/DVD Creator" but does not seem to exist or I don't know where it is ?
 
    brasscat@Ryzen56G:/dev$ ls -l "CD/DVD Creator"
    ls: cannot access 'CD/DVD Creator': No such file or directory

I am a little ( or more) over my head here! Please help.

Stan.

---

### Post by TheFu on 2024-06-13
```
lrwxrwxrwx 1 root root 3 Jun 12 11:47 cdrom -> sr0
```
is just the symlink.  We need to see the output from
```
ls -al /dev/sr0

```to know the real device file permissions. Please use forum code-tags for all CLI output. That will retain the spacing and columns.

---

### Post by BrassCat on 2024-06-14
Hello TheFu, thanks for the reply.

```
brasscat@Ryzen56G:~$ ls -al /dev/sr0
brw-rw----+ 1 root cdrom 11, 0 Jun 14 09:58 /dev/sr0
```

You wrote "is just the symlink". I am unaware of the difference. OK, I see
articles on this. Will study.

Curious, as a member of cdrom, it appears I have read and write permissions ???

---

### Post by TheFu on 2024-06-14
> **BrassCat said:**
> Hello TheFu, thanks for the reply.

```
brasscat@Ryzen56G:~$ ls -al /dev/sr0
brw-rw----+ 1 root cdrom 11, 0 Jun 14 09:58 /dev/sr0
```

You wrote "is just the symlink". I am unaware of the difference. OK, I see
articles on this. Will study.

Curious, as a member of cdrom, it appears I have read and write permissions ???

Well, there's a '+' character at the end of the shown permissions, which means that ACLs are being used and that the permissions displayed may be completely bogus. You'll need to use the **getfacl** command to see the real permissions.  Hopefully, those won't override what is being displayed, but it is possible.  ACLs are very powerful, but terrible for visibility of permissions.  In 30+ yrs of doing Unix/Linux, I've needed to use ACLs just twice and they were very handy, but these days, I'll call ACL-abuse on lots of project teams because ACLs let them be lazy.  For example, if you aren't in the cdrom group, you could add your personal group to the ACLs of the sr0 file with rw permissions, if you liked, but these permissions wouldn't be clearly shown until someone uses getfacl to see them.

---

### Post by BrassCat on 2024-06-14
Thanks ThuFu, I have run the suggested command. Now I need to read up on this.

```
getfacl /dev/sr0
getfacl: Removing leading '/' from absolute path names
# file: dev/sr0
# owner: root
# group: cdrom
user::rw-
user:brasscat:rw-
group::rw-
mask::rw-
other::---
```

I ran again without the / in front of dev/sr0.
getfacl considered it an error.

---

### Post by BrassCat on 2024-06-14
I am running the new release Ubuntu 24.04. Should be others having this problem.

---

### Post by TheFu on 2024-06-14
> **BrassCat said:**
> I am running the new release Ubuntu 24.04. Should be others having this problem.

Very few people burn optical media anymore.  I haven't since at least 2015.  With Flash drives being huge and cheap, the lifespan of most home-burned optical media is about the same as a typical flash storage device.  Get a pack of 128-256GB microSD cards or just a few $100 12TB HDD and the convenience over optical media is clear.

---

### Post by BrassCat on 2024-06-18
Well, thanks for the responses,

I have been working in micros before the Z80 came out. What fun. I have many projects stored to CD and DVDs, of course, that started years later. I CAN still read those CDs no problem. They work fine for me, but I do use thumb drives for short term tasks. Ubuntu 22 LTS did not have this problem. 23  (.10?) did not have this problem. I loaded my sata ssd with 22.04 LTS in my new Ryzen machine . It has no problem recognizing blank CDs, DVDs. It also writes to them. Something is funny with 24.04 LTS with regard to this problem. Yes I like 24.04.

Booted using my sata ssd 22.04, I wrote my ISO for Clonezilla onto CD. This machine, this hardware. The hardware is fine. Anyway, hope they get the bug fixed soon. Thanks for the attempts to resolve this issue.

Stan

---

