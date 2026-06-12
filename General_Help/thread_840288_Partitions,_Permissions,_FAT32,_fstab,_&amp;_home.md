---
title: "Partitions, Permissions, FAT32, fstab, &amp; /home"
date: 2008-06-25
forum: General Help
---

### Post by chadoh on 2008-06-25
I bought a new hard drive and installed xp pro on it. Then I used a linux rescue cd and partitioned my drive up into four parts: ntfs for xp, ext3 for ubuntu 8.04 Hardy, linux swap, and a FAT 32 partition to be used for sharing files between xp and ubuntu. This was my first time with all of this, I'm new at linux/ubuntu and have very limited experience with things like terminal.

So the dual boot works fine. The shared drive works fine with windows. But in ubuntu, the shared drive (which appears as a folder called "share" in /) is read-only. More accurately, the "My Documents" folder is read-only (I moved my "My Documents" folder in windows to this partition, because I want to share nearly all of my files between the two).

From reading other posts, I discovered that my problems might have to do with this mystical "fstab", so I "sudo gedit /etc/fstab"ed in terminal and it says

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=08fa3640-b716-4227-806b-429f287af0de /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=485F-ABD5  /share          vfat    utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=7c7eea3c-1d73-410d-9b8e-deefad28439a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I don't know what any of this means.

Also, Ubuntu recognizes the ntfs partition as a media drive, and I did not expect it to recognize it at all. I seem to have unlimited privileges with all of it. This surprised me.

Finally, I'd like to move my home directory to the "My Documents" folder on the shared partition. From what I gather this is quite difficult, or at least it used to be, but it'd be most excellent.

In summary: I need permission to access (in ubuntu) the "My Documents" folder from windows which lives on a shared FAT32 partition, and I would like to make it my home folder (which is currently /home/chad). 

I'm in Hardy Heron, the windows system is xp pro sp3.

---

### Post by ilrudie on 2008-06-25
Can the super user write to the partition?

Try sudo touch /share/test.txt.

See if that makes the file on that partition.

Also are you a member of the plugdev group(GID=46)?  Check with cat /etc/group | grep 46

See if your username is in the list.  If its not add yourself to that group and see if you can write to the partition.

---

### Post by owlgorithm on 2008-06-25
The /etc/fstab file tells Linux exactly where your drives are and what to do with them. As in a lot of Linux, there is a lot of power/configurability here but it's weird the first time you see it. The columns, from left to right, tell it (a) the name of the drive, (b) where to mount the drive, (c) what filesystem is on the drive, (d) options for who can access the drive and what they can do with it, and (e/f) maintenance options to be performed automatically.

As far as mounting the drive in a different location, you can do that by changing column (b), but I would recommend instead to move all media files to your /share drive and then create symbolic links to those folders. These are like mail-forwarding for your folders -- Ubuntu will look for the file on one drive but be invisibly directed to the other drive for movies, documents, etc.

To do this for your Music folder, for instance, use
```

cp -rf ~/Music/* path_to_WindowsMusicFolder
rm -rf ~/Music
ln -s path_to_WindowsMusicFolder ~/Music

```

(Sorry for typing "path_to_WindowsMusicFolder" -- its actual path escapes me, I don't have a Windows box. Fill that in and you'll be good to go.)

---

### Post by owlgorithm on 2008-06-25
Then, you can change the line in your /etc/fstab from 

```

# /dev/sda2
UUID=485F-ABD5 /share vfat utf8,umask=007,gid=46 0 1

```

to

```

# /dev/sda2
UUID=485F-ABD5 /share vfat utf8,umask=007,uid=xxx,gid=yyy 0 1

```

where xxx and yyy are your user and group ID's, which can be found by

```

id username

```
where "username" is your username (creative, no?)

---

### Post by bodhi.zazen on 2008-06-25
Edit fstab :

```
gksu gedit /etc/fstab
```

Modify :

```
# /dev/sda2
UUID=485F-ABD5  /share          vfat    utf8,[color=blue]**uid=1000,gid=100,dmask=027,fmask=137**[/color] 0 [color=blue]**0**[/color]
```

For more relaxed permissions use : dmask=000,fmask=111

Then remount:

```
sudo umount /share
sudo mount /share
```

---

### Post by bodhi.zazen on 2008-06-25
> **owlgorithm said:**
> T(creative, no?)

close, see my post :twisted:

Educational moment :

umask=000 sets file as executable, check out dmask and fmask.

Also in the last column, "1" should be used for / 

0 = do not check and is best for FAT and NTFS
2 = check after root and is best for linux non root partitions (not swap)
3 = there is no 3,4,5 ...

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

[uhelp]community/Fstab[/uhelp]

---

### Post by owlgorithm on 2008-06-25
My bad, I just meant my naming convention was lame. Thanks for the educational moment -- this is exactly why I love these forums.

---

### Post by chadoh on 2008-06-25
ilrudie: when I "cat /etc/group | grep 46", it says 

plugdev:x:46:chad

I don't know what this means, or what you had me type in means. Is that a good message? And how do I add myself to it if that's saying I'm not there?

I can save to the partition itself, but the My Documents folder, which was put there using windows, cannot be written to or deleted from in Ubuntu. I can only open and view the documents, but cannot edit them. Things outside of the "My Documents" folder on the partition can be deleted, however, and new things can be saved. But for iTunes in xp and Rhythmbox in Ubuntu to share the same music library, I need access to the My Documents folder in Ubuntu.

everyone else: I think I mislead everyone with this fstab business, since it turns out I do, indeed, have permissions for the partition. BUT I do not have permission to the My Documents folder, which is the only thing I care about in that partition. Sorry, and thanks so far.

---

### Post by bodhi.zazen on 2008-06-25
> **chadoh said:**
> ilrudie: when I "cat /etc/group | grep 46", it says 

plugdev:x:46:chad

I don't know what this means, or what you had me type in means. Is that a good message? And how do I add myself to it if that's saying I'm not there?

I can save to the partition itself, but the My Documents folder, which was put there using windows, cannot be written to or deleted from in Ubuntu. I can only open and view the documents, but cannot edit them. Things outside of the "My Documents" folder on the partition can be deleted, however, and new things can be saved. But for iTunes in xp and Rhythmbox in Ubuntu to share the same music library, I need access to the My Documents folder in Ubuntu.

everyone else: I think I mislead everyone with this fstab business, since it turns out I do, indeed, have permissions for the partition. BUT I do not have permission to the My Documents folder, which is the only thing I care about in that partition. Sorry, and thanks so far.

LOL

Educational moment part 2:

Take a look at permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[uhelp]community/FilePermissions[/uhelp]

Basically everything is owned by a user + group and permissions are ser for owner, group, an other.

If you do not have permission you can not have access.

Groups are in /etc/group and are given a name and number.

"cat /etc/group | grep 46" lists the name of group 46 which is "plugdev".

Look at the previous posts to change permissions on your partition. Read re ownership when you get the time.

---

### Post by bodhi.zazen on 2008-06-25
> **owlgorithm said:**
> My bad, I just meant my naming convention was lame. Thanks for the educational moment -- this is exactly why I love these forums.

You are most welcome, that is why we are here.

---

### Post by ilrudie on 2008-06-25
> **bodhi.zazen said:**
> 

"cat /etc/group | grep 46" lists the name of group 46 which is "plugdev".



True.  It will also show users who are members of plugdev which is specifically what I wanted him to look at.  Of course since he can write to the partition that wasn't his problem.

---

### Post by bodhi.zazen on 2008-06-25
> **ilrudie said:**
> true.  It Will Also Show Users Who Are Members Of Plugdev Which Is Specifically What I Wanted Him To Look At.  Of Course Since He Can Write To The Partition That Wasn't His Problem.
 
8)

---

### Post by chadoh on 2008-06-25
> **bodhi.zazen said:**
> 

Educational moment part 2:

Take a look at permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

 I looked at that. Insightful. Danka. > **bodhi.zazen said:**
> 

[uhelp]community/FilePermissions[/uhelp]

Look at the previous posts to change permissions on your partition. Read re ownership when you get the time.

I want to read "re: ownership", but cannot find it. Thanks very much so far.

---

### Post by bodhi.zazen on 2008-06-26
> **chadoh said:**
> I want to read &quot;re: ownership&quot;, but cannot find it. Thanks very much so far.

 ownership = owner of file, ie permissions in general.

---

### Post by chadoh on 2008-06-26
All is well! thanks so much, all.

---

