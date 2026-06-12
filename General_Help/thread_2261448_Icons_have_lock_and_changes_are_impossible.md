---
title: "Icons have lock and changes are impossible"
date: 2015-01-19
forum: General Help
---

### Post by hvn2 on 2015-01-19
Hi,

A laptop running 14.04 shows all icons with a lock. All permissions of the icons are for the user, but when the icons are clicked the message appears that there is no permission. Also, with the Firefox icon, it says it is already started. All permissions of the files in ./Desktop are for the user (755) as should be.
A second problem is that, when in terminal, tab-completion doesn't work anymore because writing is disabled. Chown and chmod are no longer possible.
A third problem is that all cli commands given since the lock started, are not remembered. So with arrow-up and down, only older commands are shown.
What does work are su to root and sudo. This way can I still can reboot and shutdown, because shutdown/reboot from the menu is disabled as well.

Does anyone have a clue what might cause this (and a solution) ? (I rather would not have to reinstall...)

---

### Post by nerdtron on 2015-01-19
What happened or what did you do before this?
First even though files are 755(folder) and 644(files) are set, if you are not the owner of the files, then there will still be a locked icon. To correct the ownership of your whole home folder to your user:
```
 sudo chown -R myusername:myusername /home/myusername
```

Let's see first how that command (I think will affect/solve problem 2 and 3)
To confirm that you have the correct permissions on your home folder:
```
ls -lah /home/myusername 
```

---

### Post by kerry_s on 2015-01-19
just a wild guess, but if you can su to root, you activated root & if you activated root & did anything as root in your home folder, it would be owned by root locking you out.

i remember doing something like that once upon a time, my solution was to delete everything in my user folder as root & reboot. when i logged back in everything was back to like the first time after a clean install.

i'm not saying do that, you should wait for others to give some input. if all else fails, do what ya gotta do.

---

### Post by hvn2 on 2015-01-19
> **nerdtron said:**
> What happened or what did you do before this?
First even though files are 755(folder) and 644(files) are set, if you are not the owner of the files, then there will still be a locked icon. To correct the ownership of your whole home folder to your user:
```
 sudo chown -R myusername:myusername /home/myusername
```
Ok, forgot to mention that I am the owner of the files as well. And as said, neither chown nor chmod work anymore, neither as root nor as user.
> 
Let's see first how that command (I think will affect/solve problem 2 and 3)
To confirm that you have the correct permissions on your home folder:
```
ls -lah /home/myusername 
```
I did check that, and that is as should be.

---

### Post by steeldriver on 2015-01-19
In what way do chown and chmod "not work" - are there any error messages?

Is it possible that your filesystem is mounted read-only (perhaps because of disk errors)?

---

### Post by hvn2 on 2015-01-19
> **steeldriver said:**
> In what way do chown and chmod "not work" - are there any error messages?
Yes, write errors, but I can't copy/paste them in here.
> 
Is it possible that your filesystem is mounted read-only (perhaps because of disk errors)?
That is a good point. I do notice it does check the harddisk for errors on each (re)boot since this lock is going on. So this can indicate a read-only mount. Is there a way to check and/or solve this ?

---

### Post by nerdtron on 2015-01-19
check for the filesystem:
```
mount
```

It's puzzling, you just says permissions are correct yet you don't provide any inputs..

---

### Post by Holger_Gehrke on 2015-01-19
This command
```

cat /proc/mounts

```
gives the status of all mounted file systems (as opposed to 'mount -l', which gives the mounted file systems and the options given at mount time). To (try to) repair the problem boot from some live medium and 'fsck' the file system

---

### Post by hvn2 on 2015-01-19
> **Holger_Gehrke said:**
> This command
```

cat /proc/mounts

```
gives the status of all mounted file systems (as opposed to 'mount -l', which gives the mounted file systems and the options given at mount time). To (try to) repair the problem boot from some live medium and 'fsck' the file system

OK, this shows all mounts are rw, except for /dev/disk/by-uuid/<number> / ext4 ro,relatime,error=remount-ro, data=ordered 0 0

I compared this with another machine where it says rw, so I assume this indeed is the problem. Will try to fsck the filesystem.

---

### Post by hvn2 on 2015-01-19
Ok, despite using fsck in maintenance-mode (fixed /dev/sda1) as well as gparted-live check and fix (seems to have fixed some left errors) there's no change: / partition still on ro instead of rw. I did find "mount -o remount -o rw {partition}" in a forum but doubt I should use that on the / partition. Any recommendations ?

---

### Post by Holger_Gehrke on 2015-01-19
It might help to look in the output of 'dmesg'. This command show all messages the kernel has given during (and since) boot. Be prepared to search a bit, this can get long (and technical and partially far beside the point).

---

### Post by hvn2 on 2015-01-19
Ok, ty for this hint. I know dmesg, but didn't think of looking at it. Found the culprit. Some forumposts report a bad controller, but bad medium is most likely.

---

### Post by nerdtron on 2015-01-20
since the partition is in read only mode, that's the reason why the files have locked icons even if you have the correct permissions on the files/folders.

The command you mentioned regarding mount remount, I tried it a few times, once in recovery mode for read/write on / partition. i also used that command on a mounted partition before.

you might wanna run fsck on your drives.

---

