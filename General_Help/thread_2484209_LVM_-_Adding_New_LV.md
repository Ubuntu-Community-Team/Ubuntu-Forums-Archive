---
title: "LVM - Adding New LV"
date: 2023-02-20
forum: General Help
---

### Post by Quarkrad on 2023-02-20
I've created three LVs in a vm, all ext4.  One is called root where I have installed **/**, one is called home where I've installed **/home** and another called *workspace.*  For some reason I cannot create a folder or document in *workspace* (options greyed out in file manager) - I've obviously done something wrong (I can create/delete in **/** and **/home**).  I used some commands to look at the free space and only partial information appears for *workspace*. Appreciate any advice on where I've gone wrong.

```
dad@dadubuntu:~$ LC_ALL=C df -hP | column -t
Filesystem             Size  Used  Avail  Use%  Mounted         on
tmpfs                  393M  1.4M  392M   1%    /run            
/dev/mapper/vg01-root  25G   8.8G  15G    38%   /               
tmpfs                  2.0G  0     2.0G   0%    /dev/shm        
tmpfs                  5.0M  4.0K  5.0M   1%    /run/lock       
/dev/vda1              119M  6.1M  113M   6%    /boot/efi       
/dev/mapper/vg01-home  30G   118M  28G    1%    /home           
tmpfs                  393M  124K  393M   1%    /run/user/1000  
dad@dadubuntu:~$ 

```


```
dad@dadubuntu:~$ lsblk -ao NAME,FSTYPE,FSSIZE,FSUSED,FSUSE%
NAME               FSTYPE      FSSIZE FSUSED FSUSE%
loop0              squashfs      128K   128K   100%
loop1              squashfs       62M    62M   100%
loop2              squashfs     63.4M  63.4M   100%
loop3              squashfs    163.4M 163.4M   100%
loop4              squashfs    400.9M 400.9M   100%
loop5              squashfs    346.4M 346.4M   100%
loop6              squashfs     91.8M  91.8M   100%
loop7              squashfs     49.9M  49.9M   100%
loop8              squashfs      384K   384K   100%
loop9              squashfs      384K   384K   100%
loop10             squashfs      128K   128K   100%
loop11             squashfs     13.6M  13.6M   100%
loop12             squashfs     13.6M  13.6M   100%
loop13                                       
vda                                          
&#9500;&#9472;vda1             vfat        118.1M     6M     5%
&#9492;&#9472;vda2             LVM2_member               
  &#9500;&#9472;vg01-root      ext4         24.4G   8.8G    36%
  &#9500;&#9472;vg01-home      ext4         29.4G 117.4M     0%
  &#9492;&#9472;vg01-workspace ext4 
  
```

```
 dad@dadubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vg01-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/vda1 during installation
UUID=D4D0-38D1  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vg01-home /home           ext4    defaults        0       2
/dev/mapper/vg01-workspace   /media/dad/workspace         ext4    defaults  0       2
```

---

### Post by TheFu on 2023-02-20
sudo lvs
Did you run mkfs on workspace?
Does the /dev/mapper/vg01-workspace device file exist?  Can you manually mount it?
Is there a reason you didn't also create a swap LV?  

Please save and use these aliases for df and lsblk commands:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'

```
so we don't ever have to see cruft.

---

### Post by Dennis N on 2023-02-20
Check who is the owner of the mount folder /media/dad/workspace.
I use a subfolder of /mnt for my data partition mount point and I know that after creation, it's necessary to change the owner of the mount point to access it.

---

### Post by MAFoElffen on 2023-02-20
+1 with Dennis N.

I would suspect ownership, group permissions and access.

With whatever Filesystem Manager I use, if I create or mount a data area outside of home, I set ownership, then set group permissions to folders within that... Then set users as members of those group(s).

Otherwise, when you check (at first), you will most likely find that it is owned by root, and would need root permissions to access. (Until changed)

---

### Post by TheFu on 2023-02-20
The "workspace" isn't being mounted, so it isn't permissions.  It is something upstream before that, which is why I requested to see the lvs and lsblk output without cruft along with a manual mount command, which will likely tell exactly what the issue is.  

I suspect the workspace LV was created, but no file system was placed onto it, but we need confirmation.  When doing things over and over and over, it is easy to forget 1 step for 1 of the LVs.

After that, is addressed, permissions would matter.

---

### Post by MAFoElffen on 2023-02-20
@TheFu -

LOL. Dang. True.

I saw it in his fstab to be mounted, but missed that it isn't showing up in his 'df' output as actually being mounted... My oversight.

---

### Post by Quarkrad on 2023-02-20
Doh .....  Thank you all.  Guess I should have thought of that (it was the permission) as all the LVM commands I've used so far have been preceded by sudo.

---

### Post by Quarkrad on 2023-02-20
Forgot to answer @TheFu question.  I have not created a lv for swap as I'm experimenting with lvm in a vm.  When I migrate to LVM to my live environment I will certainly have lv for swap.  I've never had a separate location for /var and I can see the logic when in a server environment from what I have read many times. Most examples quote run-away log files.  However, due to my in-experience, I'm not sure if I need a separate /var lv for my stand-alone Desktop machine.

---

### Post by TheFu on 2023-02-21
> **Quarkrad said:**
> Doh .....  Thank you all.  Guess I should have thought of that (it was the permission) as all the LVM commands I've used so far have been preceded by sudo.

So it is mounting now?  Was the missing file system the issue?

---

### Post by Quarkrad on 2023-02-23
Re: the file system no, it was formatted as ext4.  I checked the ownership of *workspace *and it was root.  Once I changed it back to myself all was fine.

---

### Post by TheFu on 2023-02-23
> **Quarkrad said:**
> Re: the file system no, it was formatted as ext4.  I checked the ownership of *workspace *and it was root.  Once I changed it back to myself all was fine.

Permissions wouldn't prevent it from mounting.  It was something else.

---

### Post by MAFoElffen on 2023-02-23
From post #1, reposted to clear up things and provide and explanation for others, reading this for later on...
> **Quarkrad said:**
> I've created three LVs in a vm, all ext4.  One is called root where I have installed **/**, one is called home where I've installed **/home** and another called *[COLOR=#ff0000]workspace[/COLOR].*  [COLOR=#ff0000]For some reason I cannot create a folder or document in *workspace* (options greyed out in file manager)[/COLOR] - I've obviously done something wrong (I can create/delete in **/** and **/home**).  I used some commands to look at the free space and [COLOR=#ff0000]only partial information appears for *workspace*.[/COLOR] Appreciate any advice on where I've gone wrong.

```
dad@dadubuntu:~$ LC_ALL=C df -hP | column -t
Filesystem             Size  Used  Avail  Use%  Mounted         on
tmpfs                  393M  1.4M  392M   1%    /run            
/dev/mapper/vg01-root  25G   8.8G  15G    38%   /               
tmpfs                  2.0G  0     2.0G   0%    /dev/shm        
tmpfs                  5.0M  4.0K  5.0M   1%    /run/lock       
/dev/vda1              119M  6.1M  113M   6%    /boot/efi       
/dev/mapper/vg01-home  30G   118M  28G    1%    /home           
tmpfs                  393M  124K  393M   1%    /run/user/1000  
dad@dadubuntu:~$ 

```


```
dad@dadubuntu:~$ lsblk -ao NAME,FSTYPE,FSSIZE,FSUSED,FSUSE%
NAME               FSTYPE      FSSIZE FSUSED FSUSE%
loop0              squashfs      128K   128K   100%
loop1              squashfs       62M    62M   100%
loop2              squashfs     63.4M  63.4M   100%
loop3              squashfs    163.4M 163.4M   100%
loop4              squashfs    400.9M 400.9M   100%
loop5              squashfs    346.4M 346.4M   100%
loop6              squashfs     91.8M  91.8M   100%
loop7              squashfs     49.9M  49.9M   100%
loop8              squashfs      384K   384K   100%
loop9              squashfs      384K   384K   100%
loop10             squashfs      128K   128K   100%
loop11             squashfs     13.6M  13.6M   100%
loop12             squashfs     13.6M  13.6M   100%
loop13                                       
vda                                          
&#9500;&#9472;vda1             vfat        118.1M     6M     5%
&#9492;&#9472;vda2             LVM2_member               
  &#9500;&#9472;vg01-root      ext4         24.4G   8.8G    36%
  &#9500;&#9472;vg01-home      ext4         29.4G 117.4M     0%
  &#9492;&#9472;vg01-workspace ext4 
  
```

```
 dad@dadubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vg01-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/vda1 during installation
UUID=D4D0-38D1  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vg01-home /home           ext4    defaults        0       2
[COLOR=#ff0000]/dev/mapper/vg01-workspace   /media/dad/workspace         ext4    defaults  0       2[/COLOR]
```
@TheFu --

He has able to access the mount (it was mounting), but could not do anything in it (because of ownership and permissions).

I guess if he had showed us the output from 'mount', it would have showed us that it was successfully mounted, but that wasn't one of his outputs that he provided... 

True, if it didn't have a filesystem, it would not have mounted... But if was mounting. (He could access the mount itself.)

As he said, he could access the mount, but he could not create a folder or document inside the mounted storage... Until he changed ownership of the mounted storage from root to himself. Once he was the owner, he had permissions to do anything he wanted on that mounted storage... He could have also done that in the mount in his fstab (setting uid/gid), but the fstab line was basic/generic.

I do things a bit different, I set mounted storage ownership/permissions to "a group", instead of just an individual, that way it is multi-user access/permissions, instead of just to single individuals (which still works). That way if another person needs access/permissions, all you have to do is make that person a member of that group, resulting in shared storage. Same answer, different methodology.

---

### Post by TheFu on 2023-02-24
'df' output does show mounted storage and since "workspace" isn't there, I decided the mount wasn't working.
The lack of file system information in lsblk output is why I decided a possible cause was that no file system was created.

Details matter ... for posting information AND for interpreting it.  Bad inputs == bad outputs.

---

