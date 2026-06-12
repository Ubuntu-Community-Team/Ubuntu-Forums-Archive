---
title: "really, really locked out, can't change password"
date: 2013-06-12
forum: General Help
---

### Post by linbo on 2013-06-12
I've searched and searched and cannot find the solution to my locked out problem

I was using Ubuntu on my home computer three years ago for remote work and have not tried to log in since then.  Now I'd really like to login again.

I boot my computer using the last recovery kernel available (it's ubuntu 10.something but I don't think the version is really the problem)
I select the boot to root shell then try to reset my password
I get an error message:
"Authentication token manipulation error"

I try all the various fixes in all the searches, i.e.
I check write permission for / and /etc both are rw for root
I still try the mount command, >> mount -o rw,remount /
but that produces an error saying I cannot remount

OK so I check write permissions for /etc/passwd and /etc/shadow, both are rw for root.  Both files have an entry for acorn user and the shadow file has a long encrypted string in the password field (second from username)

What can I do?  
I've read all sorts of posts about copying the shadow file, using some utility to delete the shadow file, logging in using ssh, etc.
None of these solutions seems right.  I don't have a backup and so I'm hesitant to just go in and muck with these files.  Not sure if I can copy all the Ubuntu stuff from Windows side (I have a terabyte standalone drive so space isn't an issue)
Right now I'm posting this from the Windows side.

Does anyone have any suggestions?

---

### Post by Toz on 2013-06-12
> I boot my computer using the last recovery kernel available (it's ubuntu 10.something but I don't think the version is really the problem)
I select the boot to root shell then try to reset my password
I get an error message:
"Authentication token manipulation error"Its probably because the filesystem is mounted readonly. Remount it as read/write then try resetting the password again:
```
mount -rw -o remount /
```

---

### Post by Iowan on 2013-06-12
Have you tried creating another user? The new one wouldn't have sudo privileges, but would be a step forward.

---

### Post by linbo on 2013-06-12
Um, I've tried that.  Not sure why my post isn't showing.  I've checked all the rw permissions, /, /etc, /etc/shadow, /etc/passwd, and tried remounting.  All permissions show rw in the root field (i.e. first area) and remount gives error message

thanks

---

### Post by linbo on 2013-06-12
Hmm, haven't tried creating a new user--is there a way to do this while still in the root recovery shell?  Meaning I have no access to the regular commands or apps

---

### Post by Iowan on 2013-06-12
**adduser** would be the command - **man adduser** for details.
(I always get confused between **adduser** and **useradd**)

---

### Post by Toz on 2013-06-12
> **linbo said:**
> ..... and remount gives error message
What is the error message?

What does the following command show?
```
mount
```

---

### Post by linbo on 2013-06-12
mount -o rw,remount /
gives error message:

......EST4-fs error (device loop0): ext4_remount: Abort forced by user.........
......mount: cannot remount block device /host/ubuntu/disks/.............
......riit,dusj read-write, is write-protected

the ...... are where the text runs off the screen, i.e. I cannot see the entire error message

the mount command by itself gives a page of lines, too many to write down--no errors but a warning at the bottom
warning /etc/mtab is not writable e,g, read-only file system

I hesitate to change permissions on this without knowing what I'm doing.

I'll try creating a new user next

---

### Post by carboi82 on 2013-06-12
[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)  The second half of that how-to has worked for me in the past...

---

### Post by linbo on 2013-06-12
no success

adduser yields error message:
>adding user lingo
>adding new group linbo
>groupadd: cannot lock /etc/group; try again later
>adduser: '/usr/sbin/groupadd -g 1001 linbo' returned error code 10 Exiting

useradd yields error message:
>cannot lock /etc/passwd

second methd from howtogeek yields
"Authentication token manipulation error" message when I get to the point of changing the password for acorn user

It's clear that this is a write permission problem.  Should I try a different title in hopes of snagging an expert that knows how to force the write permissions?

---

### Post by Iowan on 2013-06-12
> **linbo said:**
> It's clear that this is a write permission problem.  Should I try a different title in hopes of snagging an expert that knows how to force the write permissions?You can use the Report Post button to request staff to edit the title. Give it a day, though, to see what other information shows up. You can also search here (and elsewhere) to see what that "Authentication token manipulation error" message or what "cannot remount block device" means.

---

### Post by steeldriver on 2013-06-12
If it is refusing to remount the root partition with write permissions, that may be because it has detected filesystem damage - if there's an option to run a filesystem check from the recovery menu (instead of dropping to the root shell) you could try that, if it completes successfully it should leave the filesystem mounted rw anyway and you can then drop back to the root shell and try the password reset again

However based on your earlier post mentioning 'loop0' and '/host' I'm guessing this is a wubi install? in which case I'm really not the right person to advise since I've never used wubi

---

### Post by HiImTye on 2013-06-12
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
here's a couple methods to try [http://www.botskool.com/geeks/how-recover-your-ubuntu-1004-password](http://www.botskool.com/geeks/how-recover-your-ubuntu-1004-password)

---

### Post by carboi82 on 2013-06-13
I believe youre getting that error because its only mounting the filesystem in read only. After dropping into the root shell from the boot loader, you can force it to mount it in rw with

[FONT=Ubuntu Mono]mount -rw -o remount /[/FONT]

then continue and change the password

---

### Post by Impavidus on 2013-06-13
This indeed looks like a wubi install. Maybe you have to remount /host as rw first. I'm not a wubi specialist, but it might help.

Ubuntu 10.something has reached end of live. This means that if you want to resume using Ubuntu you can best upgrade to a later version. You can create a live disk, boot from that and try to mount your partition from there. First mount the ntfs partition where it is installed, then mount ubuntu/disks/root.disk, which contains your file system, and rescue any files you like to keep. Then reinstall. I don't think fixing this complicated stuff on an end-of-live version is really worth the effort.

I hope you didn't encrypt your home directory. If that's the case recovery will be nearly impossible.

---

