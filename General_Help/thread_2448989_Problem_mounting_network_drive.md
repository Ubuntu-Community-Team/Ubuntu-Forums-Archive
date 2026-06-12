---
title: "Problem mounting network drive"
date: 2020-08-17
forum: General Help
---

### Post by michael351 on 2020-08-17
I tried mounting a network drive using the following:

sudo mount.cifs //192.168.1.xx/share /mnt/HomeNeworkDrive/ -0 user=username,pass=password 

and received: mount error(13): Permission denied

Any suggestions? (user name and password are correct when I checked)

---

### Post by TheFu on 2020-08-17
More info needed. Please.
Info about the client and server.
[LIST]
[*]OS
[*]OS version
[*]share server
[*]share server version
[*]share client version
[*]exact command used (minus passwd); really should use a credentials file instead
[*]exact error messages
[*]
[/LIST]
please.

it used to be easy. not anymore.  We can't read minds. Info necessary.

---

### Post by michael351 on 2020-08-17
[LIST]
[*]OS: Ubuntu
[*]OS version: 18.04
[*]share server: WD Cloud NAS
[*]share server version: version 2
[*]share client version: don't know
[*]exact command used (minus passwd); really should use a credentials file instead: as above - exactly.
[*]exact error messages: also above - exactly
[/LIST]

---

### Post by TheFu on 2020-08-17
**WD Cloud NAS** is what you need to look into.  The specific version of SAMBA running on that device and specific supported SMB version. Should be in the WD Support pages somewhere.

As for a "credentials file", that is a _specific option_ for mounting CIFS storage. From the mount.cifs manpage:
```
credentials=filename|cred=filename
   specifies a file that contains a username and/or password 
   and optionally the name of the workgroup. The format of the 
   file is: 
      username=value
      password=value
      domain=value

   This is preferred over having passwords in plaintext in a shared 
   file, such as /etc/fstab . Be sure to protect any credentials file 
   properly.
```
You can check the manpage on your Linux system using **man mount.cifs**.

Sorry I can't tell you the exact options to use. Samba used to be easier before MSFT and the Samba projects both changed their defaults to improve security.  Old devices that don't support the current protocols from Win7+ all need special settings to work since about Feb 2020.
You've probably seen this already:
[https://baihuqian.github.io/2019-10-20-how-to-mount-wd-mycloud-on-ubuntu-18-04/](https://baihuqian.github.io/2019-10-20-how-to-mount-wd-mycloud-on-ubuntu-18-04/)
I don't think that's sufficient anymore, but perhaps the 2 options will be helpful?

If the device supports NFS, I can definitely help with that, since NFS is NFS almost everywhere supporting v3 well. If it can't, we've reached the end of my CIFS notes. Someone else with more expertise will have to help.

---

### Post by michael351 on 2020-08-18
Thanks! I am going to give the link you supplied a try. Seems straight forward.

---

### Post by michael351 on 2020-08-21
"TheFu" - The link worked ! .... sort of.

I was able to mount the WD MyCloud NAS following the links instrucitons since I was able to see the files and do what I needed to, however I received this error when mounting:

//192.168.10.10/Archive /media/Archive cifs uid=ubuntu,credentials=/home/ubuntu/.smbcredentials,iocharset=utf8 0 0

mount: 0: mount point does not exist.

Mount point must exist since all is working .... am I missing something?

---

### Post by TheFu on 2020-08-21
Before the storage is mounted, 
```
sudo mkdir /media/Archive
```
That should be handled by systemd.mount service, but in the old days, we had to ensure the mount directory pre-existed.

---

