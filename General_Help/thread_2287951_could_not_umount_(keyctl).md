---
title: "could not umount (keyctl)"
date: 2015-07-23
forum: General Help
---

### Post by Drenriza on 2015-07-23
Hi all

I am getting an error i don't fully understand and i cant seem to find a solution on Google

> user@user-machine:~$ sudo umount ~/Desktop/mnt1/
Could not unlink the key(s) from your keying. Please use `keyctl unlink` if you wish to remove the key(s). Proceeding with umount.
umount: /home/user/Desktop/mnt1/: not mounted

Anyone who knows what the system is trying to tell me?

Thanks on advance
Kind regards

---

### Post by dino99 on 2015-07-23
ok, you want to unmont "sudo umount ~/Desktop/mnt1/".
so the comment tell you to run "keyctl unlink" (which you have not done  ;)
and finally the system answer: "/home/user/Desktop/mnt1/: not mounted"

That is: you want to unmount something that is not mounted ;) ;)

if your main trouble concern English understanding, then chromium-browser can auto-translate to your local language, or use translate.google.com.

---

### Post by Drenriza on 2015-07-23
> **dino99 said:**
> ok, you want to unmont "sudo umount ~/Desktop/mnt1/".
so the comment tell you to run "keyctl unlink" (which you have not done  ;)
and finally the system answer: "/home/user/Desktop/mnt1/: not mounted"

That is: you want to unmount something that is not mounted ;) ;)

if your main trouble concern English understanding, then chromium-browser can auto-translate to your local language, or use translate.google.com.

Thanks for your reply @Dino

The thing is, that if i run
```
df -h
```
it displays the ~/Desktop/mnt as mounted. If i try to mount it again while df displays it as mounted than nothing happends.
If i try to unmount it i get above error.

---

### Post by bab1 on 2015-07-23
> **Drenriza said:**
> ...

The thing is, that if i run
```
df -h
```
it displays the ~/Desktop/mnt as mounted. If i try to mount it again while df displays it as mounted than nothing happends.
If i try to unmount it i get above error.
When you use sudo you are asking for the root user to un-mount the partition.  Your command actually is asking root to un-mount the partition in the user root's home directory (e.g sudo umount ~/).  There is no way for root to expand ~ to your home directory.  The symbol ~ means the users (in this case root) home directory.

Rather than just giving us the command you used such as ***df -h***, you might post the results so we can see what you have.

In the end you should define the path to the partition explicitly with a command like this ```
sudo umount  /home/<user>/Desktop/mnt1
```
...rather than using the shortcut to home (~).  The <user> should be the user in the path to the mount point.

---

### Post by bab1 on 2015-07-23
> **dino99 said:**
> ok, you want to unmont "sudo umount ~/Desktop/mnt1/".
Not really.  The command is asking for something different than what the OP intended.  See my comments in the previous post.
> 

so the comment tell you to run "keyctl unlink" (which you have not done  ;)
and finally the system answer: "/home/user/Desktop/mnt1/: not mounted"

That is: you want to unmount something that is not mounted ;) ;)
It may well be that the OP has also not defined the location of the mount point correctly.  We don't know that by the information that has been supplied so far.> 
if your main trouble concern English understanding, then chromium-browser can auto-translate to your local language, or use translate.google.com.
I think the problem is not language, but rather, understanding of how sudo really works.

---

### Post by Drenriza on 2015-07-23
> **bab1 said:**
> When you use sudo you are asking for the root user to un-mount the partition.  Your command actually is asking root to un-mount the partition in the user root's home directory (e.g sudo umount ~/).  There is no way for root to expand ~ to your home directory.  The symbol ~ means the users (in this case root) home directory.

Rather than just giving us the command you used such as ***df -h***, you might post the results so we can see what you have.

In the end you should define the path to the partition explicitly with a command like this ```
sudo umount  /home/<user>/Desktop/mnt1
```
...rather than using the shortcut to home (~).  The <user> should be the user in the path to the mount point.

uhmm yes that actually makes sense about ~ with sudo says the root users. Since its barrowing super user privilegies for that command.
Dont know why i didnt think of that, long day :)

> I think the problem is not language, but rather, understanding of how sudo really works.
smile and wave, smile and wave.
Your always allowed to learn from mistakes :D

> It may well be that the OP has also not defined the location of the  mount point correctly.  We don't know that by the information that has  been supplied so far.
True the information was scarse, but i didnt understand the problem at the time. And im not a 100% i do now since the ketctl error is new to me.
Even though i tried and umount it incorrectly. But the problem persists even when i do the full path of /home/user/Desktop/mount-point

I mount it with

/etc/fstab
```

//ip-address/samba-share /home/user/Desktop/mount-point cifs credentials=/root/.smbcredentials,uid=1000,gid=1000 0 0

```

---

### Post by bab1 on 2015-07-23
> **Drenriza said:**
> uhmm yes that actually makes sense about ~ with sudo says the root users. Since its barrowing super user privilegies for that command.
Dont know why i didnt think of that, long day :)
It is not borrowing super user privileges.  The command is **[SIZE=3]S[/SIZE]**witch **[SIZE=3]U[/SIZE]**ser and **[SIZE=3]DO[/SIZE]**.  So we switch to the user root and do the command if we do not define the user.  If sudo is set up for it, you can do this```

sudo Drenriza <some_command> 
```

From the sudo man page```
sudo, sudoedit — execute a command as another user
```

---

### Post by bab1 on 2015-07-23
> **Drenriza said:**
> uhmm yes that actually makes sense about ~ with sudo says the root users. Since its barrowing super user privilegies for that command.
Dont know why i didnt think of that, long day :)


smile and wave, smile and wave.
Your always allowed to learn from mistakes :D


True the information was scarse, but i didnt understand the problem at the time. And im not a 100% i do now since the ketctl error is new to me.
Even though i tried and umount it incorrectly. But the problem persists even when i do the full path of /home/user/Desktop/mount-point

I mount it with

/etc/fstab
```

//ip-address/samba-share /home/user/Desktop/mount-point cifs credentials=/root/.smbcredentials,uid=1000,gid=1000 0 0

```

The comments were for @ dino99.  You don't have to defend yourself.

It would be nice to see the output of ```
df -h
```.... and also ```
mount 
```

What is the exact command you used and what errors (exactly) did you get?  Post the output from the terminal back here.  The command umount should work anywhere unless you have an encrypted partition or some other security settings.

---

### Post by Drenriza on 2015-07-24
Thanks for all the replies @bab1 and @dino99

> The comments were for @ dino99.  You don't have to defend yourself.
Thanks @bab1 But i don't at all feel like i am defending myself :)

df -h output
> 
//samba-share/share1     458G   15G  421G   4% /home/user/Desktop/mount-point
//samba-share/share2   458G   15G  421G   4% /home/user/Desktop/mount-point


mount output
> 
//samba-share/share1 on /home/user/Desktop/mount-point type cifs (rw,relatime,vers=1.0,cache=strict,username=user,domain=Domain,uid=1000,forceuid,gid=1000,forcegid,addr=ip,file_mode=0755,dir_mode=0755,nounix,serverino,rsize=61440,wsize=65536,actimeo=1)
//samba-share/share2 on /home/user/Desktop/mount-point type cifs (rw,relatime,vers=1.0,cache=strict,username=user,domain=Domain,uid=1000,forceuid,gid=1000,forcegid,addr=ip,file_mode=0755,dir_mode=0755,nounix,serverino,rsize=61440,wsize=65536,actimeo=1)
//samba-share/share3 on /home/user/Desktop/mount-point type cifs (rw,relatime,vers=1.0,cache=strict,username=user,domain=Domain,uid=1000,forceuid,gid=1000,forcegid,addr=ip,file_mode=0755,dir_mode=0755,nounix,serverino,rsize=61440,wsize=65536,actimeo=1)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1199724k,mode=700,uid=1000,gid=1000)


My /etc/fstab is as follows
```

//ip-address/samba-share /home/user/Desktop/mount-point cifs credentials=/root/.smbcredentials,uid=1000,gid=1000 0 0

```

I see the error on my system when navigating to /home/user/Desktop/any-share
and see it being empty.

df -h and mount than looks as above.

Attempt 1
```
umount /home/user/Desktop/mount-point
```
it says
> umount: /home/user/Desktop/mount-point: umount failed: Operation not permitted

Attempt 2
```
sudo umount /home/user/Desktop/mount-point
```
it says
> Could not unlink the key(s) from your keying. Please use `keyctl unlink` if you wish to remove the key(s). Proceeding with umount.
umount: /home/user/Desktop/mount-point: not mounted

---

### Post by bab1 on 2015-07-24
> **Drenriza said:**
> 
```
Could not unlink the key(s) from your keying. Please use `keyctl unlink` if you wish to remove the key(s). Proceeding with umount.
umount: /home/user/Desktop/mount-point: not mounted 
```

This does not appear to be a sudo problem or a mount/umount problem at all.  I have no definitive answer for you.  Google searches indicate that it involves encrypted volumes.

---

