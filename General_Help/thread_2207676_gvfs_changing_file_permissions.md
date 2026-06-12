---
title: "gvfs changing file permissions?"
date: 2014-02-24
forum: General Help
---

### Post by Beta_Grumm on 2014-02-24
I'm running Ubuntu 13.10 with kernel 3.13.1
I'll try and explain the issue as best as I can:

I ssh into a server and execute a bash file.
I connect to a network drive, open that bash file in a local editor, save the file.
Return to the ssh terminal, attempt to execute the file again and the permissions have been stomped and I have to chmod +x to be able to run it.
If I edit the file through the ssh terminal via vim, it does not do this so it's not on the server side.

At first, I thought this was an issue with sublime text, (my usual editor) but then I was able to reproduce the issue when using gedit, or vim locally. 

It was suggested that it has something to do with the way ubuntu is mounting the network drive with gvfs. 

That's really about all I know.
Could this be caused by the gvfs mount system and if so, how can I prevent it from stomping file permissions?

---

### Post by coldcritter64 on 2014-02-24
Try the "mount -l" (that is a lower case L, and don't include the quotation marks) command and see if you can recognize the network drive and post back the mount options listed with it. 

That would be a place to start looking for the mount options used with the network drive.

---

### Post by Beta_Grumm on 2014-02-25
Ok here's the mount -l

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=micah)





To be honest, I don't really know what I'm looking at here, because if I unmount the network drive, this doesn't change.

---

### Post by coldcritter64 on 2014-02-25
> **Beta_Grumm said:**
> Ok here's the mount -l

[B]...gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=micah)
[/B]




To be honest, I don't really know what I'm looking at here, because if I unmount the network drive, this doesn't change.

A bit of a "stab in the dark" ... With your share mounted see what contents are in the folder above. Otherwise I'm not too sure with how the share is being set up.

edit more info : Open **/run/user/1000/gvfs **in nautilus that is. If permissions block you looking as user use,
```
gksu nautilus /run/user/1000/gvfs
```_*but only if needed run as normal user if you can.*_

---

### Post by Beta_Grumm on 2014-02-25
Ok. 
Running nautilus /run/user/1000/gvfs opens a nautilus window correctly displaying my phone (connected via usb), and the network share.

---

### Post by Beta_Grumm on 2014-02-25
Perhaps my issue has nothing to do with the gvfs. That being the case, can anyone think of a reason that my local machine would be changing the file permissions of a file that I've opened from a remote location?

---

### Post by steeldriver on 2014-02-25
Out of curiosity, what method/protocol are you connecting to the remote drive with? SSH (SFTP)? Windows share (CIFS/SMB)? something else?

---

### Post by Beta_Grumm on 2014-02-26
The share is connected via SMB.

---

### Post by Beta_Grumm on 2014-02-26
Apparently whatever is causing the drop of executable on the files, is also the same thing that is causing a conversion of line endings from LF to CRLF. This has been the source of so many obscure bugs in my code that I'm working on.

I knew that the line ending conversion was happening, but I didn't think it was related. Does this shed any new light on what might be doing this? Again, It's happening on multiple local editors, so it's not editor specific. All signs point to something local to the OS.

---

### Post by bab1 on 2014-02-26
> **Beta_Grumm said:**
> Perhaps my issue has nothing to do with the gvfs. That being the case, can anyone think of a reason that my local machine would be changing the file permissions of a file that I've opened from a remote location?
All of your problems are due to mount time ownership and permissions issues.  The file system ownership and permissions are always set at mount time.

When you "connect with the NAS" what it really happening is you mount a portion of the remote file system to the local file system.  It depends on which tools you are using as to who is the owner and what permissions you end up with.  In addition the various applications (e.g. Libre Office) have their own assumptions as to what ownership and permissions are.  Libre Office is notorious for this lack of gvfs awareness.

It is also possible to have differing ownership and permissions depending on whether the file resides on a remote host or is on the local file system.  Regardless of all of that, the thing to remember is that the permissions and ownership can change.  The only way to control that is for you to create the mount command as you want the ownership and permissions in a script or via fstab.

---

### Post by Beta_Grumm on 2014-02-26
Ok.
So that sparked a little googling, specifically on how to custom mount my smb. I ran across an article that mentioned the -o parameter with the fileperms=whatever. However when I looked through the man for mount I saw no reference to this option. 
I also thought about setting the umask, but that doesn't really seem like a usable option either. 

Two things I guess, 
1. How do I view the current default settings that the smb share is being mounted with?

2. Can I/How do I directly change them?
(Google wasn't especially helpful with either of these questions)

I've poked around in gvfs man page and I can't seem to get any of this information. I'd like to see if the fileperms or umask parameter is being used and what it's currently set to.

Bear with me, this is all new territory I'm wading through.

---

### Post by bab1 on 2014-02-27
> **Beta_Grumm said:**
> Ok.
So that sparked a little googling, specifically on how to custom mount my smb. I ran across an article that mentioned the -o parameter with the fileperms=whatever. However when I looked through the man for mount I saw no reference to this option. 
I also thought about setting the umask, but that doesn't really seem like a usable option either. 

Two things I guess, 
1. How do I view the current default settings that the smb share is being mounted with?

mount or mount -l shows the settings that are in current use.
> 
2. Can I/How do I directly change them?
(Google wasn't especially helpful with either of these questions)

You set them at mount time only.  There should be no need to change them after that.
> 
I've poked around in gvfs man page and I can't seem to get any of this information. I'd like to see if the fileperms or umask parameter is being used and what it's currently set to.

See question #1
It seems the man page for *mount * is outdated.  The reference is to smbfs, which is now cifs.   A more detailed and current description of the options can be found here ```
man mount.cifs
```
Read the mount.cifs page, then as questions here.  Then we can decide whether to mount the share via a script or from fstab with your options upon boot up.

---

### Post by Beta_Grumm on 2014-02-27
Ok, so I installed cifs-utils, as I wasn't able to find a man page until I did. 
I rebrowsed through man mount, and man mount.cifs.

I started trying to mount the network drive manually by just trying commands and options that seemed relevant. However, I'm obviously missing something basic.

I'm getting stuck when I try just a simple mount such as:
```
mount.cifs //<server>/<folder> /mnt/share
```

This returns the message ```
Couldn't chdir to /mnt/share: No such file or directory
```
Now, I guess I don't know what a valid option is for this, but it seems to be necessary. At one point I read in the man mount that if it was not present, that it would go ahead and look for an appropriate location, but when I try the command with out it, I just get a usage message.

After rereading the man pages for more info on this, I have come up with no new information. What is a valid option for the <dir> in ```
mount.cifs <remotetarget> <dir> -o <options>
```?

---

### Post by bab1 on 2014-02-27
> **Beta_Grumm said:**
> Ok, so I installed cifs-utils, as I wasn't able to find a man page until I did. 
I rebrowsed through man mount, and man mount.cifs.

I started trying to mount the network drive manually by just trying commands and options that seemed relevant. However, I'm obviously missing something basic.

I'm getting stuck when I try just a simple mount such as:
```
mount.cifs //<server>/<folder> /mnt/share
```

This returns the message ```
Couldn't chdir to /mnt/share: No such file or directory
```
Now, I guess I don't know what a valid option is for this, but it seems to be necessary. At one point I read in the man mount that if it was not present, that it would go ahead and look for an appropriate location, but when I try the command with out it, I just get a usage message.

After rereading the man pages for more info on this, I have come up with no new information. What is a valid option for the <dir> in ```
mount.cifs <remotetarget> <dir> -o <options>
```?

Even the man pages can be confusing.   Showing the reader this ```
SYNOPSIS
     mount.cifs <service> <mount-point> [-o options]

```...means you should be able to use it at the CLI.

But in fact, this  would indicate not```
DESCRIPTION
       This tool is part of the cifs-utils suite.

       mount.cifs mounts a Linux CIFS filesystem. It is usually invoked indirectly by the
       mount(8) command when using the "-t cifs" option.
```

I use the latter.  In most cases only root can use the mount filesystems.  Here is what I use```

sudo mount -t cifs //server/share <mountpoint> -o options> 

```

I use these options myself```

-o uid=<uid of user>,gid=<gid of user groupt>,nobrl

```

There are others in mount.cifs.  You can also use the options in mount if they don't conflict.  Try it and see if everything works correctly (permissions and ownership wise).  Try creating a document in the share.  Check the ownership and permissions.

You shouldn't need to worry about umask, but we can deal with that too if it is a problem.  The nobrl option is specifically for Libre Office in my case.

Questions   ;-)

---

### Post by Beta_Grumm on 2014-02-27
Ok, so progress!
I was able to mount my share via CLI.
I first created a folder in /mnt/ called myfolder
```
sudo mkdir /mnt/myfolder
```
Then to mount I used:
```
sudo mount -t cifs //server/share /mnt/myfolder -o defaults,username=<user>,password=<pass>
```

According to man, defaults should give me rw, suid, dev, exec, auto, nouser and async. I don't know what all of those do but it seemed like it should get me started. 

HOWEVER, after mounting, I browsed to the folder, opened up a script file, edited it, and then tried to save it but got the following error message: "Unable to save /mnt/myfolder/script.sh"

I should have permissions to read and write. What's this all about?

---

### Post by bab1 on 2014-02-27
> **Beta_Grumm said:**
> Ok, so progress!
I was able to mount my share via CLI.
I first created a folder in /mnt/ called myfolder
```
sudo mkdir /mnt/myfolder
```
Then to mount I used:
```
sudo mount -t cifs //server/share /mnt/myfolder -o defaults,username=<user>,password=<pass>
```

According to man, defaults should give me rw, suid, dev, exec, auto, nouser and async. I don't know what all of those do but it seemed like it should get me started. 

All of this is in the man pages.  The defaults are: Read/Write, allows suid, allows executable files to be made, Forbid  an  ordinary  (i.e.,  non-root)  user to mount the filesystem., All  I/O  to  the  filesystem  should  be  done  asynchronously. 
> 

HOWEVER, after mounting, I browsed to the folder, opened up a script file, edited it, and then tried to save it but got the following error message: "Unable to save /mnt/myfolder/script.sh"

I should have permissions to read and write. What's this all about?
Not if you are not the owner (user or group) of the directory and have the correct permissions.  My guess is that the user root is the owner of the files.  

This is for the authentication (who are you) of the user (Samba)```
username=<user>,password=<pass>
```...it does not set the ownership and permissions, which is used for authorization (can you use this resource).  

Without the uid and gid explicitly defined  the mount operation uses the root users uid and gid.

More questions  ;-)

---

### Post by Beta_Grumm on 2014-02-27
YEEEEEEEEEEEEEEEEEEESSSSS!!!
IT WORKS!
My god!
I think we solved it!

Ok, here's the solution:
From command line, create a folder in /mnt/:
```
sudo mkdir /mnt/myfolder
```
Look up your uid and gid:
```
id <user>
```
Returned a uid=1000 and gid=1000
Then, mount the NAS:
```
sudo mount -t cifs //<server>/<folder> /mnt/myfolder -o username=<user>,password=<pass>,rw,exec,uid=1000,gid=1000
```

I then browsed to myfolder, opened up a script file in a local editor, edited it, saved it back to the share folder, then ran it on the server, and presto! All is right with the world.
Thank you so much for helping me out with this. I've learned a lot.

---

### Post by bab1 on 2014-02-27
> **Beta_Grumm said:**
> YEEEEEEEEEEEEEEEEEEESSSSS!!!
IT WORKS!
My god!
I think we solved it!

Ok, here's the solution:
From command line, create a folder in /mnt/:
```
sudo mkdir /mnt/myfolder
```
Look up your uid and gid:
```
id <user>
```
Returned a uid=1000 and gid=1000
Then, mount the NAS:
```
sudo mount -t cifs //<server>/<folder> /mnt/myfolder -o username=<user>,password=<pass>,rw,exec,uid=1000,gid=1000
```

I then browsed to myfolder, opened up a script file in a local editor, edited it, saved it back to the share folder, then ran it on the server, and presto! All is right with the world.
Thank you so much for helping me out with this. I've learned a lot.

You can look at the owner/permissions in the directory with this```
ls -l /path/to/directory 
```

If this share is going to be mounted all the time and the Samba server (NAS) is always on, we can mount the share via the fstab tab file.  This file (/etc/fstab) is the configuration file for the mount command at boot up time.

You can unmount the share like this```

sudo umount <path/to/directory

```..this would be: *sudo umount /mnt/mydirectory*

---

### Post by Beta_Grumm on 2014-02-27
Yes, this was the next step. I was just going to create a bash script, but if I can get it to mount automatically, even better.

I opened up /etc/fstab.
The template looks like it's: # <file system> <mount point>   <type>  <options>       <dump>  <pass>
so the line I add to the fstab file should look like:
```
//server/folder/ /mnt/myfolder cifs username=<user>,password=<pass>,rw,exec,uid=1000,gid=1000 0 0
```
That is:
file system= //server/folder
mount point = /mnt/myfolder
type = cifs
options = username=<user>,password=<pass>,rw,exec,uid=1000,gid=1000
dump = 0
pass = 0

Does this look correct?

---

### Post by bab1 on 2014-02-27
> **Beta_Grumm said:**
> Yes, this was the next step. I was just going to create a bash script, but if I can get it to mount automatically, even better.

I opened up /etc/fstab.
The template looks like it's: # <file system> <mount point>   <type>  <options>       <dump>  <pass>
so the line I add to the fstab file should look like:
```
//server/folder/ /mnt/myfolder cifs username=<user>,password=<pass>,rw,exec,uid=1000,gid=1000 0 0
```
That is:
file system= //server/folder
mount point = /mnt/myfolder
type = cifs
options = username=<user>,password=<pass>,rw,exec,uid=1000,gid=1000
dump = 0
pass = 0

Does this look correct?
Yes.  But I would put the password in a credentials file in your home directory.  I use .smbcred (the dot (.) makes it hidden.  In that file I have ```
username= <your username>
password=<your pass>

``` ...then you can used the option *credentials = /home/<user>/.smbcred* instead of user and password naked for all to see in your fstab file.

See the man pages of this.

More and more questions ;-)

---

### Post by Beta_Grumm on 2014-02-27
So I added the line to fstab, put my credentials in a file in my home directory, restarted my computer and it worked perfectly!
I also figured out how to add the new mount as a bookmark in nautilus.

Everything is setup and ready to rock! Thank you, again, so much.

---

### Post by bab1 on 2014-02-27
> **Beta_Grumm said:**
> So I added the line to fstab, put my credentials in a file in my home directory, restarted my computer and it worked perfectly!
I also figured out how to add the new mount as a bookmark in nautilus.

Everything is setup and ready to rock! Thank you, again, so much.

I just noticed you left the nobrl option off the fstab line.  I would go back and add that.  You can remount everything like this```
sudo mount -a
```...no need to restart the computer.

---

