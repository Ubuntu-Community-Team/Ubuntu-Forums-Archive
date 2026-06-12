---
title: "Does &quot;ls&quot; work"
date: 2007-02-04
forum: General Help
---

### Post by cethomas on 2007-02-04
I'm new to ubuntu. I just installed ununtu 6.06 Dapper Drake. And I must say it is different.:) 
I need to install VMware wokstation 5.5.3 Tools. I finally found out get to root. The VMware Tools instructions go like this:
 3. As root (su -), mount the VMware Tools virtual CD-ROM image, change to a working directory (for example, /tmp), uncompress the installer, then unmount the CD-ROM image.

Note: Some Linux distributions automatically mount CD-ROMs. If your distribution uses automounting, do not use the mount and umount commands below. You still must untar the VMware Tools installer to /tmp.

Some Linux distributions use different device names or organize the /dev directory differently. If your CD-ROM drive is not /dev/cdrom or if the mount point for a CD-ROM is not /mnt/cdrom, you must modify the following commands to reflect the conventions used by your distribution.

mount /dev/cdrom /mnt/cdrom

cd /tmp

Note: If you have a previous installation, delete the previous vmware-distrib directory before installing. The default location of this directory is
/tmp/vmware-tools-distrib.

4. Untar the VMware Tools tar file:

tar zxpf /mnt/cdrom/VMwareTools-5.0.0-<xxxx>.tar.gz

umount /dev/cdrom 

Now I need to do a ls to see where I'm at. My promt looks like this:
root@linux-ubuntu:/#, but when I do ls I get nothing, not even an error. In SUSE Linux when I do ls it shows me all of my files (folders). What am I doing wrong?:confused:

---

### Post by finer recliner on 2007-02-04
if the folder is empty, ls may output nothing.

try 'ls -a' (show all files, including hidden files/folders). this command will always display at least . (current directory) and .. (shorcut to one directory above where you currently are).

to find out what directory you're in right now, type the command 'cwd' or 'pwd' (i forget which one bash supports), but it stands for current working directory or present working directory respectively.

---

### Post by cethomas on 2007-02-04
> **finer recliner said:**
> if the folder is empty, ls may output nothing.

try 'ls -a' (show all files, including hidden files/folders). this command will always display at least . (current directory) and .. (shorcut to one directory above where you currently are).

to find out what directory you're in right now, type the command 'cwd' or 'pwd' (i forget which one bash supports), but it stands for current working directory or present working directory respectively.

Thanks. Pwd and ls -a worked but what is this? and .. (shorcut to one directory above where you currently are). When I did ls -a I seen the files and folders but nothing elese. And shouldn't just ls work? Using ls -a could make finding what you want harder to find.

---

### Post by riven0 on 2007-02-04
Yeah, but some files are hidden. That's why you add the** -a** after** ls**. If you don't care about hidden files, just use **ls**. The** ..** that you see is the directory above your current one. Type **cd ..** to move there.

---

### Post by finer recliner on 2007-02-04
im having a hard time understanding your question.

when you do ls -a, do all of your files start with a . (period)? the period means they are defined as a hidden file/folder. ls will only display non-hidden files and folders. ls -a will show both hidden and non-hidden files/folders.

ls should work similarlly to SUSE. if the folder is empty, ls will output nothing.

---

### Post by reclusivemonkey on 2007-02-05
> **cethomas said:**
> 
tar zxpf /mnt/cdrom/VMwareTools-5.0.0-<xxxx>.tar.gz

umount /dev/cdrom 

Now I need to do a ls to see where I'm at. My promt looks like this:
root@linux-ubuntu:/#, but when I do ls I get nothing, not even an error. In SUSE Linux when I do ls it shows me all of my files (folders). What am I doing wrong?:confused:

You're trying to unpack the tar to your CD Rom, which won't work and then you are unmounting, so even if it had worked there wouldn't be anything there. First copy the VMWareTools package to /tmp, then upack it;

```

cp /mnt/cdrom/VMwareTools-5.0.0-<xxxx>.tar.gz /tmp
cd /tmp
tar zxvf VMwareTools-5.0.0-<xxxx>.tar.gz

```

---

### Post by srt4play on 2007-02-05
> **reclusivemonkey said:**
> You're trying to unpack the tar to your CD Rom, which won't work and then you are unmounting, so even if it had worked there wouldn't be anything there. First copy the VMWareTools package to /tmp, then upack it;

```

cp /mnt/cdrom/VMwareTools-5.0.0-<xxxx>.tar.gz /tmp
cd /tmp
tar zxvf VMwareTools-5.0.0-<xxxx>.tar.gz

```


I agree it's a good practice to copy data from a cd to the hard disk before working with it, but his commands were not incorrect.  

tar will output to the currect directory by default, so he's not trying to unpack the tar file to his cd-rom. He's trying to unpack them in /tmp.

---

