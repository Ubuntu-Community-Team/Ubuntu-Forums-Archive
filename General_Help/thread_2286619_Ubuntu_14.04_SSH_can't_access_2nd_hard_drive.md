---
title: "Ubuntu 14.04 SSH can't access 2nd hard drive"
date: 2015-07-13
forum: General Help
---

### Post by zoidberg2 on 2015-07-13
I am running Ubuntu 14.04 64 Desktop version & I have a 2[SUP]nd[/SUP] hard drive that the machine recognises & allows me to access the ISOs, other software & multimedia files saved on to it.  
 

 However when I use SSH and remote on to the computer when at work I can initiate an SSH session, log in & view all of the  stuff on the Ubuntu file system but not my additional hard drive. When I try & move to the directory using the correct root, media/john/Media I get a message that I don't have permissions to access the file system.  
 

 Usually I don't need to mount the 2[SUP]nd[/SUP] hard drive it mounts by itself but if I have tried to access it by SSH first before logging in I am then required to mount it when logging on.  
 

 Is there a fix that would allow me to power up the computer, not log in but be able to remote in using SSH that would give me access to the 2[SUP]nd[/SUP] drive?

---

### Post by sudodus on 2015-07-13
If you don't want to mount it manually, you can mount it automatically with an entry for it in /etc/fstab

The syntax will be similar to that of your root file system, and probably similar to my data partition

```
UUID=d3f3f4a3-436e-5r4f-8e1a-d1f0de792f90 /media/multimed-2     ext4    defaults 0       2
```

Find more details at ```
man mount
``` and ```
man fstab
```

---

### Post by zoidberg2 on 2015-07-13
Thanks for the response, when I go to the /etc.fstab file

My current output reads 
> 
UUID=27cf43b8-55ba-4ec1-8d08-c87d0f511ca5 /               ext4    errors=remoun$


should I change it to 

> UUID=27cf43b8-55ba-4ec1-8d08-c87d0f511ca5 /media/john/Media ext4  defaults 0       2

---

### Post by sudodus on 2015-07-13
No, keep that line, it is for mounting your root partition and is necessary.

Make another line for the other partition. Check the UUID of your data alias Media partition with

```
sudo blkid
```

and use it (without quotes).

Create a mount point, for example **data**

```
sudo mkdir /mnt/data
```

and enter that into the line (where I have /media/multimed-2)

Enter the correct file system (problably ext4, but check with **sudo blkid**), ...

---

### Post by zoidberg2 on 2015-07-13
I just want to check this is right but do I add this line  to the /etc/fstab file

   > UUID=6ACA1FCBCA1F9285 /mnt/media  ntfs defaults 0       2



The output of the sudo bklid was this 
> 
/dev/sdb1: LABEL="Media" UUID="6ACA1FCBCA1F9285" TYPE="ntfs"

---

### Post by sudodus on 2015-07-14
Yes, I think so.

First run

```
sudo mkdir /mnt/media
```

If you are not happy with the ownership and permissions of the partition and its directories and files, you can add options to mount it with different options.

See the general options in ```
man mount
``` but also those specific for ntfs

```

Mount options for ntfs
       iocharset=name
              Character set to use when returning file names.  Unlike VFAT, NTFS suppresses names that
              contain nonconvertible characters. Deprecated.

       nls=name
              New name for the option earlier called iocharset.

       utf8   Use UTF-8 for converting file names.

       uni_xlate={0|1|2}
              For  0 (or `no' or `false'), do not use escape sequences for unknown Unicode characters.
              For 1 (or `yes' or `true') or 2, use vfat-style 4-byte escape  sequences  starting  with
              ":". Here 2 give a little-endian encoding and 1 a byteswapped bigendian encoding.

       posix=[0|1]
              If enabled (posix=1), the filesystem distinguishes between upper and lower case. The 8.3
              alias names are presented as hard links instead of  being  suppressed.  This  option  is
              obsolete.

       uid=value, gid=value and umask=value
              Set  the  file  permission  on  the  filesystem.  The umask value is given in octal.  By
              default, the files are owned by root and not readable by somebody else.

```

---

### Post by zoidberg2 on 2015-07-14
The above fix worked, thanks for all of your help.

---

