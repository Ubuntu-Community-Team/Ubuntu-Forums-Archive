---
title: "common data partition fails"
date: 2007-07-24
forum: General Help
---

### Post by feffer on 2007-07-24
I dual boot Kubuntu and Fedora7. Each has it's own home, but I have a common data partition which I mount "/home/user/data" I have a common group on both distros and enable "users" in fstab. This works OK and is accessible from both distros except for one thing: on Kubuntu new files created in /home/user/data are read only for the group. I can't open them from Fedora without doing chmod each time. I tried changing umask in .bashrc to 0002 (it was 0022), but something is preventing this from taking affect. I know that others have used this process to access data without messing up the config files in their /home dir, but I can't see what I'm missing. How can I get Kubuntu to play nice and create shareable files?

Thanks,
feffer

---

### Post by kuja on 2007-07-24
Pull up Konqueror and go to "/home/user" Right click on the data folder -> properties -> permissions tab - click "advanced permissions" -> Check on "Set UID" and "Set GID". Also, set Read, and write but not execute for the owner and group. Setting the Read & Write but not execute has a bad side effect, you'll need to chmod only the folders back to having execute perms, so - this command should do the trick.
```
sudo find /home/user -type d -execdir chmod +x {} +
```

And you should be good to go.

---

### Post by feffer on 2007-07-24
kuja, did as per your post, but still any new file created in data has perms of -rw- r-- ---, or user is read/write, but group is read only. I do not see what is constraining this?  I added "umask = 0002" to .bashrc, but I see after reboot that umask has reverted to 0022. I think this is the issue, but not sure how to make it persistently change.

feffer

---

### Post by kuja on 2007-07-24
Weird. I've never had any issues like this with sharing something ... Have you always used that umask? Perhaps that could be the issue to begin with ... Wait, I thought the umask was set in the fstab not the .bashrc ... in which case wouldn't you have to modify both fstabs?

---

### Post by bodhi.zazen on 2007-07-24
Yea, that can be a pain because of Fedora and Ubuntu use different numbers for users as well ;)

I do not think of my shared data partition as "secure" so you could add this to /etc/rc.local :

```
chmod -R 777 /home/user/data
```

This will set permissions at each boot of each os

* I know it is ugly, but it will get the job done :p

---

### Post by bodhi.zazen on 2007-07-24
> **kuja said:**
> Weird. I've never had any issues like this with sharing something ... Have you always used that umask? Perhaps that could be the issue to begin with ... Wait, I thought the umask was set in the fstab not the .bashrc ... in which case wouldn't you have to modify both fstabs?

LOL

Depends on just what umask you are talking about 

in fstab umask is used to set permissions of ntfs and fat partitions/drives at the time of mount.

in .bashrc umask can be used to set the default permissions of files/directories created by the user.

---

### Post by feffer on 2007-07-25
Thanks Kuja and bodhi.zazen. Normally, I wouldn't have gone through such trouble to use a common data partition. I'd just do chmod as needed on individual files. I'm going to lend this lap-top to a family member who uses Mac OS X and I wanted it as seamless as possible.

I finally resorted to putting the chmod line in rc.local, but as you noted bodhi.zazen it's not a very elegant solution ;) Yes, the fact that Fedora and Kubuntu (Debian) numbers users differently is a complicating factor. Also Fedora uses a default umask of 0002, so newly created files have group rw perms. Kubuntu seems to default umask to 0022, and that only give the user rw, but not the group. The problem is that even when I change umask, the Kubuntu new file behavior is still not group writable. I thought it would be trivial to change umask, but something else must be restraining it. In any case, I'm tired of fighting it and the rc.local line does revert the perms of any new file on reboot, so that's where I'll leave it. It's a bit unsatisfying though not to understand what's really going on here.

Regards,
feffer

---

