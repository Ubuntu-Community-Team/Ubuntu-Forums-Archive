---
title: "How to share SMB autofs mount with two different users ?"
date: 2020-06-03
forum: General Help
---

### Post by georgesgiralt on 2020-06-03
Hello,
My wife and I share the same computer. (Two different graphical sessions).
I have the automounter set up to mount others computer's home directories using NFS V4 and, once mounted, each directory can only be accessed by it's legitimate owner. So fine, so good.
But we also have a NAS with an SMB share on it for files we like to share (music, pictures, you name it). I use this line to mount the share using an indirect map :
```

disk -fstype=cifs,dir_mode=777,rw,vers=1.0,username=NASUSER,password=NASPASSWD,gid=users,uid=$USER ://NAS/disk

```
It works fine and the directory where the nas will be mounted has the following permissions when I use the user "georges" to mount it :
```

drwxr-xr-x 7 georges users 0 juin   3 11:19 disk

```
And here lies the problem. People in the users group can't create or delete files on the disk directory, and I can't find the way to tell the automounter or the CIFS mount tool to make the disk directory accessible to the people in the users group in writing. 
So I would very much like to get your help on this matter !
Many thanks in advance for your help
And stay safe !

---

### Post by Morbius1 on 2020-06-03
I'm surprised you didn't get an error when you tested this out.

CIFS is kinda persnickety when it comes to how you define dir_mode. It has to be preceded by a 0 ( zero ) in order for it to be recognized as an octal value:
> disk -fstype=cifs,[COLOR=#ff0000]**dir_mode=0777**[/COLOR],rw,vers=1.0,username=NASUSER,password=NASPASSWD,gid=users,uid=$USER ://NAS/disk

You may want to add the corresponding file_mode setting in there as well: [B]file_mode=0666

*EDIT*[/B][I]: The more I look at your post you may need one more option: **nounix **No need to add it if it works without it.

**Also note**: If you really are trying to restrict access to members of the users group you need to drop the last 7: **dir_mode=0770**
[/I]

---

### Post by georgesgiralt on 2020-06-03
Hello,
Thank you for your answer, but if I'm not mistaken, the dir_mode and file_mode flags are only here to set the proper permissions ON the nas, and not on the Ubuntu box. The dir_mode flag works flawlessly on my nas so it seems to be understood by the cifs mount software.
What I'm trying to do is having the ubuntu mount point /nas/disk writeable by members of the group users; And I can't find a solution for this.

---

### Post by TheFu on 2020-06-03
If both usernames are in the "users" Unix group, then you can restrict the file and directory access as:[B]
dir_mode=0775,file_mode=0664[/B]

I see Morbius has the more restrictive dir_mode=0770 too. That would prevent anyone not in the "users" group from having access and a better idea if you don't have services like a plex media center or some music streaming service on the LAN so you both listen to the same stuff.

If the NAS supports NFS, perhaps using that instead of samba would be useful?

---

### Post by georgesgiralt on 2020-06-03
Hello,
Problem is not on the NAS machine. Problem is on the UBUNTU machine. The directory has rwxr-xr-x permission and I would like rwxrwxr-x. This is my question.

---

### Post by TheFu on 2020-06-03
> **georgesgiralt said:**
> Hello,
Problem is not on the NAS machine. Problem is on the UBUNTU machine. The directory has rwxr-xr-x permission and I would like rwxrwxr-x. This is my question.

And the file and directory options provided by both myself and Morbius addresses that.

---

### Post by TheFu on 2020-06-03
> **georgesgiralt said:**
> Hello,
Thank you for your answer, but if I'm not mistaken, the dir_mode and file_mode flags are only here to set the proper permissions ON the nas, and not on the Ubuntu box.  


This is incorrect.

---

### Post by georgesgiralt on 2020-06-03
Sorry, but i may have made something wrong. 
Here are the results of your suggestions with, of course, the autofs daemon running in debug mode :
```

master_do_mount: mounting /NAS
automount_path_to_fifo: fifo name /var/run/autofs.fifo-NAS
lookup_nss_read_map: reading map file /etc/auto.NAS
do_init: parse(sun): init gathered global options: (null)
remount_active_mount: trying to re-connect to mount /NAS
mounted indirect on /NAS with timeout 30, freq 8 seconds
remount_active_mount: re-connected to mount /NAS
st_ready: st_ready(): state = 0 path /NAS
ghosting enabled
handle_packet: type = 3
handle_packet_missing_indirect: token 247, name disk, request pid 172130
attempting to mount entry /NAS/disk
lookup_mount: lookup(file): looking up disk
lookup_mount: lookup(file): disk -> -fstype=cifs,dir_mode=0775,file_mode=0664,rw,vers=1.0,username=nasuser,password=naspasswd,gid=users,uid=$USER ://NAS/disk
parse_mount: parse(sun): expanded entry: -fstype=cifs,dir_mode=0775,file_mode=0664,rw,vers=1.0,username=nasuser,password=naspasswd,gid=users,uid=georges ://NAS/disk
parse_mount: parse(sun): gathered options: fstype=cifs,dir_mode=0775,file_mode=0664,rw,vers=1.0,username=nasuser,password=naspasswd,gid=users,uid=georges
parse_mount: parse(sun): dequote("://NAS/disk") -> ://NAS/disk
parse_mount: parse(sun): core of entry: options=fstype=cifs,dir_mode=0775,file_mode=0664,rw,vers=1.0,username=nasuser,password=naspasswd,gid=users,uid=georges, loc=://NAS/disk dur
sun_mount: parse(sun): mounting root /NAS, mountpoint disk, what //NAS/disk dur, fstype cifs, options dir_mode=0775,file_mode=0664,rw,vers=1.0,username=nasuser,password=naspasswd,gid=users,uid=georges
do_mount: //NAS/disk dur /NAS/disk type cifs options dir_mode=0775,file_mode=0664,rw,vers=1.0,username=nasuser,password=naspasswd,gid=users,uid=georges using module generic
mount_mount: mount(generic): calling mkdir_path /NAS/disk
mount(generic): calling mount -t cifs -o dir_mode=0775,file_mode=0664,rw,vers=1.0,username=nasuser,password=naspasswd,gid=users,uid=georges //NAS/disk  /NAS/disk
mount_mount: mount(generic): mounted //NAS/disk type cifs on /NAS/disk
dev_ioctl_send_ready: token = 247
mounted /NAS/disk

```
And here is the result on the mount point on the Ubuntu machine : 
```

drwxr-xr-x  8 georges users    0 juin   3 13:08 disk

```
So what did I did wrong ? 
Thank you for your help.

---

### Post by TheFu on 2020-06-03
After making the changes, did you remember to restart autofs service? Looks like the debug has the expected options, so yes seems correct.
```
sudo service autofs restart
```

if that doesn't fix it, for more troubleshooting, let's simplify.

Stop autofs.
Try manually mounting.
```
sudo service autofs stop
sudo mkdir /mnt/disk
sudo mount -t cifs   //NAS/disk    /mnt/disk   dir_mode=0775,file_mode=0664,rw,vers=1.0,username=nasuser,password=naspasswd,gid=users,uid=$USER 
```
Does autofs support $USER?  it runs as root, so i wouldn't expect that variable to be set or set correctly.    The mount.cifs manpage:
```
       uid=arg
           sets the uid that will own all files or directories on the mounted
           filesystem when the server does not provide ownership information.
           It may be specified as either a username or a numeric uid. When not
           specified, the default is uid 0. The mount.cifs helper must be at
           version 1.10 or higher to support specifying the uid in non-numeric
           form. See the section on FILE AND DIRECTORY OWNERSHIP AND
           PERMISSIONS below for more information.
...
ENVIRONMENT VARIABLES
       The variable USER may contain the username of the person to be used to
       authenticate to the server. The variable can be used to set both
       username and password by using the format username%password.

```
USER would work for a mount on the command line. i still have doubts about it working on a mount post-boot. Maybe it works fine.  idk.  Something that I&#8217;d check. Again, the debug output has the username, so that seems to be working too.

Here's my autofs line that connects to a share on win7ult:
```
win7ult  -fstype=cifs,sec=ntlmv2,iocharset=utf8,rw,vers=2.1,uid=thefu,gid=plex,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials  ://172.22.22.8/Data
```

The resulting permissions:
```
drwxrwxr-x 2 thefu   plex         8192 Nov  2  2019 ./
```
i put the Windows login credentials into a root 600 file for better security.

All this make me thing there is a NAS server setting getting in the way.

---

### Post by georgesgiralt on 2020-06-03
Hello,
If you check carefully, the directory mount point size is 8192 in your case meaning that the directory was existing prior to the mount.
In the case of the autofs mount, the mount point does not exist BEFORE the mount takes place. This is why the size of my directory is 0. 
As the directory is not existing I can't change it's permission. And yes, the $USER directive is working fine because the directory has no prior existence on the filesystem.
To clarify things, on a terminal, using root identity, i do this : 
```

#systemctl stop autofs.service
# umount /NAS/disk
# ll /NAS/
total 8
drwxr-xr-x  2 root root 4096 juin   3 11:40 ./
drwxr-xr-x 22 root root 4096 juin   3 17:39 ../
# automount -f -v -d       <------- this is to get as much debug information as I could

```
Then on another terminal, using "georges" account : 
```

georges@isengrin:~$ ll /NAS
total 0
drwxr-xr-x 2 root root 0 juin   3 16:10 disk
georges@isengrin:~$ cd /NAS/disk
georges@isengrin:/NAS/disk$ ll ..
total 0
drwxr-xr-x 8 georges users 0 juin   3 17:39 disk
georges@isengrin:/NAS/disk$ ls 
...... output omitted but files present.....

```
As you can see, the disk directory is owned by root and switch to "georges:users" once the automounter has made it's trick.
BTW, I run Ubuntu 20.04 LTS and Ubuntu 18.04LTS on those machines.

---

### Post by TheFu on 2020-06-03
If both machines are Ubuntu, why not use NFSv4?  Then you'd have native Unix permissions and probably a little better performance.  

Also the vers=1.0 can be removed. Let samba on both sides negotiate the best version if you don't want to change to NFS.

---

### Post by georgesgiralt on 2020-06-03
Sorry, I *should* have written "the two client machines run Ubuntu 18.04LTS and Ubuntu 20.04LTS to mount a network NAS " I promise, I wont' do 3 things at the same time and answer the missus ;-)
Frankly, if i could use NFS (either version) I would gladly dump this s...

---

### Post by Morbius1 on 2020-06-03
Looks like you didn't do this:
> ***EDIT****: The more I look at your post you may need one more option: **nounix **No need to add it if it works without it.*
I don't know where you are at the moment -- too many posts - but something like this:
> disk -fstype=cifs,dir_mode=0770,file_mode=0660[COLOR=#ff0000]**,nounix**[/COLOR],rw,vers=1.0,username=NASUSER,password=NASPASSWD,gid=users,uid=$USER ://NAS/disk

---

### Post by georgesgiralt on 2020-06-03
Will try right now and report back.

---

### Post by georgesgiralt on 2020-06-03
Hurrah !
That did it ! this is the line I have in my automount map :
```

disk    -fstype=cifs,dir_mode=0775,file_mode=0664,rw,vers=1.0,nounix,username=nasuser,password=naspasswd,gid=users,uid=$USER ://NAS/disk

```
and this is what I get :
```

$ll /NAs
total 0
drwxr-xr-x 2 root root 0 juin   3 18:36 disk
$ cd /NAS/disk/
$ ll ..
total 0
drwxrwxr-x 2 georges users 0 juin   3 13:08 disk
$

```
Thank you !
I'll mark the thread as resolved in order for others to profit of your knowledge !
Have a nice day !

---

