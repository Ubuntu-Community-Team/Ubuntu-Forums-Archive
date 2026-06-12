---
title: "[SOLVED] Permissions Issues"
date: 2007-11-21
forum: General Help
---

### Post by CNLiberal on 2007-11-21
I was a long time Fedora user.  I decided to give Ubuntu a try, and it's very user friendly.  Unfortunately, I don't have much experience with permissions and I need some help.  I've got a MythDora 4.0 install with a soft RAID5 mdadm array on a different machine.  I have exported the /storage directory (the array) and have NFS mounted that to this ubuntu 7.10 box as the same /storage.  I can see the files just fine.  I can play audio and video no problem.  However, I can't write to this folder.  I'd like to be able to have write perms to this folder, while still keeping them on the MythDora box.  Is this possible for two machines to have read/write access to these files?  Do owner perms have to change?  Thanks for your help.

Jim

---

### Post by bingoUV on 2007-11-22
The owner of the file is a user on the server machine. That user may not exist in the client machine. What do you get if you "ls -l" for the folder and the files at the client machine?

---

### Post by fragos on 2007-11-22
I regularly use NFS between my laptop and desktop, both Ubuntu.  I use the same user name on both boxes and everything, including R&W, works well.  I use a mount command rather than editing fstab.  If I'm not mistaken fstab can mount read only or R&W.

---

### Post by mptpro on 2007-11-23
I am having thhe same problem.  I cannot delete files on a networked computer.  I have the same user and pass on both machines.

---

### Post by CNLiberal on 2007-11-23
> **bingoUV said:**
> The owner of the file is a user on the server machine. That user may not exist in the client machine. What do you get if you "ls -l" for the folder and the files at the client machine?

Bingo,

Thanks for taking the time to respond to my post.  As you requested, I have ran the ls -l command from my client machine (Gallifrey) on the /storage directory which is NFS mounted from the MythBackend machine.  Here is the output.

```
joltman@gallifrey:/$ ls -l storage
total 358692
-rwxrwxrwx  1    1001 joltman      3755 2007-07-08 21:55 asound.conf
drwxrwxrwx 10    1001 joltman      4096 2007-11-20 17:25 Azureus
drwxrwxrwx  6    1001 joltman      4096 2007-09-29 12:56 Backup
-rwxrwxrwx  1    1001 joltman     93479 2007-03-28 18:01 bookmarks.html
-rwxrwxrwx  1    1001 joltman   8093696 2007-05-27 09:39 boot.iso
drwxrwxrwx  2 joltman joltman      8192 2007-11-23 10:44 cover
drwxrwxrwx  2    1001 joltman      4096 2007-09-28 20:07 cover (copy)
drwxrwxrwx 21    1001 joltman      4096 2007-11-21 17:13 Documents
drwxrwxrwx  2    1001 joltman      4096 2007-11-23 03:05 dorabackup
drwxrwxrwx 12    1001 joltman        80 2007-09-23 17:10 games
-rwxrwxrwx  1    1001 joltman     50113 2007-04-30 18:42 gfhcmd-0.1.9-0.i686.rpm
drwxrwxrwx  2    1001 joltman      4096 2007-03-27 16:29 Images
drwxrwxrwx  3    1001 joltman         8 2007-09-23 17:06 misc
drwxrwxrwx 27    1001 joltman     16384 2007-11-11 22:04 music
drwxrwxrwx  2    1001 joltman         1 2007-09-23 17:10 mytharchive
drwxrwxrwx  2    1001 joltman        32 2007-09-23 22:12 mythstreamtv
drwxrwxrwx 34    1001 joltman      4096 2007-11-07 18:01 mythvideo
drwxrwxrwx  2    1001 joltman      4096 2007-09-30 20:05 Nicotine
drwxrwxrwx  2    1001 joltman         1 2007-09-23 17:10 pictures
drwxrwxrwx  6    1001 joltman        48 2007-07-15 17:05 pix
drwxrwxrwx  2    1001 joltman         1 2007-09-23 17:10 posters
drwxrwxrwx  2    1001 joltman      8192 2007-11-22 18:00 recordings
drwxrwxrwx  3    1001 joltman        24 2007-03-28 17:44 SIERRA
drwxrwxrwx  9    1001 joltman        72 2007-11-17 19:46 Software
drwxrwxrwx  2    1001 joltman         1 2007-09-23 17:10 temp
drwxrwxrwx  2    1001 joltman        48 2007-11-11 17:14 Trailers
-rw-r--r--  1    1001 users   358601608 2007-11-20 11:42 ubuntu-7.10-desktop-i386.iso
drwxrwxrwx  2    1001 joltman         1 2007-09-23 17:10 videos
```

The backend machine has got a user named joltman just like my user on the client machine.  In the properties for the /storage folder on the client machine (Gallifrey), the owner is showing as 1001 and the group as joltman ( a group I created on the server machine).  Any help would be appreciated.  Thanks!

Jim

---

### Post by bingoUV on 2007-11-23
CNLiberal, 
    When you have 2 different machines, same username on both the machines does not guarantee that the users are same. It is UIDs that must be the same. In your case, the owner of the files is joltman of server machine. Its UID is 1001. 

The user joltman on client machine does not have UID 1001. So the client machine does not think the owner of the files is the joltman user of the client machine. You must edit the UID of the joltman user on client machine to be 1001. But there is a catch.

The client machine might already have a user the UID of which is 1001. In this case, it is not possible to change the UID of joltman to 1001. Verify this by looking in the file /etc/passwd. The fields are colon ( : ) separated. The 3rd field is UID. Check if any user has this UID. If not, simply change the UID of joltman by the following command. If yes, skip ahead.
```

sudo usermod --uid 1001 joltman

```If you find a user on the client machine of which the UID is already 1001, choose a UID that is not there. Also check the server machine to decide on a UID that does not exist on server machine also. UIDs upto 1000 are reserved for special system accounts, so choose something greater than 1000.
Suppose 1010 is such a UID that is not present in either of your machines. Then run the following command on both the machines to change the UID of joltman users.
```

sudo usermod --uid 1010 joltman

```

---

### Post by bingoUV on 2007-11-23
fragos, 
     It is likely that such setup works without doing anything on your part. Especially because both are Ubuntu. This is because Ubuntu creates users with UIDs starting with 1000. So first user created has UID 1000 on both machines, second has 1001 and so on. If the users have been created in the same order, username and UIDs match perfectly.

But Fedora(for example) creates users starting 500. So even the first Ubuntu user and first Fedora user don't have same UIDs. Hence you have to edit UIDs for NFSing(or sharing data partitions) between Ubuntu and Fedora.

---

### Post by fragos on 2007-11-23
> **bingoUV said:**
> fragos, 
     It is likely that such setup works without doing anything on your part. Especially because both are Ubuntu. This is because Ubuntu creates users with UIDs starting with 1000. So first user created has UID 500 on both machines, second has 1001 and so on. If the users have been created in the same order, username and UIDs match perfectly.

But Fedora(for example) creates users starting 500. So even the first Ubuntu user and first Fedora user don't have same UIDs. Hence you have to edit UIDs for NFSing(or sharing data partitions) between Ubuntu and Fedora.

Thanks, I wasn't aware of the UID thing which was the same for both my machines.  My account was the first one created on both machines.  There's always more to learn.

---

### Post by CNLiberal on 2007-11-26
Success!!  A simple usermod change and all my issues went away.  That made me feel a LOT better.  I guess it makes sense too.  In Winblowz, you are assigned a SID.  Active Directory uses that unique SID for all your permissions and it identifies you as you.  Unfortunately, I had to take it to windows territory.  My job at work is to keep windoze servers running.  They won't even consider Linux.  Thanks so much!

Jim

---

