---
title: "samba permissions on directories"
date: 2012-10-18
forum: General Help
---

### Post by Drenriza on 2012-10-18
Loads of samba threads from me ,)

Question about permissions on directories inside a share.

On my samba server i have a share, inside that share i have a folder as follows

drwxr-xr-x 2 root root 4096 Oct 18 15:22 test.d

When i then mount this share on another system the permissions change

drwxrwxrwx 1 root root 0 2012-10-18 15:22 test.d

Why?

The same is happening with a pearl script i got in my share

share
-rwxr-xr-x  1 root root  270 Oct 16 14:27 import_all.sh

mounted
-rwxrwSrwx 1 root root  270 2012-10-16 14:27 import_all.sh

Anyone who can tell me what is going on with the permissions?

I have tried to google it, but i cant get a straight answer.

I would just like that the permissions i got on the folders in my share on the samba server, would be the same when the share gets mounted.

Kind regards.

---

### Post by Drenriza on 2012-10-22
No one?

---

### Post by bab1 on 2012-10-22
> **Drenriza said:**
> Loads of samba threads from me ,)

Question about permissions on directories inside a share.

On my samba server i have a share, inside that share i have a folder as follows

drwxr-xr-x 2 root root 4096 Oct 18 15:22 test.d

When i then mount this share on another system the permissions change

drwxrwxrwx 1 root root 0 2012-10-18 15:22 test.d

Why?

Permissions are set by the local system mount of the remote file system. > 

The same is happening with a pearl script i got in my share
[**_[COLOR="Blue"]Pearls[/COLOR]_**]("https://www.google.com/search?q=pearls&btnG=Go!") come from oysters.  ;-)  It's perl.> 
share
-rwxr-xr-x  1 root root  270 Oct 16 14:27 import_all.sh

mounted
-rwxrwSrwx 1 root root  270 2012-10-16 14:27 import_all.sh

Anyone who can tell me what is going on with the permissions?

I have tried to google it, but i cant get a straight answer.

I would just like that the permissions i got on the folders in my share on the samba server, would be the same when the share gets mounted.

Kind regards.
As I said before this is controlled when the share is mounted by the local host.  The best you can do on the server side is control the access to the share.  I have to assume you are using a GUI to mount the share and the permissions are set by the file manager (i.e. Nautilus or Windows Explorer).

---

### Post by Drenriza on 2012-10-22
Thanks bab1

It's mounted on a debian server with cifs.

So i should create a /etc/fstab entry?

But i'am not a good fstab'er. So i'am not sure what i should create for a entry. To have 555 permissions on the mounted share folders and files.

> Pearls come from oysters.   It's perl.
xD

Anyone who can give an /etc/fstab example on mounting a samba share using cifs to get 555 permissions?

Kind regards.

EDIT.
I have tried
//192.168.100.10/video1 /root/cristian-test/sambaTest.d cifs  credentials=/root/smb_credientials_txt,auto,user,ro 0 0

But still permissions dont get for example "read only"

What permissions are the one that take effect.

The permissions on the directori and files in the samba share?

The permissions defined in /etc/samba/smb.conf

or the permissions in fstab on the remote machine that mount the share

???

---

### Post by bab1 on 2012-10-23
> **Drenriza said:**
> Thanks bab1

It's mounted on a debian server with cifs.

So i should create a /etc/fstab entry?

But i'am not a good fstab'er. So i'am not sure what i should create for a entry. To have 555 permissions on the mounted share folders and files.


Anyone who can give an /etc/fstab example on mounting a samba share using cifs to get 555 permissions?

Kind regards.

EDIT.
I have tried
//192.168.100.10/video1 /root/cristian-test/sambaTest.d cifs  credentials=/root/smb_credientials_txt,auto,user,[COLOR="Red"]**ro**[/COLOR] 0 0

But still permissions don't get for example "read only"

What permissions are the one that take effect.

The option ro (above in red) is all that is needed to mount the entire share as read only.  The other options such as *auto,user* are not needed.  The credentials are to ID the samba user.  Here is what I used to mount a share named test.  I supplied the password at the CLI```
sudo mount -t cifs //rincon/test /media/test/ -o user=bab1,ro
```
The test share (//rincon/test) is defined as this```
[test]
        comment = Test Share
        path = /smb/test_share
        browsable = yes
        force group = smbusers
        writable = yes
        create mask = 0664
        directory mask = 2775

```...note that the share shows that it is writable  amd the create masks allow for writeable data.  But I tested the mount and no files or directories can be created, nor can any existing date be altered.
> 

The permissions on the directory and files in the samba share?  The permissions defined in /etc/samba/smb.conf?
See above.  Share permissions in the smb.conf don't matter when you use ro in the remote mount.> 

or the permissions in fstab on the remote machine that mount the share

???
Once again the share permissions are determined when you mount the remote share to the local machine.  The specific option is **ro** (for read only).  To convert the CLI version of my mount command you would use something like this```
  //rincon/test /media/test/  cifs credentials=/root/smb_credientials_txt,ro 0 0 
```... The creds file should have the Samba user and pass in it.

See if this works.  If not let me know.  One odd thing is that the GUI permissions tab still shows that the data is rw even if it really is ro.  This is the line for the remotely mounted share using the command mount at the CLI```
//rincon/test on /media/test type cifs (ro,mand)
```

---

### Post by Drenriza on 2012-10-24
If i set ro in fstab yes then the share is only "read only" BUT!

Why are permissions shown as rwxrwSrwx for many of my files??

The sticky bit for group is for one creating trouble for me.

Why are my files not shown as 444 r--r--r-- when set so in fstab

---

### Post by bab1 on 2012-10-24
> **Drenriza said:**
> If i set ro in fstab yes then the share is only "read only" BUT!

Why are permissions shown as rwxrwSrwx for many of my files??

The sticky bit for group is for one creating trouble for me.

Why are my files not shown as 444 r--r--r-- when set so in fstab

If I understand you correctly; you are successful!  All the data is RO.

The permissions in file system is not changed by fstab.  They were overridden by the peramiter RO.  The permissions are still there at the remote host.  I told you that this would be the case.  It does not change the fact that the data is RO after you have mounted the share.

The bit you are talking about (S) is not the sticky bit.  It is the SGID bit and should not really be of concern as it only sets the GID upon creation of a file of directory, which you can't do on a RO filesystem,

I told you that this would be the case.  It does not change the fact that the data is RO after you have mounted the share.

---

### Post by since on 2012-10-24
hi great! i'll dig it


because i'll need to work with samba in a fev minutes


gotta dump / rescure data to a friends win7 laptop

---

### Post by Drenriza on 2012-10-25
> The bit you are talking about (S) is not the sticky bit. It is the SGID bit and should not really be of concern as it only sets the GID upon creation of a file of directory, which you can't do on a RO filesystem,

But it is, since it create a error further down the line when trying to run a perl script.

-rwxrwSrwx 1 root root  270 2012-10-16 14:27 import_all.sh
error
Setuid/gid script is writable by world.

Thus the script cannot run. I'am not a perl script writer, and does not fully understand the error. But from what i have been told, it's a error that can give perl the ability to say "i'am X user, thus execute me with permissions for this user".

Which is not allowed in this manner and the script closes.

Any ideas?

---

### Post by bab1 on 2012-10-25
> **Drenriza said:**
> But it is, since it create a error further down the line when trying to run a perl script.

-rwxrwSrwx 1 root root  270 2012-10-16 14:27 import_all.sh
error
Setuid/gid script is writable by world.

Thus the script cannot run. I'am not a perl script writer, and does not fully understand the error. But from what i have been told, it's a error that can give perl the ability to say "i'am X user, thus execute me with permissions for this user".

Which is not allowed in this manner and the script closes.

Any ideas?

Read only means just that.  No write and no execute.  I assume we are referring to the partition we mounted RO.  Is this correct?

---

