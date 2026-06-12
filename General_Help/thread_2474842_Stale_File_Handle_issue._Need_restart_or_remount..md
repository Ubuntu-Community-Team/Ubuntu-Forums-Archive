---
title: "Stale File Handle issue. Need restart or remount."
date: 2022-05-09
forum: General Help
---

### Post by herculpirate on 2022-05-09
I have a synology server and an unraid server
I have created a map network drive under /media for both of them using this methodology:
[https://ubuntuhandbook.org/index.php/20 ... ntu-14-04/]("https://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/")

But after a while, I cannot access the unraid server but Synology server is accessible.
Also the dir created under /media/UnraidServer does not show and I try  to access the server via the bookmark that I created, it gives me this  error

[https://pasteboard.co/oJrVgWAWQBd5.png](https://pasteboard.co/oJrVgWAWQBd5.png)
[IMG]https://pasteboard.co/oJrVgWAWQBd5.png[/IMG]

If I do a restart or if I run the following commands, it comes back again
```
sudo unmount -f /media/share
sudo mount -a
```

How can I prevent this Stale File Error.

---

### Post by yancek on 2022-05-10
I'm not sure I understand your setup.  Could you post the full path to both UnRaid Server and Synology?  You indicate they are both mounted under /media but the mount command you use shows /media/share.  Are their mount points under /media/share?:

```
 sudo unmount -f /media/share sudo mount -a
```

The link below to Stack Exchange has a description of the problem and 
a solution so you might check that out.

[https://stackoverflow.com/questions/20105260/what-does-stale-file-handle-in-linux-mean](https://stackoverflow.com/questions/20105260/what-does-stale-file-handle-in-linux-mean)

---

### Post by herculpirate on 2022-05-10
@yancek

The path to the servers are

```

/media/UnraidServer
/media/Synology

```


I am now trying to move the contents from my Synology moved over to Unraid. I am doing this via my docker container "Krusader"
But on my personal Linux Mint laptop, I have created a map network drive at the paths shown.

But after sometime, the UNRAID gives me the "Stale file Handle" error.

Not sure if its a UNRAID issue or LINUX issue.

---

### Post by herculpirate on 2022-05-10
@yancek

There is no solution in that post.
I know by unmounting and remounting works (sometimes)
is there another option ?

---

### Post by #&amp;thj^% on 2022-05-10
> **herculpirate said:**
> @yancek

There is no solution in that post.
I know by unmounting and remounting works (sometimes)
is there another option ?

A buddy of mine called with something very close to your problem.
after hours and hours, The  Key is to add **"noserverino"** to mount flags. This forces client to generate its own inode codes rather than using server one. 
Hope it works for you as well
EDIT: to be clear, These are used by "fstab" in "/etc/fstab" 
if your setup is different a one-line EXAMPLE ONLY
```
//192.168.1.20/sharename   /mnt/sharename  cifs    rw,_netdev,noserverino,uid=MYLOCALUSERNAME,gid=users,credentials=/etc/samba/credentials/MYLOCALUSERNAME,file_mode=0666,dir_mode=0777      0       0
```

---

### Post by yancek on 2022-05-10
The link was meant to give an explanation of the reason for the error.  Read through it to see if you have done anything mentioned in that link.

I don't know if it matters but the link at StackOverflow discusses nfs while you are using Samba.  I wouldn't think it would matter but I don't know having never used samba.

I don't understand how the command umount /media/share can unmount /media/unraid and /media/Synology.  

I'd try the solution proposed by 1fallen above.

---

### Post by herculpirate on 2022-05-10
Thank you @yancek
My mistake, I meant to say
```

sudo unmount -f /media/UnraidServer

```

I have tried @1fallen 's solution
```

//192.168.1.20/sharename   /mnt/sharename samba    rw,_netdev,noserverino,uid=MYLOCALUSERNAME,gid=users,credentials=/etc/samba/credentials/MYLOCALUSERNAME,file_mode=0666,dir_mode=0777      0       0

```
The only change I made is "samba" instead of "cifs"

I will report back. Not sure if I have to restart or 
```

sudo mount -a

```
Should work.

---

### Post by TheFu on 2022-05-10
"samba" isn't a valid type of remote mount. "cifs" is.

Doesn't unraid support NFS?  That's the native file system for Unix-like system to use. It happens to be faster than CIFS and supports native Unix permissions.

Win-Win!

---

### Post by #&amp;thj^% on 2022-05-11
> **TheFu said:**
> "samba" isn't a valid type of remote mount. "cifs" is.

Doesn't unraid support NFS?  That's the native file system for Unix-like system to use. It happens to be faster than CIFS and supports native Unix permissions.

Win-Win!

+1 my friend was the same, I'm not sure why samba is a first choice? 
@ herculpirate I really like the TheFu's suggestion.
Quote from the Unraid forum. 
> I believe adding support for more recent NFS versions is important because it is likely to resolve many of the problems we see with NFS here on the forum (especially the NFS "stale file handle" errors). I think that's why we also keep seeing this request come up over and over again.

 His reply

> I understand where Tom is coming from when he says, "Seriously, what is the advantage of NFS over SMB?"
You do a lot of short/random-read/write-like file operations: NFS tends to perform better than Microsoft's SMB here. As you deal with larger files and get more into sequential IO performance territory, though, the advantage between NFS and SMB blurs. Reference: [https://www.rootusers.com/windows-nfs-vs-linux-nfs-performance-comparison/](https://www.rootusers.com/windows-nfs-vs-linux-nfs-performance-comparison/)

---

### Post by herculpirate on 2022-05-11
Thank you.
Let me try with NFS and the noserverino

```

//192.168.1.20/sharename   /mnt/sharename nfs    rw,_netdev,noserverino,uid=MYLOCALUSERNAME,gid=users,credentials=/etc/samba/credentials/MYLOCALUSERNAME,file_mode=0666,dir_mode=0777      0       0

```

I will have to restart I suppose. 
Does 
```
sudo mount -a
```
work ?

---

### Post by herculpirate on 2022-05-11
I am assuming the format to mount the NFS shares is different than the above.
What is the NFS equivalent to the below line in the /etc/fstab file that references my server credentials.

```

//10.0.0.123/Share /media/SynologyServer cifs credentials=/home/user/.credentials,noserverino,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0

```

Help please.

---

### Post by herculpirate on 2022-05-11
The following link is great guide.

[http://manpages.ubuntu.com/manpages/bionic/man5/nfs.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/nfs.5.html)

Can someone help me with the reference to credentials and options bit:

```
10.0.0.123:share   /media/SynologyServer nfs  option,option,...   0 0
```

---

### Post by herculpirate on 2022-05-11
I tried the following
```

10.0.0.123:/share /media/SynologyServer nfs username=admin,password=pass,noserverino,hard,timeo=200,rsize=4096,wsize=4096 0 0

```


Error I got after I did 

```

USER@WorkStation:~$ sudo mount -a
mount.nfs: an incorrect mount option was specified

```

---

### Post by TheFu on 2022-05-12
NFS isn't user-to-server authentication like CIFS. It is server-to-server, meaning the admin of both machines has to allow the other access. Any changes of file/directory owners needs to happen on the system where the storage is physically installed.  I.e. root on the NFS client doesn't get any priviledges to the storage.  

From the NFS client, you can ask the NFS server about shared storage.
```
showmount -e 10.0.0.123
```

It uses the userids on both systems ( 'id' command).  Those numbers need to match between the NFS client and the NFS server.
Try:
```
10.0.0.123:/Share     /media/SynologyServer   nfs   defaults   0 0
```


but you should probably read the Synology NFS how-to, since the Synology will likely need a few settings configured. Perhaps userids?
Since NFS uses native Unix permissions, you'll need to become comfortable with those, if you aren't already.  chmod, chown.

---

### Post by herculpirate on 2022-05-12
@TheFu

The showmount told me that I am sharing my media drive.
When I used your ```
10.0.0.123:/Share     /media/SynologyServer   nfs   defaults   0 0
```
The result was that it was asking for credentials.

The id on my server is UID=1000, GID=100
The id on my Desktop is UID=1000, GID=1000

How do I pass the authentication in the /etc/fstab ?

---

### Post by TheFu on 2022-05-12
Please post the showmount ... command and output.

It is best if you show exact commands AND the output from those commands, if they don't work.  Lets misinterpretation that way. Plus, we all make tiny mistakes that another eyeball can often see.

NFS uses server-to-server authentication, but only if the NFS server is configured for Kerberos, KDC.  You'd know if that was the situation, since it is non-trivial to setup and most cheap NAS devices don't support it.  I don't know about Synology models.  Kerberos doesn't passes tokens using the Kerberos protocol, not part of the NFS mount.  If you google "ubuntu nfs kerberos", there is a guide at help.ubuntu.com.  I don't run Kerberos at home. Seems like overkill there.  My NFS mounts look like I posted.  The IP of the server in the client fstab and in the server /etc/exports specifically listing the IP/DNS-hostname of the client on the line for each share to be served, along with the correct uid/gid are it.

In your id post, seems the gid is wrong. They need to match at least 1 of the groups that the userid on the client has, typically the "users" group, or for a single-user LAN, 1000, not 100.

Which exact, release of Ubuntu is being used?  I can't recall, but NFS or CIFS needed some option that was in a link in the 22.04 release notes.  I did test 22.04 as an NFS client connecting to 20.04 and 18.04 NFS servers. Those worked perfectly. Nothing special was needed.  But one of the popular NAS devices needed an option ... think it needed "vers=4.0" as the option, since Ubuntu uses NFS v4.2 and the fallback code wasn't working.  I don't remember if the option was ver[COLOR="#FF0000"]s[/COLOR]= or ver=, sorry.

[https://kb.synology.com/en-us/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://kb.synology.com/en-us/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS) is probably the best source of info for synology.  I couldn't see it.  It is a blank webpage to me, since they require javascript and I don't allow javascript for 99% of the internet.

---

### Post by herculpirate on 2022-05-13
The showmount command from my desktop for my server
```

user@WorkStation:~$ showmount -e 10.0.0.32
Export list for 10.0.0.32:
/mnt/user/media   *
/mnt/user/isos    *
/mnt/user/domains *

```

Regarding UID and GID for my Desktop is as follows:
```

user@WorkStation:~$ id user
uid=1000(user) gid=1000(user) groups=1000(user),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),114(lpadmin),134(sambashare)

```

The UID and GID from the root @ UNRAID 
```

[COLOR=#000000][FONT=Arial]root@Unraid:~# id root
uid=0(root) gid=0(root) groups=0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),17(audio),281(docker)
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
The UID and GID from a account "server_user_id" created on my UNRAID
```

[COLOR=#000000][FONT=Arial]root@Unraid:~# id server_user_id[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
uid=1000([/FONT][/COLOR][COLOR=#000000][FONT=Arial]server_user_id[/FONT][/COLOR][COLOR=#000000][FONT=Arial]) gid=100(users) groups=100(users)[/FONT][/COLOR]

```

---

### Post by TheFu on 2022-05-13
I've never seen a showmount like that.  I'd expect something like this:
```
$ showmount -e romulus
Export list for romulus:
/Data/r2                                 pi3,regulus,hadar,posc
/raid/media/VMs                          hadar
```
Allowing anyone, anywhere access is scary.  Each of the names above are in DNS, but could easily be an IP address instead.  Romulus looks up the names.  Doubt this has anything to do with the issue.  Just general security practice. Don't allow access to any system that doesn't NEED access.

The /etc/exports file on romulus:
```
/Data/r2 pi3(fsid=5,rw,async,no_subtree_check),regulus(fsid=5,rw,async,no_subtree_check),hadar(fsid=5,rw,async,no_subtree_check),posc(fsid=5,rw,async,no_subtree_check)
/raid/media/VMs                          hadar(fsid=6,rw,async,no_subtree_check)
```

The uid and gid from client systems is all that matters. Those need to match the uid/gid on the NFS server, typically.  After all, if they don't then the client users can't manage any NFS storage or change permissions for it.  In theory, idmapd can handle the mapping of userid and groupid between different systems. I've never gotten it to work. Inside enterprises, they use LDAP for user and group management, which ensures those are consistent everywhere. That's usually overkill at home, so we get to manually ensure the uid/gid match on each system.

root has little to do with NFS permissions. It is only useful to manage accounts and storage on the local machine. It cannot modify any NFS storage. I see permission denied errors when using root/sudo on a client to attempt anything on NFS storage. The root account is mapped to nobody on the NFS server.

---

