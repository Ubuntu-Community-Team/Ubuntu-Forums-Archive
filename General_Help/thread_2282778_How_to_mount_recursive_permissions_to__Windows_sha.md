---
title: "How to mount recursive permissions to  Windows shares in FSTAB"
date: 2015-06-16
forum: General Help
---

### Post by jason-aints on 2015-06-16
I have a small home network of 6-8 computers, most of them running either Ubuntu or Fedora.  I decided to share everything with CIFS (Samba) so that I could see all drives from my 2 Windows 7 boxes, my Windows tablet and all of my Linux machines.

Long story short, when I try and mount a CIFS share in my FSTAB file, it mounts with no problem and I can access it.  In the top level I can create a folder, then once I am inside of that folder, I cannot create a new directory or copy files.  I do not have write permissions to the new folder I just created.

Prior to mounting the share, I CHMOD the mountpoint with 0777.  After I enter the FSTAB line and run sudo mount -a, the mountpoint no longer shows 0777, and usually comes up with a strange user:group, or perhaps just numbers in the user:group listing.

Here are the lines I added in my FSTAB file:
```
//192.168.1.10/Parakletos /mnt/parakletos cifs creds=/root/creds 0 0
//192.168.1.3/Users /mnt/shamgarr cifs creds=/root/jape.creds 0 0
```

here is the ls-l command on the /mnt folder:
```
drwxrwxrwx  10 nobody users    0 Jun  9 12:25 parakletos
drwxrwxrwx   2 root   root  4096 May 18 22:27 samson
drwxr-xr-x   2 root   root  4096 May  2 08:16 shamgarr
```

I think I need to add something to the FSTAB to make it recursive but I am not certain.  I just want to be able to write to the Windows share, which I should have complete permissions to.  the jape.creds file has the username/password of my windows box, which I made to match my linux boxes also.

Thanks for any help

---

### Post by nlee2 on 2015-06-16
I chown the mount point to myself:mygroup. Assuming an id of 1000 for both, then change fstab entry to grant rw to everyone or whatever chmod is appropriate for you.

//192.168.1.10/Parakletos /mnt/parakletos cifs creds=/root/creds,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0

---

### Post by jason-aints on 2015-06-18
This seems to be working fine, thanks.

What do you suggest if I am mounting a shared drive from another Linux box?  I tried this same command and even though that box has the share mounted as CIFS, it gave errors.  I assume that I need to mount it with NFS or EXT4, or something.

---

### Post by nlee2 on 2015-06-18
My understanding is that you have a linux host with a hdd that you would like to share and the client should be able mount this share using a fstab entry but it is not working. 

How is the drive on the Linux box mounted and be specific?

"it gave errors" I do not know what that means.

---

### Post by jason-aints on 2015-06-18
I have multiple hosts, as stated originally.  I have 2 NAS devices, not sure what filesystem they use, but they act like Windows file systems.
From my Fedora laptop, I updated the FSTAB file with your suggestions from your first reply, and used those settings to mount the NAS share in the FSTAB file.  It seems to be working fine.
When I try those same settings from the Fedora laptop to mount a 3rd share, which is served from a CentOS box on my network, it doesn't work.  I tried several combinations of syntax in the FSTAB file, and I am probably just missing the correct combination.

Here are 2 NAS shared drives, mounted from my Fedora laptop, which seem to be working fine after your suggestion:
```
//192.168.1.10/Parakletos /mnt/parakletos cifs creds=/root/jape.creds,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
//192.168.1.3/Users /mnt/shamgarr cifs creds=/root/jape.creds,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0

```

When I added a 3rd line to the FSTAB, this one pointing to a CentOS shared directory, I got these messages.  I used the same syntax as above, and then tried changing it up a bit also.
> [jape@hamtop mnt]$ sudo vim /etc/fstab
[jape@hamtop mnt]$ sudo mount -a
mount.nfs: remote share not in 'host:dir' format
[jape@hamtop mnt]$ sudo vim /etc/fstab
[jape@hamtop mnt]$ sudo mount -a
mount.nfs: Failed to resolve server //192.168.1.13: Name or service not known
[jape@hamtop mnt]$ sudo vim /etc/fstab
[jape@hamtop mnt]$ sudo mount -a
mount.nfs: an incorrect mount option was specified
[jape@hamtop mnt]$ sudo vim /etc/fstab
[jape@hamtop mnt]$ sudo mount -a
mount.nfs: Failed to resolve server /192.168.1.13: Name or service not known
[jape@hamtop mnt]$ sudo vim /etc/fstab
[jape@hamtop mnt]$ sudo mount -a
mount: special device 192.168.1.13:/mnt/cloud does not exist
[jape@hamtop mnt]$ sudo vim /etc/fstab
[jape@hamtop mnt]$ sudo mount -a
mount: special device 192.168.1.13:/mnt/cloud does not exist
[jape@hamtop mnt]$ sudo vim /etc/fstab
[jape@hamtop mnt]$ sudo mount -a
mount: special device 192.168.1.13:mnt/cloud does not exist


Some samples of what I tried adding to the FSTAB file are:
```
//192.168.1.13/share /mnt/josephus cifs creds=/root/jape.creds,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
/192.168.1.13:/share /mnt/josephus cifs creds=/root/jape.creds,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
192.168.1.13:/share /mnt/josephus cifs creds=/root/jape.creds,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
```

None of these worked, so I removed the link completely.  Again, I am sure I don't have the correct format, but I also wonder about the shared directory on my CentOS box.  I think I currently have it CHMOD to 0777 and it is a EXT4 file system.

---

### Post by nlee2 on 2015-06-18
This is a ubuntu forum. Slightly off topic but it applies to ubuntu as well.

Thanks for the info. Centos is on 192.168.1.13 and you have samba running, created a user specified in your credentials and configured a share named share and allowed user access.

What is in /etc/samba/smb.conf for [share]?

---

### Post by jason-aints on 2015-06-18
[Tonido]
	path = /mnt/cloud
	writable = yes
	browsable = yes
	guest ok = yes
	valid users = @wheel

---

### Post by jason-aints on 2015-06-18
Yes you are right about the Ubuntu forum.  My main box is actually a 14.04 box.  I am moving everything to the CentOS box right now because I need to reload the OS on Ubuntu and I am going to upgrade some hardware at the same time.  I am likely going to put Ubuntu back on my laptop also, I think I like it better than Fedora.

---

### Post by nlee2 on 2015-06-18
//192.168.1.13/Tonido /mnt/josephus cifs creds=/root/jape.creds,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0

To test. Sign on to 192.168.1.13 with userid in your credentials. Run

smbclient -L localhost

check that Tonido share is available.

---

### Post by jason-aints on 2015-07-11
This is what I have in my FSTAB file:
```
//192.168.1.13/Tonido /mnt/josephus cifs creds=/root/jape.creds,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0

```
smbclient -L localhost shows this:

[jape@josephus ~]$ smbclient -L localhost
Enter jape's password: 
Domain=[JUDEA] OS=[Unix] Server=[Samba 4.1.12]


	Sharename       Type      Comment
	---------       ----      -------
	Tonido          Disk      
	Public          Disk      
	IPC$            IPC       IPC Service (Samba Server Version 4.1.12)
Domain=[JUDEA] OS=[Unix] Server=[Samba 4.1.12]


	Server               Comment
	---------            -------
	JOSEPHUS             Samba Server Version 4.1.12


	Workgroup            Master
	---------            -------
	JUDEA                JOSEPHUS


When I run sudo mount -a, I get this:
[jape@hamtop ~]$ sudo mount -a
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
[jape@hamtop ~]$

---

