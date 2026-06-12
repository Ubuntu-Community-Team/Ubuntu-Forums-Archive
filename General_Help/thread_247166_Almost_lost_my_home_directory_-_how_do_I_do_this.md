---
title: "Almost lost my /home directory - how do I do this?"
date: 2006-08-30
forum: General Help
---

### Post by Slychilde on 2006-08-30
On my desktop PC, I have 2 hard drives, and I wanted to make a little more room to store my music on linux finally, so I could use easytag/amarok to their full extent (not gonna risk writing to ntfs and corrupt data).  So, I resized my /dev/hdb and made a 25GB ext3 partition, booted back into ubuntu and formated it with the intention of mounting it as /home.

I'm sure many can see where this is going.  I mounted it as home, and poof, all my stuff was gone (oops!).  Or, so I thought.  I did logout, login to a recovery terminal, made my /home/acct, and logged back into gnome.  But, as you know when I restarted I got all my stuff back because I didn't edit /etc/fstab, luckily.  However, I am proud I got my gui back before restarting; it really showed me how tough this os can really be.  That would have caused a reinstall on windows.

So, what is the best way of:

1.)Backing up my current home directory, hidden files and all. will cp /home/myDir /some/other/dir get it all?
2.)Editing my /etc/fstab to mount /dev/hdb2 ext3 as /home - exact syntax is way beyond me.
3.) copy it all back, again will cp /some/dir /home/myDir pick up the hidden files or do I need to add a flag?

Thank you for any help.

---

### Post by VirtuAlex on 2006-08-30
add -a option to cp and you should be fine

---

### Post by VirtuAlex on 2006-08-30
by the way, you have to mount new partition at some other mountpoint first, say at /mnt, then copy everything from /home to /mnt, and after you done with all that you edit fstab

---

### Post by bluenova on 2006-08-30
What I do is:

```

cd <yourhome dir>
cp -R .* /the/new/dir

```

That copies all files including hidden files and sub files/folders

---

### Post by VirtuAlex on 2006-08-30
-R is not enough, you may want to preserve links with -d and attributes with -p
-a takes care of all of above

---

### Post by Slychilde on 2006-08-30
OK, I did it thanks to your guys' help!  What I did in case anyone else needs to know in the future:

-First, mount new partition.
-Copy your home directory, hidden files and preserve everything; also back-up somewhere else, just in case.
-edit /etc/fstab. I just copy/pasted the mounted root one and changed accordingly.

```
sudo mount /dev/hdb2 /mnt
cd
cp -a slychilde /mnt/slychilde
cp -a slychilde /lost+found/slychilde
sudo gedit /etc/fstab

```

copied: 
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1

and changed it to:
/dev/hdb2       /home           ext3    defaults,errors=remount-ro 0       1

I was reading the wiki 'mount' page and it mentioned the flags --move and --bind, would that have done the same thing, but required less work, or does that essentially equal a symbolic link?

---

### Post by VirtuAlex on 2006-08-30
-p an -r options are redundant
as I said -a takes care of it all
as of --move I can not be sure
will play with it when have time and occasion

---

### Post by Ramses de Norre on 2006-08-30
This seems the best way to me: (the new home partition is mounted as /mnt/newhome/)
```
cd /home/
find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
```

---

### Post by Slychilde on 2006-08-31
Aye, I posted it right after you posted yours and went to bed - I edited it accordingly.  Thanks again for your help. :)

---

### Post by VirtuAlex on 2006-08-31
> **Ramses de Norre said:**
> This seems the best way to me: (the new home partition is mounted as /mnt/newhome/)
```
cd /home/
find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
```
Would you explain why is this animal better than simple cp? :confused:

---

### Post by Ramses de Norre on 2006-08-31
I read it somewhere :D 
> Now, Copy files over:
Since the “/home” directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide:
$cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
[Link]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by VirtuAlex on 2006-08-31
> **Ramses de Norre said:**
> [Link]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")
Well, that is interesting, thanks for the link. But they still vague on what exactly cp will miss. I'm not sure, but it seems that problem can arise with hard links across different filesystems. However, if you do not know what hard links are it is a good chance you do not have any, and if you do, in this particular case cp should process them just fine, or give you error message. By the way, as someone mentioned in comments, there is already one missed parameter in the command: --preserve-modification-time
So I still would recommend to use cp unless you are positive that you need cpio.

---

### Post by Ramses de Norre on 2006-08-31
> **VirtuAlex said:**
> [...]it seems that problem can arise with hard links across different filesystems. [...]
As far as I know you can't make hard links across different file systems.. A hard link is just an inode pointing to the same disc content as an allready existing inode, and that is impossible across different file systems (if I understand it correctly..).

---

### Post by VirtuAlex on 2006-09-01
I did not mean making them across filesystems. I mean copying them across filesystems.

---

### Post by Ramses de Norre on 2006-09-01
Ow sorry, I misunderstood you. I'm not so sure nomore about which method is really the best though =)

---

### Post by VirtuAlex on 2006-09-01
Neither am I ;)

---

### Post by UniRecovery on 2006-09-01
The safest way is to get back-up software such as Acronis which enables you to create an exact image of your drive, which can booted from incase your drive is down or your data is deleted. Take this advice from a data recovery "technician";)  please see our web on [http://www.unirecovery.co.uk](http://www.unirecovery.co.uk)

---

### Post by UniRecovery on 2006-09-01
I would also back up the image of the data on DVDs, which may be around 2Gb of compressed image for 160Gb HDD , never on tape.

---

