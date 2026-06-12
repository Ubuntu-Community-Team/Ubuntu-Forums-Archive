---
title: "Can't login as root"
date: 2022-06-28
forum: General Help
---

### Post by veedub67 on 2022-06-28
Hello,

I'm using 22.04

I have tried enabling root and setting the password using the following guides

[https://linuxize.com/post/how-to-enable-and-disable-root-user-account-in-ubuntu/](https://linuxize.com/post/how-to-enable-and-disable-root-user-account-in-ubuntu/)

[https://www.tecmint.com/reset-forgotten-root-password-in-ubuntu/](https://www.tecmint.com/reset-forgotten-root-password-in-ubuntu/)

I was able to follow both sets of instructions

However when I try to login as root, I get

```
Sorry, password authentication didn't work. Please try again
```

Would appreciate suggestions on how to troubleshoot.

Thanks

VW

---

### Post by QIII on 2022-06-28
Hello!

Do you realize that the root account is disabled in Ubuntu by default for security reasons?  It is a very bad idea to enable it.  There is little reason to in any case, since you can temporarily elevate your privileges using sudo if you are the one who installed the OS or if you have been included in the sudoers list by an admin (which whatever limitations might have been imposed).  Even with distros that have the root account enabled, is is rarely - rarely - a good idea to log in as root.

What is your reason for wanting to log in as root?  Are you wanting to run your GUI as root (that is, log in to your desktop)?  If so, we do not allow discussion about how to do that, but simply direct users to [this]("https://help.ubuntu.com/community/RootSudo").  Much of that is in flux, but you may still read the Pros and Cons to make your own decision.

---

### Post by veedub67 on 2022-06-28
@QIII

I need to schedule some tasks in cron that need to be run with root privileges

---

### Post by QIII on 2022-06-28
There is no reason to be logged in as root to do that.

```
sudo crontab -e
```

should suffice.  Just enter your password.  That will allow you to edit root's crontab.

I would make sure to ensure root is no longer enabled by removing the password.

```
sudo passwd -l root
```

---

### Post by veedub67 on 2022-07-04
Hello,

I have another reason where I may need to login as root.

I recently posted this question on the BorgBackup user-list

--------------------------------------------------------------------
 
I’m trying to mount a repository to /tmp/Borg
 
So, I do the following
 

[LIST]
[*]mkdir /tmp/Borg
[*]sudo borg mount  /media/zen/REAR-000/Borg /tmp/Borg
[LIST]
[*]Borg appears to process the command, I am prompted for the passphrase and there are no Borg errors
[*]But I can’t access /tmp/Borg
[LIST]
[*]Permission denied
[*]The permissions of “Borg” could not be determined
[/LIST]
[/LIST]
[/LIST]
 
I have tried the following, while the repository is mounted

[LIST]
[*]sudo chown -R $USER: /tmp/Borg
[*]sudo chmod 755 /tmp/Borg
[LIST]
[*]The files that have been mounted, are displayed while these commands are processed, but afterwards /tmp/Borg remains inaccessible
[/LIST]
[/LIST]
 
I have then tried the following, while the repository is unmounted

[LIST]
[*]sudo chown -R $USER: /tmp/Borg
[*]sudo chmod 755 /tmp/Borg
[*]This time the commands are successful, but after mounting the repository, /tmp/Borg becomes inaccessible, as before
[/LIST]

-----------------------------------------------------------------------------------

Here was the response:

Mounts are per user, so if you use SUDO to mount, you need some SUDOed shell to access the mounted content as well. Changing permissions on dirs won't help, those don't forward into the BORG backups AFAIK anyway. In the easiest case, try both MOUNT+ACCESS with real root shells without SUDO and move forward from there.

---

### Post by ActionParsnip on 2022-07-04
Jut use
```

sudo su -

```
You can then work as root.

---

### Post by TheFu on 2022-07-04
> **ActionParsnip said:**
> Jut use
```

sudo su -

```
You can then work as root.

Or **sudo -i**, but root-abuse is a serious issue and often leads to broken systems.  We all break our systems a few times by misusing root, so good luck and please be prepared for when that happens.

The borg mount seems to be the failing issue.  I don't know anything about the FUSE borgfs, it's capabilities or limitations, but I suspect that is where the true issue lies. [https://borgbackup.readthedocs.io/en/stable/usage/mount.html](https://borgbackup.readthedocs.io/en/stable/usage/mount.html)

---

### Post by ajgreeny on 2022-07-04
My terminal prompt as user is always green but when I very occasionally use either ***sudo su*** or ***sudo -i*** to get a root terminal, I have made the terminal prompt bright red.

This serves as a very immediate warning to me that I am acting as root and is a lot more obvious than the simple change of the wording of the prompt.

---

### Post by TheFu on 2022-07-04
> **ajgreeny said:**
> My terminal prompt as user is always green but when I very occasionally use either ***sudo su*** or ***sudo -i*** to get a root terminal, I have made the terminal prompt bright red.

This serves as a very immediate warning to me that I am acting as root and is a lot more obvious than the simple change of the wording of the prompt.

xterm's have a "secure keyboard" setting and a "reverse video" option in the menus which reverses the current colors. It is a good reminder.  The secure keyboard locks all keyboard events to that terminal, regardless for which has focus.  That's important when doing root stuff.

---

### Post by veedub67 on 2022-07-04
> **ActionParsnip said:**
> Jut use
```

sudo su -

```
You can then work as root.

Hello,

This works.

I'm able to access the mount point via the terminal

However, I would prefer to work with the mount point via a GUI File Manager.

Nautilus has an admin "plugin" (not sure if that is the correct terminology). But I installed the Nautilus admin plugin, and I can't open the Borg mount point in Nautilus using 'Open as Administrator'

If I try and launch Nautilus from the terminal session running as root, I see
```
root@Ubuntu-DR6:/tmp# nautilus
(org.gnome.Nautilus:10155): Gtk-WARNING **: 09:54:30.041: cannot open display:
```

How can I run nautilus, or some other GUI File Manager as root?

Thanks
VW

---

### Post by TheFu on 2022-07-04
So, mounts done through a GUI use an extra layer and are almost always much slower than a proper mount via the fstab or autofs.  As much as 30% slower transfers.

Running GUI programs as root is a bad idea for a number of reasons.   Whenever you see anything mentioning a display or DISPLAY, that usually means it is an X/Windows security feature blocking what you seek.  This is to prevent access to X-events on the same machine by different user accounts. It is a good thing. Sometimes, this will prevent keyloggers from capturing all X-events for nefarious use.

But, if you insist on using any GUI tool under the root account (and you shouldn't), then you can use the **xhost** command. This is just a hint and there are specific instructions for how in these forums.  But really you shouldn't to it.

---

### Post by veedub67 on 2022-07-04
@TheFu

Thanks for responding.

While I was able to find a number of posts that reference the xhost command.

I couldn't find the "magic" post to allow me to successfully launch Nautilus as root.

That being said, some smart person, mentioned using mc (Midnight Commander) a text-based file manager that can be launched from terminal. 

mc is a perfect solution for me, I just don't want to be stuck at the command line trying to copy and paste a bunch of files.

---

### Post by TheFu on 2022-07-04
> **veedub67 said:**
> 
mc is a perfect solution for me, I just don't want to be stuck at the command line trying to copy and paste a bunch of files.

There aren't any copy-paste in the CLI, so it would be very hard, indeed.

At the command line, I would use **mv**, not cp or rsync for that task.  Move within the same file system is instantaneous, since only an inode object has to be modified. It is also the magical program to rename a file or directory.
If you are moving across file systems, then I'd use rsync. Once the rsync completes successfully, I'd remove the SOURCE files.  Since you seem to want to use an elevated permissions account for this work, that implies that you need to keep the owner, group, ACLs, xattrs and permissions intact with the file move.  I'm 100% positive that happens with **sudo mv .... **, but couldn't guarantee that using any GUI, since GUIs hide how they really accomplish things.

If you learn about Unix shell globbing, you might find that moving huge numbers of files around is 100x more efficient from the shell when compared to any GUI method.  But it is fine if you want to be a GUI-only user too.

So, if I want to move all the files that start with 'Z' in my HOME directory to /tmp/, I'd use **mv ~/Z* /tmp** using {tab} completion to ensure the target directory is spelled correctly.  {tab}-completion make the shell extremely efficient and prevents dumb command, option, and directory/file name mistakes.

---

