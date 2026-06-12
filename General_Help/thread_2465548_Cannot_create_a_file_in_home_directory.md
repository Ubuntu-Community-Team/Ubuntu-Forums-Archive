---
title: "Cannot create a file in /home directory"
date: 2021-08-04
forum: General Help
---

### Post by WB0HYQ on 2021-08-04
Maybe I'm doing this wrong, but I simply cannot create a file (or a directory either) in my home directory in a terminal or in Thunar (Create File and Create Directory are grayed out). I can do it everywhere else (including in an already existing directory in my home directory) except where I need it.

I've tried making myself root (SUDO -i) and trying to create it after CD-ing to my home directory, but that fails the same way: "Operation not permitted."

I've even logged on as root. Still fails.

How do I create a file in my own home directory?

Bill

---

### Post by monkeybrain20122 on 2021-08-04
Hi, I don't use xfce or thunar but it seems that you have to create a template first like for nautilus [https://forum.xfce.org/viewtopic.php?id=11873](https://forum.xfce.org/viewtopic.php?id=11873)

I don't know why they follow gnome's idiotic practice.

---

### Post by WB0HYQ on 2021-08-04
Not quite right. What you cited is an entirely different problem.

In Terminal, if I issue: LS -a, I get an entire list of every file in my home directory, including the dotted files. What I want to do is create another file in this same directory and I keep getting told I can't do it.

For example:

```

root@bill-UBU:/home/bill# cat > xxx.txt
-bash: xxx.txt: Operation not permitted
root@bill-UBU:/home/bill# touch xxx.txt
touch: setting times of 'xxx.txt': No such file or directory
root@bill-UBU:/home/bill# mkdir .text
mkdir: cannot create directory &#8216;.text&#8217;: Operation not permitted
root@bill-UBU:/home/bill# mkdir test
mkdir: cannot create directory &#8216;test&#8217;: Operation not permitted
root@bill-UBU:/home/bill# 


```

Note this is being attempted as ROOT. How much higher do I have to go than root?

Bill

---

### Post by oldfred on 2021-08-04
Your root's home is usually locked and you do not want to use it anyway.

You need to be in your user's home.

List some of /home. You do not need to show everything. Just a few examples.

[FONT=monospace][COLOR=#54ff54]**fred@z97-focal-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l[/COLOR]


[/FONT]

---

### Post by Impavidus on 2021-08-05
> **monkeybrain20122 said:**
> Hi, I don't use xfce or thunar but it seems that you have to create a template first like for nautilus [https://forum.xfce.org/viewtopic.php?id=11873](https://forum.xfce.org/viewtopic.php?id=11873)

I don't know why they follow gnome's idiotic practice.
I haven't installed any templates, but have no problem creating files on Xubuntu from the right mouse click menu. I just don't see the purpose of creating an empty file from a mouse click.

> **WB0HYQ said:**
> Not quite right. What you cited is an entirely different problem.

In Terminal, if I issue: LS -a, I get an entire list of every file in my home directory, including the dotted files. What I want to do is create another file in this same directory and I keep getting told I can't do it.

For example:

```

root@bill-UBU:/home/bill# cat > xxx.txt
-bash: xxx.txt: Operation not permitted
root@bill-UBU:/home/bill# touch xxx.txt
touch: setting times of 'xxx.txt': No such file or directory
root@bill-UBU:/home/bill# mkdir .text
mkdir: cannot create directory ‘.text’: Operation not permitted
root@bill-UBU:/home/bill# mkdir test
mkdir: cannot create directory ‘test’: Operation not permitted
root@bill-UBU:/home/bill# 


```

Note this is being attempted as ROOT. How much higher do I have to go than root?

Bill
I assume mkdir just calls the mkdir() system call and reports the error it receives from there. You can look up the error string with **errno -l**, telling us this is EPERM. According to the manual (**man -s2 mkdir**), this means ```
       EPERM  The filesystem containing pathname does not support the creation
              of directories.

```
So not a normal permissions issue. Doing this as the root user would have helped against "Permission denied":```
       EACCES The  parent  directory  does  not  allow write permission to the
              process, or one of the directories in  pathname  did  not  allow
              search permission.  (See also path_resolution(7).)
```
It would be great if I knew the solution, but I think this is a lead. Anything peculiar about the filesystem? Reached some sort of filesystem limit?

---

### Post by The Cog on 2021-08-05
I wonder if it's mounted in a funny way. Can you post the output from this comand so we can figure out how it's mounted?
```
mount | awk '!/snap|sys/' | column -t
```

---

### Post by Tadaen_Sylvermane on 2021-08-05
Indeed. Read only sounds like the issue here. You probably didn't do that intentionally. May mean disk is going

---

### Post by WB0HYQ on 2021-08-05
> **oldfred said:**
> Your root's home is usually locked and you do not want to use it anyway.

You need to be in your user's home.

List some of /home. You do not need to show everything. Just a few examples.

[FONT=monospace][COLOR=#54ff54]**fred@z97-focal-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l[/COLOR]

[/FONT]

I am positive I am in /home/bill (even signed on as root) as I did  CD and then an LS to make sure I was where I wanted to be.

Bill

---

### Post by WB0HYQ on 2021-08-05
> **Impavidus said:**
> I haven't installed any templates, but have no problem creating files on Xubuntu from the right mouse click menu. I just don't see the purpose of creating an empty file from a mouse click.


I assume mkdir just calls the mkdir() system call and reports the error it receives from there. You can look up the error string with **errno -l**, telling us this is EPERM. According to the manual (**man -s2 mkdir**), this means ```
       EPERM  The filesystem containing pathname does not support the creation
              of directories.

```
So not a normal permissions issue. Doing this as the root user would have helped against "Permission denied":```
       EACCES The  parent  directory  does  not  allow write permission to the
              process, or one of the directories in  pathname  did  not  allow
              search permission.  (See also path_resolution(7).)
```
It would be great if I knew the solution, but I think this is a lead. Anything peculiar about the filesystem? Reached some sort of filesystem limit?

Nothing peculiar that I can see. I made sure I was first set up as root, then did a CD to /home/bill (my actual user directory) and tried to create the file or directory there. No dice.

Bill

---

### Post by WB0HYQ on 2021-08-05
> **The Cog said:**
> I wonder if it's mounted in a funny way. Can you post the output from this comand so we can figure out how it's mounted?
```
mount | awk '!/snap|sys/' | column -t
```

Here's the result:

```

bill@bill-UBU:~$ mount | awk '!/snap|sys/' | column -t
proc        on  /proc                type  proc             (rw,nosuid,nodev,noexec,relatime)
udev        on  /dev                 type  devtmpfs         (rw,nosuid,noexec,relatime,size=8134492k,nr_inodes=2033623,mode=755)
devpts      on  /dev/pts             type  devpts           (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs       on  /run                 type  tmpfs            (rw,nosuid,nodev,noexec,relatime,size=1639368k,mode=755)
/dev/sdb1   on  /                    type  ext4             (rw,relatime,errors=remount-ro)
tmpfs       on  /dev/shm             type  tmpfs            (rw,nosuid,nodev)
tmpfs       on  /run/lock            type  tmpfs            (rw,nosuid,nodev,noexec,relatime,size=5120k)
mqueue      on  /dev/mqueue          type  mqueue           (rw,nosuid,nodev,noexec,relatime)
hugetlbfs   on  /dev/hugepages       type  hugetlbfs        (rw,relatime,pagesize=2M)
tmpfs       on  /run/user/1000       type  tmpfs            (rw,nosuid,nodev,relatime,size=1639364k,mode=700,uid=1000,gid=1000)
gvfsd-fuse  on  /run/user/1000/gvfs  type  fuse.gvfsd-fuse  (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/fuse   on  /run/user/1000/doc   type  fuse             (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda1   on  /media/bill/WIN764   type  fuseblk          (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,uhelper=udisks2)
/dev/sde1   on  /media/bill/My Book  type  fuseblk          (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc    on  /media/bill/Big_U      type  fuseblk          (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
bill@bill-UBU:~$ 


```

Nothing strange I can see, but I'm not an expert.

Bill

---

### Post by TheFu on 2021-08-05
Sometimes a disk with corruption, the file system gets mounted read-only. That's my best guess for this issue.

The best fix, if the issue is just logical, not physical, would be to boot off a Try Ubuntu flash drive and run fsck on all the file system in the system manually.

What does 
```
ls -dl /home/bill 
```
show?
Should be ... 
```
drwxr-x--- 180 bill bill ..... 
```

---

### Post by WB0HYQ on 2021-08-05
This is what I get:

drwxrwxrwx+ 110 bill sambashare 12288 Jul  3 21:25 /home/bill

I can create files and directories everywhere below /home/bill, but not in bill, just the subdirectories so it isn't a read-only problem that I can see.

Bill

---

### Post by TheFu on 2021-08-05
drwxrwxrwx[COLOR="#FF0000"]+[/COLOR]

That's the issue.  Check the ACLs. See if there is anything bad there.  **getfacl /home/bill**
And are you 100% certain it isn't a read-only mount?

sambashare as the group is a problem too, BTW.

---

### Post by WB0HYQ on 2021-08-05
Hmm. I see the problem as well. Here's what I get:

```

bill@bill-UBU:~$ getfacl /home/bill
getfacl: Removing leading '/' from absolute path names
# file: home/bill
# owner: bill
# group: sambashare                  <----- This is odd. Haven't a clue how this happened.
user::rwx
user:bill:rwx
group::r-x                                  <----- HERE
group:bill:r-x                              <----- HERE
mask::rwx
other::rwx
default:user::rwx
default:user:bill:rwx
default:group::rwx
default:group:bill:rwx
default:mask::rwx
default:other::rwx


```

I can also see, if I right-click /bill in Thunar, Sambashare is the owner, but the other two drop-downs show read & write. I agree. Something smells fishy here.

Will a change of ownership help here? As it stands now, I can access my home directory (/bill) from my downstairs server (Windows Server 2012 R3) and my Windows 10 machine. I will have to go back and re-share them I guess if this is changed.

Bill

---

### Post by TheFu on 2021-08-05
Samba is a different skillset.  I use it to access 1 HOME directory, but don't use ACLs nor is any of my directories using the sambashare group. I avoid samba, though it has been used here since the 1990s.

---

### Post by WB0HYQ on 2021-08-05
Samba was the only method I could find that let me share certain directories on my Linux boxes/laptops with Windows. If there is an alternative, I could certainly try it. I still haven't found a method for me to access any directories on my Windows 10 or Server boxes from Linux as I am always told "No Network Found" when I try.

Bill

---

### Post by dragonfly41 on 2021-08-05
My simplistic approach for sharing small common files between Windows 10 and Ubuntu 20.04
is to create a partition, format NTFS, and mount it either from within Windows 10 or Ubuntu 20.04. 
This way I can launch any shared file in the associated crossplatform application. For example I share CherryTree files.
Another approach is to use DropBox nut that requires internet connection.

---

### Post by TheFu on 2021-08-05
http:// s p r u n g e.us/Vued0l

Sorry for the link. The forums aren't excepting my attempts to trick it into allowing those steps.

Fix 1 issue at a time. Samba would be fixed after the write problem is handled.

---

### Post by WB0HYQ on 2021-08-05
> **TheFu said:**
> http:// s p r u n g e.us/Vued0l

Sorry for the link. The forums aren't excepting my attempts to trick it into allowing those steps.

Fix 1 issue at a time. Samba would be fixed after the write problem is handled.

The website is unknown to any server (after removing the spaces). I get "Do you want to buy this domain?" Are you sure this URL is legit and correctly spelled. I note is also isn't HTTPS.

Bill

---

### Post by TheFu on 2021-08-05
It is a pastebin clone.  Use **lynx** as your browser - that's a text-only, no javascript, browser. Very safe for what it does.

I just tested it. Working fine from here.

It is a post for the world to see. Whether https is good for those is debatable. Https is far from perfect.

---

### Post by WB0HYQ on 2021-08-05
Everything else set aside, why can't I, as ROOT, do whatever I want to my system. I thought this was the point of being ROOT. Is there a user above ROOT?

I also created an entire new user and have the exact same problems as I do with my own login.

Bill

---

### Post by TheFu on 2021-08-05
Read-only file systems break what root can do.  

Also, there are some other options which can be set (like immutable flags), to make a file (directories are just files too, BTW) read-only.  root can change those properties, but you have to know to do it.

Perhaps I missed the proof that the file system wasn't read-only mounted?

---

### Post by WB0HYQ on 2021-08-05
I thought that's what all the "rwxrwxrwx"s were about in the listing for /home/bill directory. Doesn't that mean read/write/execute? I am really confused now. So  what you're saying is that even ROOT can't do everything it wants to. Even as root, I was unable to CHOWN from 'sambashare' to anything else. kept getting "can't do that".

Just checked my three Linux laptops. None of them will allow creating a file or directory in the Home directory. maybe it's a new rule or something.

Bill

---

### Post by TheFu on 2021-08-05
> **WB0HYQ said:**
> I thought that's what all the "rwxrwxrwx"s were about in the listing for /home/bill directory. Doesn't that mean read/write/execute?

Bill

Nope.  It is in the mount properties, not the permissions.
Which file system is /home in?  Is that mounted read-write or read-only RIGHT now?  
Corruption can force a read-only mount to protect data.  
Has an fsck been run on that file system to ensure it isn't corrupted?

---

### Post by WB0HYQ on 2021-08-05
Okay. Here's the output of 'findmnt':

```

bill@bill-UBU:~$ findmnt /dev/sda1
TARGET             SOURCE    FSTYPE  OPTIONS
/media/bill/WIN764 /dev/sda1 fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id         <------ this is my Win 7 partition (separate drive)

bill@bill-UBU:~$ findmnt /dev/sdb1
TARGET SOURCE    FSTYPE OPTIONS
/      /dev/sdb1 ext4   rw,relatime,errors=remount-ro           <------ This is my Linux drive


```

And this is the whole enchilada, using 'df':

```

bill@bill-UBU:~$ df -T
Filesystem     Type      1K-blocks      Used  Available Use% Mounted on
udev           devtmpfs    8134492         0    8134492   0% /dev
tmpfs          tmpfs       1639368      3940    1635428   1% /run
/dev/sdb1      ext4      240231392  45019700  182985520  20% /                  <----- presumably, my Linux install on a separate SATA internal drive
tmpfs          tmpfs       8196828         0    8196828   0% /dev/shm
tmpfs          tmpfs          5120         4       5116   1% /run/lock
tmpfs          tmpfs       8196828         0    8196828   0% /sys/fs/cgroup
/dev/loop3     squashfs      56832     56832          0 100% /snap/core18/2066
/dev/loop0     squashfs     101760    101760          0 100% /snap/core/11316
/dev/loop2     squashfs     101888    101888          0 100% /snap/core/11420
/dev/loop1     squashfs      56832     56832          0 100% /snap/core18/2074
/dev/loop6     squashfs      66688     66688          0 100% /snap/gtk-common-themes/1515
/dev/loop4     squashfs     168832    168832          0 100% /snap/gnome-3-28-1804/161
/dev/loop5     squashfs     166784    166784          0 100% /snap/gnome-3-28-1804/145
/dev/loop7     squashfs      86912     86912          0 100% /snap/shotcut/282
/dev/loop8     squashfs      81920     81920          0 100% /snap/shotcut/347
tmpfs          tmpfs       1639364        32    1639332   1% /run/user/1000
/dev/sda1      fuseblk   976758784 205446995  771311789  22% /media/bill/WIN764
/dev/sde1      fuseblk   976074748 315828524  660246224  33% /media/bill/My Book      <----- External USB drive
/dev/sdc       fuseblk  1953514580   1484672 1952029908   1% /media/bill/Big_U            <----- internal SATA drive
tmpfs          tmpfs       1639364        84    1639280   1% /run/user/1001
/dev/sdd1      fuseblk    30240831   5394873   24845958  18% /media/bill/32G(M)           <----- USB thumb drive


```

Bill

---

### Post by TheFu on 2021-08-05
Ok, so 
```
/dev/sdb1 ext4   rw,relatime,errors=remount-ro
```
says it is mounted read-write.
```
/dev/sdb1      ext4      240231392  45019700  182985520  20% /
```
says that it isn't out of space.

```
$ df -i |grep sdb1
```
would check if inodes are available. Please run it

What does '**id**' return?
Did you remove all the ACLs yet?  **Make the permissions**  bill:bill 660 on /home/bill.  Be certain there's no + on the permissions. If there are, the ACLs need to be cleared.

Then run **touch /home/bill/foo**

**[COLOR="#FF0000"]Please show all commands and output.[/COLOR]**

BTW, I've never heard of findmnt.  I usually just use **df -h .** while I'm in the directory. As usual, more than 1 way to get an answer.  I almost always use **df -Th**, since it shows the most useful information in an easy to read way.

Did you happen to run the **fsck** yet?

---

### Post by WB0HYQ on 2021-08-05
fsck keeps complaining the the system is mounted and aborts.

'df' command reports:

```

bill@bill-UBU:~$ df -i |grep sdb1
/dev/sdb1        15269888 523066   14746822    4% /


```

'id' returns:

```

bill@bill-UBU:~$ id
uid=1000(bill) gid=1000(bill) groups=1000(bill),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),104(fuse),107(scanner),109(lpadmin),113(netdev),124(sambashare),130(powerdev),144(wireshark)


```

---

### Post by TheFu on 2021-08-05
Well, you need to run the fsck when the file system isn't mounted. Use a Try Ubuntu flash drive or the Recovery Mode boot option from grub.

inodes are fine.
Nothing too odd in the id output either.

The other stuff coming?

---

### Post by WB0HYQ on 2021-08-05
Other stuff? What did I miss?

Bill

---

### Post by TheFu on 2021-08-05
> **WB0HYQ said:**
> Other stuff? What did I miss?

26 post above specifies a few things.

---

### Post by WB0HYQ on 2021-08-05
Since this whole thing started because VeraCrypt complained it couldn't write a lock file in my home directory, I've decided to uninstall Veracrypt as being untrustworthy and VERY cumbersome to use. It also began mounting my encrypted directory as read-only which really killed the deal. I needed it to be R/W. Doesn't do me much good if I can't write into it or alter files.

All this obviates me from having to solve this particular dilemma right now. I am a Linux user, and have been since Ubuntu 12.01, but I don't deep-dive into the system all that much. I tend to use GUIs instead of command lines. it worked for DOS, but not for me in Linux.

I am not sure exactly what an ACL is, however I've found a forum thread on another site that describes how to remove the "+" from the file attributes. I'm going to leave everything as it is right now. I really appreciate all the time and effort you've put into this problem, Fu. Thank you a lot.

I'm going to mark this as 'solved' even though it really isn't. Is that a good idea or not?

Bill

---

### Post by oldfred on 2021-08-05
Is sdc not partitioned?
/dev/sdc       fuseblk  1953514580   1484672 1952029908   1% /media/bill/Big_U

Systems often have issues with drives not following standard partitioning.

---

### Post by WB0HYQ on 2021-08-05
Big_U is a large (1Tb) drive I added when I still booted up into Win 7. I didn't change anything and now it mounts as sdc. I can use it just fine, R/W in any directory.

Bill

---

### Post by TheFu on 2021-08-05
> **WB0HYQ said:**
> Since this whole thing started because VeraCrypt complained it couldn't write a lock file in my home directory, I've decided to uninstall Veracrypt as being untrustworthy and VERY cumbersome to use. l

We are 31 posts into this and this is the first mention of Veracrypt!!! Way to bury perhaps the most important information.

Good day and good luck.

---

### Post by WB0HYQ on 2021-08-05
As I mentioned quite a few posts back, this is happening on every one of my Linux installs on four different computers. It has nothing to do with VeraCrypt, which in only installed on ONE of my computers. I'm sorry if it offended you.

Bill

---

