---
title: "No Boot and a Bunch of Strange Error Text on Screen"
date: 2007-08-16
forum: General Help
---

### Post by flowingfire on 2007-08-16
Please help me fix my computer.  Every time I turn on my computer, it doesn't take me to a login screen or boot.  What it does is stop the booting process on a screen with text and what appear to be errors.  I have discovered, however, that pressing ctrl-alt-del when on that screen lets it complete booting as if nothing happened.  Then I get a desktop and everything is right as rain.

But I always have to go through that error-filled screen first: (see a picture of the screen at [http://flowingfire.googlepages.com/ubuntuerror.jpg](http://flowingfire.googlepages.com/ubuntuerror.jpg))

Here is the text on the screen that blocks up my boot:
```
filesystem.  If the device is valid and it really contains an ext2 filesystem
(and not swap or ufs or something else), then superblock is corrupt, and you might
try running e2fsck with an alternate superblock:
	e2fsck -b 8193 <device>

fsck died with exit status 8
                                                           [fail]
*File system check failed.
a log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
*A maintenance shell will now be started.  
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: The: command not found
The program 'apt-get' is currently not installed.  You can install it by typing:
apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
bash: The: command not found
The program 'apt-get' is currently not installed.  You can install it by typing: apt-get
install apt
bash: apt-get: command not found
root@porch-computer-linux:~#
```


Because the screen says it saved a log in /var/log/fsck/checkfs, here it is:

```
Log of fsck -C -R -A -a 
Thu Aug 16 01:41:28 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/sda3
/dev/sda3: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Thu Aug 16 01:41:28 2007
----------------
```

I'm not sure what's wrong or what to do if anything...  Please not that my knowledge of this is somewhat limited in all regards.

---

### Post by jamvegan on 2007-08-16
I'm not particularly familiar with this problem, but have you tried running:

e2fsck -b 8193 /dev/sda3

at the "root@porch-computer-linux:~#" prompt that you get when booting stops?  That seems to be what the error message is recommending that you do.  More generally, the problem has something to do with the third partition of your first (or only) hard drive, if that rings any bells for you?

---

### Post by flowingfire on 2007-08-16
I apologize for the redundancy of my posts...  (I posted another one just like this one.)

With consideration to SDA3, I think I might know what went wrong.  I just don't know how to fix it.  

I used to have another Ubuntu partition on my SDA hard drive, and SDA 3 was the swap partition for that drive.

Now, that swap partition doesn't exist anymore, and it's the home of Windows.  I think Ubuntu automatically utilizes ANY swap partitions on your computer, so on installation it used both the one I assigned to it on its own drive, and it also used the one of the other Linux partition.

Now it chokes on boot trying to access the second swap I never wanted it to use anyway.

How do I fix this?

---

### Post by confused57 on 2007-08-16
> **flowingfire said:**
> I apologize for the redundancy of my posts...  (I posted another one just like this one.)

With consideration to SDA3, I think I might know what went wrong.  I just don't know how to fix it.  

I used to have another Ubuntu partition on my SDA hard drive, and SDA 3 was the swap partition for that drive.

Now, that swap partition doesn't exist anymore, and it's the home of Windows.  I think Ubuntu automatically utilizes ANY swap partitions on your computer, so on installation it used both the one I assigned to it on its own drive, and it also used the one of the other Linux partition.

Now it chokes on boot trying to access the second swap I never wanted it to use anyway.

How do I fix this?
You probably need to delete or comment out(place a # in front of) your /dev/sda3 entry in your fstab...open a terminal(Applications---Accessories---Terminal):
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

Make the changes, then quit & save.

---

### Post by flowingfire on 2007-08-17
Ahh... Thank you, Confused.  Problem solved.  No boo up problem now.  Nice clean boot. :)

---

### Post by kiepmad on 2007-08-21
Thanks, this helped me too.

I installed Windows on a spare harddrive, which was before mounted by ubuntu and then gave out the same problem.

commenting that entry out in fstab solved the problem.

---

