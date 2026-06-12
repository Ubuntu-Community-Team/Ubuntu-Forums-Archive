---
title: "Problem with sshfs in Edgy"
date: 2006-10-29
forum: General Help
---

### Post by swtaarrs on 2006-10-29
I'm running Edgy on my Dell Inspiron 9300 and everything's working well except sshfs. I've spent the past half hour checking google but nothing I've found has worked. I'm not having any problems installing sshfs/fuse or mounting it, but after I run sshfs to do the mount, when I try to do an ls of the mounted directory, I get 'No such file or directory'. Also, when I do ls -l in the parent directory, it gives this:

bsimmers@cyclops:/mnt$ ls -l
total 0
?--------- ? ? ? ?                ? afs

Before I perform the mount, and after unmounting it, ls -l gives the expected results:

bsimmers@cyclops:/mnt$ ls -l
total 4
drwxr-xr-x 2 bsimmers bsimmers 4096 2006-10-29 02:53 afs

Has anyone encountered this or know how I can fix it?

---

### Post by bistrototal on 2006-10-29
I experienced exactly the same. I run Edgy on my Dell Latitude D420.

---

### Post by jetpeach on 2006-10-30
what is your exact sshfs command? i am have a permission problem with writing to the sshfs, but otherwise working in edgy.
try adding at the end of the command either "-o allow_other". or maybe "-o uid=1000" that is if 1000 is your user id.  i got it to show the permission as my user id, but strangely i still can't write to it...

---

### Post by garretwp on 2006-10-30
I am having issues with connecting to a share via ssh. I get this error:
"remote host has disconnected". Does anyone know how to fix this and what the cuase of this error message is?

- Garrett

---

### Post by swtaarrs on 2006-10-31
> **jetpeach said:**
> what is your exact sshfs command? i am have a permission problem with writing to the sshfs, but otherwise working in edgy.
try adding at the end of the command either "-o allow_other". or maybe "-o uid=1000" that is if 1000 is your user id.  i got it to show the permission as my user id, but strangely i still can't write to it...

I tried both of those, with no luck :(. Any more ideas?

---

### Post by jetpeach on 2006-11-01
i'm thinking of reporting a bug in launchpad.  it seems there are enough people having problems with sshfs fuse that something is broken.

just to check, try doing "sudo ls" in the directory under the one you've mounted to.  does it show the permissions then?  or trying running konqueror/nautilus as root and seeing if it's browsable then.

---

### Post by swtaarrs on 2006-11-01
> **jetpeach said:**
> i'm thinking of reporting a bug in launchpad.  it seems there are enough people having problems with sshfs fuse that something is broken.

just to check, try doing "sudo ls" in the directory under the one you've mounted to.  does it show the permissions then?  or trying running konqueror/nautilus as root and seeing if it's browsable then.

If I run sudo ls I get the same result:

bsimmers@cyclops:/mnt$ sudo ls -l
total 0
?--------- ? ? ? ?                ? afs

Running nautilus as either myself or root and going to /mnt shows the directory as a file of unknown type, with size listed as '---' and the date modified is 'unknown' :(. If you do open a bug, make sure to post here, I really want to get this working. Thanks!

---

### Post by swtaarrs on 2006-11-03
I found the problem:[https://launchpad.net/distros/ubuntu/+source/sshfs-fuse/+bug/46633](https://launchpad.net/distros/ubuntu/+source/sshfs-fuse/+bug/46633)

It turns out that's what sshfs does when the remote directory you're trying to mount doesn't exist. Hopefully they'll fix it to give a useful error message some time soon, but I changed the directory I'm trying to mount and it works great now.

---

### Post by garretwp on 2006-11-03
I would like to know what causes the remote host disconnected message when I try to do sshfs. I can connect to a directory via ssh in gnome, but using the sshfs command with no luck.

- Garrett

---

### Post by swtaarrs on 2006-11-03
> **garretwp said:**
> I would like to know what causes the remote host disconnected message when I try to do sshfs. I can connect to a directory via ssh in gnome, but using the sshfs command with no luck.

- Garrett

While I was poking around launchpad, I read that sshfs gives you that error if it can't find the remote host (instead of saying something useful like 'remote host does not exist') so triple check that you're typing in the right hostname and path. If you are, I don't know what else to try :(. Hopefully they'll update sshfs soon, there seem to be a lot of problems with it in edgy.

---

### Post by garretwp on 2006-11-03
Wow, that is really weird! I am almost positive that when I tried to mount a directory with sshfs that I had the path correct. I just did it real quick and all works! slaps self on head for being an idiot!

- Garrett

---

### Post by grantmasterflash on 2006-11-08
This problem doesn't just exist with Ubuntu. I'm using Suse10.1 and sshfs will disconnect in the middle of a transfer and say that the file doesn't exist. The logs on the remote system only say "subsystem request for sftp" which is normal. The only way out of this is to unmount the share and remount it which isn't acceptable. I don't want to use the builtin ssh support of gnome and kde because they're not transparent to the app. I guess it's back to Samba again. It seemed like a good idea.

Grant

---

