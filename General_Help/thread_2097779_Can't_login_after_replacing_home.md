---
title: "Can't login after replacing /home"
date: 2012-12-24
forum: General Help
---

### Post by PureTryOut on 2012-12-24
Hey all, i'm very new to Ubuntu, Xubuntu and Linux in general so I would like some help here :)

I've just changed the /home directory of my main account to a different partition via the Users & Groups settings.

After this was done I tried to login but was not able to.
When typing the correct password and pressing enter, it comes with a black screen for a second and then brings me back to the login screen. I am able to login via text mode though.

I've searched on Google for a bit and tried several methods, but none of them worked.

Thanks in advance.

---

### Post by steeldriver on 2012-12-24
Hello and welcome

Can you outline exactly what steps you did to change /home?

It sounds like a problem with write permissions (the X server needs to be able to write an Xauthority file and possibly other stuff to your home dir in order to start your GUI session)

Can you log in at one of the non-graphical virtual terminals (Ctrl-Alt-F1 etc.)? if so we can look at / fix things from there - if not you will need to boot to the Recovery Console

EDIT: you can check ownership / permissions from your console using:

```
$ ls -ld ~

$ ls -l ~/.{ICE,X}authority
```

---

### Post by GameX2 on 2012-12-24
> **steeldriver said:**
> Hello and welcome

Can you outline exactly what steps you did to change /home?

It sounds like a problem with write permissions (the X server needs to be able to write an Xauthority file and possibly other stuff to your home dir in order to start your GUI session)

Can you log in at one of the non-graphical virtual terminals (Ctrl-Alt-F1 etc.)? if so we can look at / fix things from there - if not you will need to boot to the Recovery Console

I've encoutered the issue a few days ago; I deleted the /home of an older Ubuntu installation, I was curious about how Ubuntu would react.  Black screen after login, same problem.  I was not able to login as Recovery Console, but I haven't tested a virtual terminal - I guess that would work.

---

### Post by PureTryOut on 2012-12-24
Thank you for the quick answer.

So to change my home directory I made a new "admin" account via Settings Manager -> Users & Groups, because I was not able to change the home directory via my account itself.
Then I logged in into the admin account (the one i'm using now), went to Settings Manager -> Users & Groups -> Main Account Advanced Settings -> Advanced, and changed the home directory.
It asked me to delete the old home directory, I answered yes and then it started replacing all of my files to the new home directory.

After this was done I tried to login into the account, but after a blackscreen for 2 seconds, it directed me back to the login screen. No matter how many times I try to login, it does not work.
Like I said I am able to login via text mode (Ctrl-Alt-F1).

---

### Post by PureTryOut on 2012-12-24
I've tried using your commands
```
$ ls -ld ~
```
Gave me this output:
drwxr-xr-r 24 root root 4096 Dec 23 19:56

```
$ ls -l ~/.{ICE,X}authority
```
Gave me this output:
ls: cannot acces //.ICEXauthority: No such file or directory
ls: cannot acces //.XXauthority: No such file or directory

---

### Post by PureTryOut on 2012-12-24
I've just checked, and according to the settings panel, the home directory is back at /home/username.
This is weird because it should have changed to /media/myname/Data/home/username
(Data) is a different partition on the same harddisk.
My files are on the right location though...

---

### Post by Lars Noodén on 2012-12-24
> **PureTryOut said:**
> I've tried using your commands
```
$ ls -ld ~
```
Gave me this output:
drwxr-xr-r 24 root root 4096 Dec 23 19:56

```
$ ls -l ~/.{ICE,X}authority
```
Gave me this output:
ls: cannot acces //.ICEXauthority: No such file or directory
ls: cannot acces //.XXauthority: No such file or directory

It looks like need to set the permissions for the new directory, as you show above it is owned by root.

```

sudo chown -R puretryout:puretryout /home/puretryout

```

---

### Post by PureTryOut on 2012-12-24
It says "no such file or directory".
I've tried "/home/username" and "/media/username/Data/home/username"
Both give the same output.

---

### Post by Lars Noodén on 2012-12-24
Ok.  That's an even more fundamental problem than permissions.  Where is the system looking for your home?

```

grep puretryout /etc/passwd

```

Edit: Or this

```

 awk -F':' '$1=="puretryout" {print $6}' /etc/passwd

```

---

### Post by PureTryOut on 2012-12-24
```
grep puretryout /etc/passwd
```
Gives me:
bart:x:1000:1000:firstname surname,,,:/home/username:/bin/bash

EDIT: That smile icon needs to be : x : but without the spaces


```
 awk -F':' '$1=="puretryout" {print $6}' /etc/passwd
```
Gives me:
/home/username

---

### Post by Lars Noodén on 2012-12-24
Ok.  So the system is looking for /home/username, but it does not seem to exist.  When you tried to point the account at a new directory, what was that new directory?

---

### Post by PureTryOut on 2012-12-24
I shall tell my username now (bart), so it's easier :)

The directory I set it to is:
/media/bart/Data/home/

---

### Post by Lars Noodén on 2012-12-24
> **PureTryOut said:**
> I shall tell my username now (bart), so it's easier :)

The directory I set it to is:
/media/bart/Data/home/

According to the output from #10 above, the change is not there.  Maybe you changed some other user by accident or did not complete the change.  You can make the change using [usermod](http://manpages.ubuntu.com/manpages/precise/en/man8/usermod.8.html).

```

sudo usermod -d /media/bart/Data/home/ bart

```

That also assumes that the permissions and ownerships have been set for your account for that directory.

---

### Post by oldfred on 2012-12-24
Ubuntu will auto create a new /home account if you do not mount a different location with fstab. Are you trying to move /home to another partition?

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Note above instructions have you editing fstab with new location of /home that was copied to another partition. And it needs to be the top level of the partition. 
Or of looking from liveCD it should show in the partition as /bart. But when mounted in fstab it will be mounted in /home so the full path is /home/bart.

---

### Post by PureTryOut on 2012-12-24
> **oldfred said:**
> Ubuntu will auto create a new /home account if you do not mount a different location with fstab. Are you trying to move /home to another partition?

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
I am indeed trying to move the /home to another partition. I'm trying to move it to my data partition so I can also use the same files in Windows (i'm dual booting).

But while searching I have seen that tutorial before, but when I come to this part:
[IMG]http://i.imgur.com/RDBid.png[/IMG]
All of the commands just do nothing. Even when trying to open the text editor.

[IMG]http://i.imgur.com/Uwm4Z.png[/IMG]



Also
```
sudo usermod -d /media/bart/Data/home/ bart
```
seems to do nothing.
I've tried
```
sudo usermod -d /media/bart/Data/home/ -m
```
before but again, it did nothing.

---

### Post by Lars Noodén on 2012-12-24
> **PureTryOut said:**
> Also
```
sudo usermod -d /media/bart/Data/home/ bart
```
seems to do nothing.


If it works, then it will say nothing.  But if you look in /etc/passwd again it should show the new directory.  If the directory exists and the permissions are right you should be able to log in.

---

### Post by PureTryOut on 2012-12-24
> **Lars Noodén said:**
> If it works, then it will say nothing.  But if you look in /etc/passwd again it should show the new directory.  If the directory exists and the permissions are right you should be able to log in.
Although it does show the new directory, i'm still not able to log in. Still the black screen, and then redirecting me to the log in screen again.

---

### Post by Lars Noodén on 2012-12-24
And you've got the right permissions set for the new directory?

```

sudo chown -R bart:bart /media/bart/Data/home/

```

Edit: wait, that path looks truncated, shouldn't it be /media/bart/Data/home/bart in full?

---

### Post by PureTryOut on 2012-12-24
> **Lars Noodén said:**
> 
```

sudo chown -R bart:bart /media/bart/Data/home/

```

I believe not, seeing this is the output:
Cannot access: /media/bart/Data/home/: No such file or directory

---

### Post by Lars Noodén on 2012-12-24
> **PureTryOut said:**
> I believe not, seeing this is the output:
Cannot access: /media/bart/Data/home/: No such file or directory

Ok.  That's why you can't log in.  That directory does not exist.  Are you adding a permanent disk or is it a dettachable USB disk?

---

### Post by PureTryOut on 2012-12-24
On a permanent disk, just a different partition.

---

### Post by Lars Noodén on 2012-12-24
Assuming your partitions are EXT4, what is the output of the following?

```

mount -t ext4

```

---

### Post by PureTryOut on 2012-12-24
That did nothing. But my partitions are not EXT4. Most of them are different.
[IMG]http://i.imgur.com/cMn45.png[/IMG]

Because I am new in this stuff I do not really know what most of it means, but my Data partition (the one I want to have my home direction on) is NTFS.

sda1 = Recovery
sda2 = Windows 7
sda3 = Xubuntu 12.10
sda4 = extended, containing Data and swap
sda5 = Data
sda6 = swap

EDIT: Now i'm thinking of it, that is probably the problem. Is it possible the /home folder can not be located on a NTFS partition?
If so what does it have to be? And is there a format I can use which Windows also can use.

---

### Post by Lars Noodén on 2012-12-24
NTFS is not really suitable for home directories.  One of the many problems is that it can't handle normal permissions.  There was some community documentation on using it, but I can't find it again right now.  The work-around by setting UID, but it is only good for a single user per partition, though.  If you can you are much better off using a regular EXT4 or EXT3 partition.

---

### Post by oldfred on 2012-12-24
Windows formats do not support Linux permissions & ownership. So /home has to be Linux formated, usually now ext4.

But you can keep /home inside your / (root) and have data in other data partitions. I have only 2GB for /home inside my / and it is only that large since I use Windows Picasa in .wine and that is more difficult to move to a data partition. 

I mount my data partitions and then link folders from the data partitions back into my /home. At the top level of my data partitin I have Documents, Music, Video etc that are all the defaults plus some others as folders. Then I remove the folders (make sure they are empty) in /home and add links to data partitions.

I have both Linux data partition and a NTFS data partition. My NTFS was from when dual booting with XP, but since I now do not use XP all new data goes into my ext4 data partition. But I have not yet moved current data from NTFS.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

    
       Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by PureTryOut on 2012-12-24
But is Windows able to use that? With both OS I want to be able to access the files. So I need a format which both Windows and Linux can use for My Documents and home folder. Is there a format which enables this?
Or is this impossible and do I just need to live with the home folder being in my Linux partition?

EDIT: Thanks oldfred for your reply, I will try that then.

---

### Post by PureTryOut on 2012-12-25
I don't know what I did, but I messed up. Now I was not able to log in into any account. I decided to just do a clean install seeing I had not that much programs to lose.

Now I have a clean Xubuntu 12.10 installation, with 1 root account.
I was not able to figure out of the links you gave how to link my home to a different location.
Can someone give me a step by step tutorial?

---

### Post by oldfred on 2012-12-25
Have you mounted you data partition with fstab? Post your fstab.

       sudo cat /etc/fstab

---

