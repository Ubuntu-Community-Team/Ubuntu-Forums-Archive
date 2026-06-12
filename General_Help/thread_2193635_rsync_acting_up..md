---
title: "rsync acting up."
date: 2013-12-13
forum: General Help
---

### Post by MibunoOokami on 2013-12-13
I use a script called incbackup which utilises rsync to back up my computers but am getting an error message when trying to back up the netbook which has mini Ubuntu on it. I had the same problem when trying to back up the same netbook when Lubuntu was installed on it so I'm thinking it's got something to do with the light weight versions. It has nothing to do with the storage device I'm using because it still works fine backing up my main computer and my wife's, and to be on the safe side I even tried using a different device. Rsync is the latest version so I'm at a loss as to why incbackup won't work. 
Time isn't one of my allies at the moment so if anyone can provide a quick fix solution that would be great because it's a lot faster than doing drag and drop, though I wish to keep using incbackup rather than trying a different one. Thanks.

```
   ~$ incbackup  
 sending incremental file list  
 rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)  
 rsync: mkdir "/media/BUFFALO/hpbackup" failed: No such file or directory (2)  
 rsync error: error in file IO (code 11) at main.c(605) [Receiver=3.0.9]  
 rsync: connection unexpectedly closed (9 bytes received so far) [sender]  
 rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9]  


```

---

### Post by nerdtron on 2013-12-14
Have you installed openssh-server (and possibly rsync) on both computers? I think openssh-client is the only package installed by default on desktop version. You need the server package to be able to ssh and rsync between computers.

---

### Post by MibunoOokami on 2013-12-15
> **nerdtron said:**
> Have you installed openssh-server (and possibly rsync) on both computers? I think openssh-client is the only package installed by default on desktop version. You need the server package to be able to ssh and rsync between computers.

I'm not sure what openssh-server is but it would seem it's not related to backing up because I tried sudo apt-get install openssh-server on both computers and neither have it installed.

EDIT: Sorry just read your post again, I'm trying to back up one of my computers not sync between them.

---

### Post by SeijiSensei on 2013-12-15
At a minimum, I believe the target computer needs openssh-server so rsync can connect to it.

The reported error is "mkdir "/media/BUFFALO/hpbackup" failed: No such file or directory (2)".  Does the target have a "/media/BUFFALO" directory?  If you create it, does it cure the problem?

---

### Post by MibunoOokami on 2013-12-16
> **SeijiSensei said:**
> At a minimum, I believe the target computer needs openssh-server so rsync can connect to it.

The reported error is "mkdir "/media/BUFFALO/hpbackup" failed: No such file or directory (2)".  Does the target have a "/media/BUFFALO" directory?  If you create it, does it cure the problem?

There was no directory so I created it and got this message when I ran incbackup ```
 incbackup
sending incremental file list
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: mkdir "/media/BUFFALO/hpbackup" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(605) [Receiver=3.0.9]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9]


``` 
I installed openssh-server beforehand. There are two questions I need to ask, the first is, my storage device is called  BUFFALO shouldn't it create its own directory when it mounts? Second is, I don't understand how the rsync thing works, if it backs up my other computer without openssh-server why can't it do so with this one? 

Please forgive my ignorance.

---

### Post by SeijiSensei on 2013-12-16
You should run backups as the root user to avoid permission problems.  Use "sudo incbackup" and enter your login password when prompted.

I don't know why rsync ran without openssh on the other machine.  Were you running rsync over the network, or using it to copy from one set of directories to another, or to a locally-mounted device?

---

### Post by MibunoOokami on 2013-12-17
> **SeijiSensei said:**
> You should run backups as the root user to avoid permission problems.  Use "sudo incbackup" and enter your login password when prompted.

I don't know why rsync ran without openssh on the other machine.  Were you running rsync over the network, or using it to copy from one set of directories to another, or to a locally-mounted device?

After seeing the permission denied message I tried "sudo incbackup" but that spat out ```
:/$ sudo incbackup
sudo: incbackup: command not found

```

I just use it to copy the contents of my computers' hard disks to a portable hard disk, not over a network though I don't think.

---

### Post by nerdtron on 2013-12-17
Since you external hasd drive is mouted. And I assume that incbackup is a script, also I would assume you put it in a custom directory to the current user only? That is why when you run sudo, it says command not found. 
Maybe we can deciper some of these errors if you post the contents of the incbackup script?

---

### Post by MibunoOokami on 2013-12-17
> **nerdtron said:**
> Since you external hasd drive is mouted. And I assume that incbackup is a script, also I would assume you put it in a custom directory to the current user only? That is why when you run sudo, it says command not found. 
Maybe we can deciper some of these errors if you post the contents of the incbackup script?

Yes, drive is mounted, incback up is a script in directory called bin. The script is below.
```
   #! /bin/bash

#copy the contents of ~/ to the given device /media/BUFFALO
#only changed or new files will be copied

rsync -av ~/ /media/BUFFALO/hpbackup
```

---

### Post by nerdtron on 2013-12-17
So it's either ~/ and /media/BUFFALO/hpbackup has permission issues. Then let's see which files you are not permitted.

```
 cd ~/
ls -la

```
and
```

cd /media/
ls -la

```

Or you can just run it again in sudo mode like this, (use a direct path to the script)
sudo bash /path/to/bin/directory/incbackup

Let's see how it goes.

---

### Post by MibunoOokami on 2013-12-17
> **nerdtron said:**
> So it's either ~/ and /media/BUFFALO/hpbackup has permission issues. Then let's see which files you are not permitted.

```
 cd ~/
ls -la

```
and
```

cd /media/
ls -la

```

Or you can just run it again in sudo mode like this, (use a direct path to the script)
sudo bash /path/to/bin/directory/incbackup

Let's see how it goes.

Assuming the files/directories labelled root root are the ones that need permission they are as follows.

~/ ```
   drwxr-xr-x  4 root root     4096 Nov 23 10:18 .. 
 drwx------  2 root root     4096 Nov 26 11:13 .gvfs 
 -rw-------  1 root root        0 Nov 27 16:23 .Xauthority 


```

/media/```
   drwxr-xr-x   5 root root 4096 Dec 16 20:50 . 
 drwxr-xr-x  21 root root 4096 Dec  4 06:36 .. 
 drwxr-xr-x   2 root root 4096 Dec 16 20:50 BUFFALO 
 lrwxrwxrwx   1 root root    7 Nov 23 09:58 floppy -> floppy0 
 drwxr-xr-x   2 root root 4096 Nov 23 09:58 floppy0 
 drwxr-x---+  2 root root 4096 Dec 17 18:35 username 


```

That's interesting, I don't have a floppy drive or even a cd drive not sure why it says floppy there. My device isn't listed in there either, the directory labelled BUFFALO is the one I created the other day.

I would like to learn how to fix this first before using the direct path. Thanks

---

### Post by nerdtron on 2013-12-17
(Don't worry about floppy drives or cd drives, ls-la means to list all, including hidden files or unused)

So the directory labelled BUFALLO is not your external hard drive? Then where is your external drive mounted? If you run the script and the drive is not mounted on /media/BUFFALO, then you will have permission issues for sure.
Assuming it the external hard drive is not mounted yet, you can mount to the BUFFALO directory by:

sudo mount /dev/sdb1 /media/BUFFALO

That is assuming your external hard drive is /dev/sdb1.
If you want make sure which device it is, run "sudo fdisk -l".
If you want to see if the device is mounted, run "mount"
If you are successful mounting the drive, try running the incbackup script again.

---

### Post by MibunoOokami on 2013-12-17
That directory is definitely not my external hard drive. When I plug the drive in it pops up asking for a password in order to mount it and says (/dev/sdb1) if that's any help. That command (sudo mount /dev/sdb1 /media/BUFFALO) worked so I guess my other computer and this one when I had full ubuntu on it automatically mounts in or at /media/BUFFALO.

Whilst getting this fixed is primarily so that I can back up my files and switch back to full Ubuntu when I have time, I would still like to know how to make it always mount where it should. Can you tell me how to do that please?

One last question, at the end of the back up there was a new error message ```
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]
``` I'm a little confused about the "see previous errors" message since this is the first time I've used incbackup with mini Ubuntu, any idea what it might be? Thanks

---

### Post by nerdtron on 2013-12-18
So I think since the last error was just attributes issue, you were able to rsync your files successfully.
That error shows (almost) always when you copy files from Linux in to a drive that is NTFS. If that is the case, and there were no failed transfers or missing files, then everything was copied.

Regarding mounting the drive, since rsync was successful, then you mounted the drive correctly on the correct path.
You want to mount the drive automatically whenever you insert it? I don't much about that, maybe you should start a new thread.

---

### Post by MibunoOokami on 2013-12-18
> **nerdtron said:**
> 
Regarding mounting the drive, since rsync was successful, then you mounted the drive correctly on the correct path.
You want to mount the drive automatically whenever you insert it? I don't much about that, maybe you should start a new thread.

It automatically asks for my password to mount the hard drive when I insert it and I can view its contents no problem. I figure something's not right though since I had to specifically add the /media/BUFFALO part to the mount command before being able to run incbackup. I may start a thread about that in the new year.

Thank you for your help Nerdtron, I do appreciate it and will mark this thread as solved now that rsync has pretty much been sorted.

---

### Post by nerdtron on 2013-12-18
Glad that it worked out for you.

---

