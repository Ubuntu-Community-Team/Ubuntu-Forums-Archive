---
title: "[SOLVED] A File with Permissions for All Users"
date: 2008-02-11
forum: General Help
---

### Post by L8erG8er on 2008-02-11
Sorry if this has been answered.  I am trying to make a directory where all users can read, write, execute.  It seems that right now, which ever user creates a file in the directory, they are the only one that can write to it.  I would like all users to be able to pull up the file and modify it.

Is there a way around this?  Obviously I'm not good with umask and general permissions.

Thanks!

---

### Post by Nepherte on 2008-02-11
with
```
chmod 0777 directory
```
you give everyone all rights. Be warned that this is not always a safe thing to do.

---

### Post by L8erG8er on 2008-02-12
> **Nepherte said:**
> with
```
chmod 0777 directory
```
you give everyone all rights. Be warned that this is not always a safe thing to do.

Thanks for the reply.  If I do this, what happens if any user creates a new file in that directory?  Is the new permission inherited?

---

### Post by port on 2008-02-12
> **L8erG8er said:**
> Thanks for the reply.  If I do this, what happens if any user creates a new file in that directory?  Is the new permission inherited?

"chmod 077 directory" will only allow anyone to read / write to that directory. When a user creates a file in that directory, the owner will have read /write permissions, group and other will only have read permissions on the file.

---

### Post by wieman01 on 2008-02-12
But users can control their own permissions... which isn't nice, I know, but that's a possibility nevertheless.

---

### Post by bernied on 2008-02-12
[EDIT]You might want to read the rest of this thread before trying this, as I left something vital out[/EDIT]

I do it like this:
- create a group for the shared area, if the group was to be called share, then:```
sudo groupadd share
```
- add the users who you want to be able to access the share to the group:```
sudo adduser bernie share
```(repeat this for each user)

- change group ownership of the directory (and any of it's contents):
```
sudo chown -R :share /path/to/share
```
- set the group write and sticky bits (this is the what will maintain group permissions in sub-directories) on the directory (and any contents)
```
sudo chmod -R g+ws /path/to/directory
```

Any logged in users will have to log out and in again for this to take effect.

---

### Post by L8erG8er on 2008-02-13
bernied:

Thanks very much, this is what I'm looking for.  
I tried this, but when I wrote another file and saved it in the new shared directory, other users were only able to open the file read-only.  So now I'm lost again.

---

### Post by bernied on 2008-02-13
Oops I am very sorry, there is one element missing from my recipe, it is the UMASK, which helps to define the default permissions of every new file, including directories. This is not a trivial thing, so I suggest you find out what it is you are doing before you do what I suggest below, as this is a system-wide change you are making. I am also uncertain that all programs will follow the default umask, I think that Konqueror in KDE for example does not.

This needs to be changed in /etc/profile, which needs to be edited as the root user, so:
```
gksu gedit /etc/profile
```
On my machine the umask value was set right at the bottom of the file, and I changed it from:
```
umask 022
```
to```
umask 002
```
Again you would need to log out and in again before this will take effect, I'd also suggest restarting the display manager, so Ctrl-Alt-Backspace once you are logged out.

There is a fairly good explanation of  UMASK at the bottom of [this page](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html).

In Ubuntu, the UMASK is set at 022, which means that when files are created, the group permission and the others permission are always set -w, meaning that the group and others cannot write to the file. Personally I think this is a mistake, because it means that groups are meaningless as they have the same permissions as everyone else. So I always change mine to 002, which means that user and group have the same permissions by default. 

If you want to see all ownership and permissions information about a file, use the command 'ls -lh' (I think the 'l' means long and the 'h' means human-readable).

```
bernie@vserver:~$ mkdir share
bernie@vserver:~$ chmod g+sw share
bernie@vserver:~$ ls -lh
<snipped>
drwxrwsr-x  2 bernie users    4.0K Feb 13 09:26 share
<snipped>
bernie@vserver:~$ umask
0002

```Note the permissions on the directory are drwx**rws**r-x, which is because my umask is 0002 instead of the standard 0022.
The 'rws' in the middle means that members of the group have read, write and execute permissions (execute for a directory means ability to navigate the directory, which is distinct from read), and the group sticky bit is set, which means that any files created in the directory will have the same group ownership.

I hope this is still helpful.

---

### Post by L8erG8er on 2008-02-13
That's it!  Bernie, thanks so much.  I appreciate you taking time to teach a newbie the umask ropes.  With umask set this way in the profile, I'll just keep an eye on "others" settings.

---

