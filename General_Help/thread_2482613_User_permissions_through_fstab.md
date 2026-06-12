---
title: "User permissions through fstab"
date: 2023-01-05
forum: General Help
---

### Post by hornetster on 2023-01-05
Setting up a dual boot pc (win10/ubuntu), and trying to figure out how to mount a filesystem in fstab, with specific permissions.
Have setup a separate drive in windows, with the top directories being user names, and their data below these. ie have moved user data (the main directories - documents/download/music etc) to the separate hard drive.
I then load this using fstab (currently using uid/gid=1000 - that's mum!). But would like to be able to load so the kids have access to their own directories, and not others, but mum has access to all...
Is on an exfat formatted drive.
Is this possible?

Thanks.

---

### Post by TheFu on 2023-01-05
> **hornetster said:**
>  Is this possible?

Yes, but probably not for a beginner.  You'll need to understand users, groups, permissions.
It would be much easier if the storage wasn't a foreign file system.  With ext2/3/4, f2fs, zfs, or any of the other native Linux file systems that support full POSIX permissions, you can find my "working together" posts in these forums.  You'll need to do this, but through the fstab mounts only, which isn't easy.

Rather than trying to describe what you want, please show the directories, owners, groups, and permissions desired as though it was a native file system. Then you'll be able to work out the needed fstab entries.

So, the needed format is that which is provided by 'ls -al' - we don't need specific file names, just examples.
If it were me, I'd setup network storage and allow MS-Windows access to that storage by each individual user and allow NFS access for Linux systems using normal Unix permissions.

What's important is to know which users need read-only access and which users need read-write access to each storage area.  Then setup the permissions for each of those situations on a per-user basis under MS-Windows.

Errr .... using foreign file systems makes this all ugly, assuming you don't want to allow everyone the ability to delete everything.  Perhaps the best answer is to have really good versioned backups and allow the source storage to allow full control by everyone. If the worst happens, you'll be able to put it back and the kids  would learn that their actions have repercussions.  Just be certain to maintain sufficient versioned backups to support restores for enough time.

BTW, better to use NTFS instead of exFAT.  exFAT isn't journaled, whereas NTFS is.  The only time to exFAT is for flash drives.  For SSDs and HDDs, use NTFS with MS-Windows.  If access will only be over a network (not dual boot), then use a native Linux file system like ZFS or ext4.  Samba can be used to allow CIFS access over the network to MS-Windows devices. All others should use NFS or some mode of ssh (sshfs, sftp, scp, rsync).  For example, any Kodi media center player accessing network files for streaming should use NFS.

---

### Post by Impavidus on 2023-01-06
I was wondering wether it's possible to set userID in the different directories separately through bind mounts, but the manual suggest it's not.

Is that signature line below your post still correct? If it is, move to the next Ubuntu release. Else, update your forum signature. Ubuntu 21.10 is dead.

---

### Post by yancek on 2023-01-06
Are you wanting to access data on the ntfs (windows) partitions from Ubuntu?  Standard Linux permissions are meaningless on windows partitions so you should do some research on using dmask, fmask and umask.  If you have separate directories for each user personal data, you could start by giving ownership to the specific directory to the specific user on his/her top level directory.

---

### Post by MAFoElffen on 2023-01-06
+1 with TheFu. You set group permissions for all the specific directories to be read by your mum in a group. Another group is for the kids, which has less permissions. Set by folder.

Contrary to yancek, you can set NTFS permissions in Windows also using groups. It just that Windows does not respect Linux permissions, nor does Linux respect Windows NTFS permissions (without LDAP and AD), so they have to be setup separately.

Explaining how to do each would take a few posts and more info would be needed to help you.

---

### Post by TheFu on 2023-01-06
I've tried to use the "permissions" options on NTFS using fake Ms-Windows userids.  They appeared to work for a little bit, but 2 weeks later, they stopped and never worked (or appeared) to work again.

For read-only access, I'd use the 'other' permissions. 755
For read-write access, I'd use a 'group'.    770
For single-user read-write access, I'd only use the 'owner' - 700
That's on the Unix side controlled by mount options.
For NTFS, on Windows, do whatever you feel is best. It will all be ignored by Linux.

---

### Post by MAFoElffen on 2023-01-06
What I meant was on the Windows side, lock it down to Windows user groups. Separately on the Linux side, set Linux user group permissions. Why both and the repetition? Because Windows doesn't know about nor respect Linux permissions, nor Linux know about and respect Windows permissions, so each is controlled separately. And that will happen if you don't have LDAP, AD and the Linux side connected to a Windows Domain. I'm still trying to summarize, but the concept understood yet?

That is basically for a dual boot machine with multiple users... That is not a part of a Windows Server Domain.

---

### Post by yancek on 2023-01-06
> Contrary to yancek, you can set NTFS permissions in Windows also using groups. 

Of course you can but, permissions in Linux to access ntfs don't carry over to windows.  To access ntfs from Linux I would think the user/group option would be best  for what the OP seems to want in both windows and Linux.

---

### Post by MAFoElffen on 2023-01-06
@yancek - Nothing personal. No malice or slight intended. Just saying there is more to it.

> **MAFoElffen said:**
> What I meant was on the Windows side, lock it down to Windows user groups. Separately on the Linux side, set Linux user group permissions. 
I thought what I said might be understood without getting into details. What you said in your last post is true, but it needs to be taken care of on the Windows side also. Neither respect each other, and it needs to be dealt with on both sides.

On the Linux side, in the fstab you just say for options : 
UUID=xxxxx /where/mounted defaults 0 0
... then you set group permissions. which would lock it down by group membership... That is what both you and TheFu said. I agree there.

Where your disagreement is is beyond that. On the Windows side, set NTFS permissions to group for different permissions based on group membership, just like you did on the Linux side.

Then Windows will respect the Windows permissions and Linux will respect the Linux permissions. Each user gets it's permission from the respective OS and how it is setup. This is how I setup network shares in a mixed environment without a Domain, ldap, kerberos, and active directory. There is no other integrated solution that takes care of both sides of that, that I am aware of, without Domain.

It's a dual-boot, There are multiple users. Why leave the Windows side open and insecure? The answer needs attention on both sides, to do it right.

You can do what you want. I'm just sharing what I do for integrated environment solutions for customers...

---

### Post by Morbius1 on 2023-01-06
> **Impavidus said:**
> I was wondering wether it's possible to set userID in the different directories separately through bind mounts, but the manual suggest it's not.

A bind mount won't work but a bindfs mount might ...............

Let's say the partition is mounted at /Data and it has a subfolder for kid1: /Data/kid1

Install bindfs:
```
sudo apt install bindfs
```
Then do a temporary remount of the subfolder with a different set of permissions from the parent:

```
sudo bindfs -o perms=0660:+X,force-user=kid1,force-group=mum,nonempty /Data/kid1 /Data/kid1
```

*[COLOR="#B22222"]That's not a typo. I am mounting a subfolder to itself.[/COLOR]*

Did my own experiment to show how this would work:

Changed ownership of the parent /Data directory to uid=tester,gid=tester

Changed permissions so only tester has access to /Data: umask=0077

Instead of kid1 I used smbuser

Then I ran the bindfs mount:
```
sudo bindfs -o perms=0660:+X,force-user=smbuser,force-group=tester,nonempty /Data/smbuser /Data/smbuser
```

Permissions from the top shows:
> ~$ ls -al /Data
total 12
drwx------  3 tester  tester 4096 Jan  6 17:28 .
drwxr-xr-x 25 root    root   4096 Jan  6 17:25 ..
drwxrwx--x  2 smbuser tester 4096 Jan  6 17:30 smbuser

And permissions within the subfolder looks like this:
> ls -l /Data/smbuser
total 0
-rw-rw---- 1 smbuser tester 0 Jan  6 17:30 test.txt


Only smbuser ( one of the kids) has access to his subfolder - except for tester ( mum ).

You can set this up in fstab - with a differnt sytax - so it happens on boot. 

Try the manual mount first to see if it satisfies the use case.

To unmount:
```
sudo umount /Data/kid1
```

---

### Post by Morbius1 on 2023-01-06
The more I think about this it may be just a bit too weird to mount a folder onto itself. It will work but it looks weird.

Just create a new folder at the same level as /Data like /kid1 for example.
```
sudo bindfs -o perms=0660:+X,force-user=kid1,force-group=mum,nonempty /Data/kid1 /kid1
```

---

### Post by Paddy Landau on 2023-01-06
> **Morbius1 said:**
> The more I think about this it may be just a bit too weird to mount a folder onto itself.
It's a time-honoured tradition!

Seriously, though, you **must** mount it onto itself to prevent people from accessing the original mount without required permissions.

I've used this mount method before to achieve a similar goal, and as far as I can tell, it's foolproof; only root can bypass this.

---

### Post by hornetster on 2023-01-06
Thanks for the detailed response.

> /home/data$ ls -al
total 772
drwxr-xr-x 7 kobi kobi 131072 Jan  7 09:32  .
drwxr-xr-x 6 root root   4096 Jan  6 11:51  ..
drwxr-xr-x 2 kobi kobi 131072 Jan  6 00:37 '$RECYCLE.BIN'
drwxr-xr-x 8 kobi kobi 131072 Jan  6 10:29  Archie
drwxr-xr-x 8 kobi kobi 131072 Jan  6 10:29  Jude
drwxr-xr-x 8 kobi kobi 131072 Jan  6 10:27  Kobi
drwxr-xr-x 2 kobi kobi 131072 Jan  6 00:36 'System Volume Information'

This is the root directory of the exfat data drive in the dual-boot pc.
Kobi needs full access to all, and the users Jude and Archie only need access to their personal directories...

Back story is: Windows users, on a low performance PC that I am trying to 'tempt' across to Ubuntu/Linux via performance/use benefits... So the drive is setup initially as a windows drive, but, hopefully, with some tweaks, a usable Linux PC...

---

### Post by TheFu on 2023-01-07
> **hornetster said:**
> Thanks for the detailed response.

```
/home/data$ ls -al
total 772
drwxr-xr-x 7 kobi kobi 131072 Jan 7 09:32 .
drwxr-xr-x 6 root root 4096 Jan 6 11:51 ..
drwxr-xr-x 2 kobi kobi 131072 Jan 6 00:37 '$RECYCLE.BIN'
drwxr-xr-x 8 kobi kobi 131072 Jan 6 10:29 Archie
drwxr-xr-x 8 kobi kobi 131072 Jan 6 10:29 Jude
drwxr-xr-x 8 kobi kobi 131072 Jan 6 10:27 Kobi
drwxr-xr-x 2 kobi kobi 131072 Jan 6 00:36 'System Volume Information' 
```

This is the root directory of the exfat data drive in the dual-boot pc.
Kobi needs full access to all, and the users Jude and Archie only need access to their personal directories...


I fixed the quote to use code tags, which are needed to get things lined up.  Please use code tags for all terminal output.
So,  first, please format the drive to be NTFS, not exFAT.  Journaled file systems are a great thing and need to be used.  exFAT isn't journaled.  Trust me. You want NTFS.

There are multiple ways to accomplish the next part - allowing access only to the people who need it. 
But you need to be clear - is this access read-only or read-write?  It matters.  Saying "access" isn't sufficient.   
Does kobi need readonly or read-write access too?  
Does it matter if kobi has access to all the files on the system that any of these users create or do you want to respect their privacy?  If kobi having access is fine, then you can just add kobi to the existing groups that the other userids already are members.  
OTOH, if you only want read-write access to the files on this partition for each of the users, then you'll need to create a new group for each and place both kobi and the other users into the specific group they will share.
Still, if kobi only needs read-only access, then the existing permissions are fine.
You don't mention if read-only access should be provided under each user's directory for the other users. We need to know that clearly too.  If not, then the 'other' set of permissions needs to be blocked.  So at mount, either 750 or 755 or 775 or 770 will be used for the directories.  

The file permissions will need to be set as well.  Generally, I'm against setting execute permissions on any files under non-native file systems.  That would be 660, 640 or 664 or 644 permissions, depending on your answer.

Clear as mud?

You'll need a separate mount for each to support the different permissions.  Using a bind mount will be needed if this is a single partition in reality, so you'll just want to mount the main storage to a location and block the directory above the mount to be 700. Simple. Elegant solution to preventing other users. No need for fancy mount-on-the-same-mount location stuff.

---

### Post by Morbius1 on 2023-01-07
> **Paddy Landau said:**
> It's a time-honoured tradition!

Seriously, though, you **must** mount it onto itself to prevent people from accessing the original mount without required permissions.

I've used this mount method before to achieve a similar goal, and as far as I can tell, it's foolproof; only root can bypass this.
I apologize in advance if this comes across as too confrontational - it's more of a knee-jerk reaction on my part - but there is no **must** in Linux:

> ~$ sudo chmod 0700 /Temp
~$ ls -dl /Temp
drwx------ 2 root root 4096 Dec 28 07:22 /Temp
~$ sudo mkdir /Temp2
~$ sudo bindfs -o perms=0666:+X,force-user=tester,nonempty /Temp /Temp2
~$ ls -dl /Temp
drwx------ 2 root root 4096 Dec 28 07:22 /Temp
~$ ls -dl /Temp2
drwxrwxrwx 2 tester root 4096 Dec 28 07:22 /Temp2

No one but root can access /Temp while everyone and your Aunt Tilly can access /Temp2.

---

### Post by Paddy Landau on 2023-01-07
> **Morbius1 said:**
> … there is no **must** in Linux
…
No one but root can access /Temp while everyone and your Aunt Tilly can access /Temp2.
**Today I learned!**

Thank you for correcting me, and for reminding me that there's always more than one way to address something in Linux!

---

### Post by Morbius1 on 2023-01-07
> **hornetster said:**
> 
```
/home/data$ ls -al
total 772
drwxr-xr-x 7 kobi kobi 131072 Jan 7 09:32 .
drwxr-xr-x 6 root root 4096 Jan 6 11:51 ..
drwxr-xr-x 2 kobi kobi 131072 Jan 6 00:37 '$RECYCLE.BIN'
drwxr-xr-x 8 kobi kobi 131072 Jan 6 10:29 Archie
drwxr-xr-x 8 kobi kobi 131072 Jan 6 10:29 Jude
drwxr-xr-x 8 kobi kobi 131072 Jan 6 10:27 Kobi
drwxr-xr-x 2 kobi kobi 131072 Jan 6 00:36 'System Volume Information'


```
This is the root directory of the exfat data drive in the dual-boot pc.
Kobi needs full access to all, and the users Jude and Archie only need access to their personal directories...


So if you don't want to create more directories for each user and keep the current mount point of /home/data my suggestion would be something like this:

Add umask=0066 to the list of options in fstab for the exfat partition. For example:
```
UUID=XXXX-XXX /home/data exfat defaults,uid=1000,umask=0066 0 0
```
[COLOR="#B22222"]This will be accessible only to uid=1000 but all other users will be able to traverse the /home/data folder.[/COLOR]

A temporary bindfs mount would look something like this:
```
sudo bindfs -o perms=0660:+X,force-user=jude,force-group=kobi,nonempty /home/data/Jude /home/data/Jude
```
[COLOR="#FF0000"]EDIT: I should have noted that because of restrictive setting on /home/data the user "jude" would have to specify the entire path to gain access to his folder. So in the location bar in the file manager he would have to specify /home/data/Jude. He could bookmark it for future use.
[/COLOR]
And an fstab entry would look something like this:
```
/home/data/Jude /home/data/Jude fuse.bindfs perms=0660:+X,force-user=jude,force-group=kobi,nonempty,x-systemd.requires=/home/data 0 0
```

Note: systemd should be smart enough to know that the bindfs mount of /home/data/Jude is dependent upon /home/data being mounted first so "x-systemd.requires=/home/data" shouldn't be necessary but ... well ... you know ... just in case.

---

### Post by Paddy Landau on 2023-01-07
> **Morbius1 said:**
> ```
sudo bindfs -o perms=0660:+X,force-user=jude,force-group=kobi,nonempty /home/data/Jude /home/data/Jude
```
What does [FONT=courier new]nonempty[/FONT] mean? I can't find this option for bindfs.

---

### Post by Morbius1 on 2023-01-07
It's not a bindfs option but a mount.fuse option:
> nonempty
              Allows mounts over a non-empty file or directory.  By  default  these   mounts  are
              rejected to prevent accidental covering up of data, which could for example prevent
              automatic backup.
I stated doing this by default because *[COLOR="#FF0000"]according to my notes[/COLOR]* I once got an error message telling me to add it:
 > fuse: mountpoint is not empty fuse: if you are sure this is safe, use the 'nonempty' mount option


---

### Post by Paddy Landau on 2023-01-08
> **Morbius1 said:**
> It's not a bindfs option but a mount.fuse option
Thank you. That's useful to know.

---

