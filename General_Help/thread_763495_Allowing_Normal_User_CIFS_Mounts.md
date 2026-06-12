---
title: "Allowing Normal User CIFS Mounts"
date: 2008-04-23
forum: General Help
---

### Post by Sondar on 2008-04-23
As the subject says, I have been trying to allow normal users to access shares on my Samba server. I'm trying to do this with the minimal amount of authorisation possible, which for me means no setuid, no changing directory owners.

Briefly, what I tried to do is set up a mount point for the Samba shares, owned by root, but belonging to the smbusers group. With an entry in my fstab file, I hoped to allow all members of the smbusers group to mount and access the share.

I couldn't get it to work. I'm describing the steps I took below, hoping that I can save some of you hours of fruitless effort, or that someone can put me straight by telling me what I'm doing wrong.

The approach I took is more-or-less described in §11.1.3, p310, in O'Reilly's *Using Samba*, 3rd ed, a copy of which suspiciously appears online. The section I'm referring to can be found at
[*Using Samba 3rd ed*]("http://codeidol.com/security/samba/Unix-Clients/The-Linux-CIFS-Filesystem#samba3-CHP-11-SECT-1.3")

Next stop after this forum is to post this message to an O'Reilly bulletin board, and gently suggest that their book wasn't proofread or edited properly, as their example doesn't work - unless, of course, someone points out my mistake.

So, to get started, let's see what version of mount.cifs and kernel I'm running:

```
me@localhost:/media$ mount.cifs -V
mount.cifs version: 1.10-3.0.26a
me@localhost:/media$ uname -a
Linux localhost 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i586 GNU/Linux
```

(This is Gutsy Gibbon 7.10)

I have no problem accessing shares on my Samba server. Here's how I tried to specify the mount point for my Samba share in my fstab file:

```
me@localhost:/media$ cat /etc/fstab
# <file system>                <mount point>    <type>      <options>          <dump>  <pass>
proc                           /proc            proc        defaults           0       0
[ ... snip ... ]
/dev/scd0                      /media/cdrom0    udf,iso9660 user,noauto,exec   0       0
**//localhost/Example\040Share   /media/smb_share cifs        user,group,noauto  0       0**
```

What I'm trying to say in the last line is that I'd like to mount the share 'Example Share' (the \040 in the file is the octal escape sequence for space) to the local directory /media/smb_share, using the cifs protocol. The options 'user,group,noauto' are standard mount(8) options - but, as the man page warns "The ... options apply to any file system that is being mounted (but not every file system actually honors them...)". From the man page, these options state, respectively, that I'd like an ordinary user to be able to mount the share, allow an ordinary user to mount the file system if one of his groups matches the group of the device, and that the device shouldn't be mounted at boot time.

Here are the permissions for the mount point:

```
me@localhost:/media$ ls -l
total 8
lrwxrwxrwx 1 root root        6 2008-04-20 21:10 cdrom -> cdrom0
drwxr-xr-x 2 root root     4096 2008-04-20 21:10 cdrom0
**drwxr-xr-x 2 root smbusers 4096 2008-04-22 15:43 smb_shar**e
```

The directory belongs to the smbusers group, and, by the group parameter, I want to allow ALL members of the smbusers group to mount and access the share. Here I find the man page a bit ambiguous, and this may be the cause of my problem. The page states that a user can mount if his group "matches the group of the DEVICE." In the situation here, the user's group matches the group of the MOUNT POINT. Alternatively, how do I find the group of the device '\\localhost\\Example Share'?

Anyway, do I belong to the smbusers group?

```
me@localhost:/media$ groups
me adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin **smbusers**
```

Yup. I also have no problem 'cd'ing into the smb_share directory, which, at the moment, happens to be empty.

Let's try to verbosely mount this share:

```
1. me@localhost:/media$ mount /media/smb_share/ --verbose
2. parsing options: rw,noexec,nosuid,nodev,noauto,user
3.
4. skipping empty user mount parameter
5. mount error: permission denied or not superuser and mount.cifs not installed SUID
```

On line 2 we see the options mount.cifs recognised from the fstab file. 'rw' appears to be a default option. The options 'noexec,nosuid,nodev' are implied by the option 'user', and I've checked this point - if I remove just the option 'user', these three option don't appear. This behaviour is consistent with the man page, and shows that standard mount recognises the standard option 'user'.

To demonstrate further that 'user' is recognised, and that it's necessary to get even this far, here's the output from mount if I remove the option from fstab:

```
me@localhost:/media/smb_share$ mount /media/smb_share/ --verbose
mount: only root can mount //localhost/Example Share on /media/smb_share
```

Looking at the rest of the options in the output, we see 'noauto', as we specified, but not 'group'. Why not? Why does mount recognise the standard option 'user', but not 'group'?

Control seems to have been passed to mount.cifs by the fourth line of the output, which skips the 'empty user mount parameter'. The 'user' option to mount.cifs(8) requires an argument, the name of a user authorized to access the share. This conflicts with the meaning of the option in mount(8). mount.cifs(8) has several synonyms for passing in user credentials - couldn't it leave this option alone, and - even better - implement the semantics specified by mount(8)? Another alternative would be to recognise and properly implement the 'group' option. For, as the last line of output shows, I was denied permission to access the share.

The next couple of lines show how I was able to succeed, by breaking my initial rule and changing the permissions of the share directory:

```
me@localhost:/media$ sudo chown me smb_share/
me@localhost:/media$ ls -ld smb_share
drwxr-xr-x 2 me   smbusers 4096 2008-04-22 15:43 smb_share
me@localhost:/media$ mount /media/smb_share/ --verbose
parsing options: rw,noexec,nosuid,nodev,noauto,user

skipping empty user mount parameter
Password: <password>

mount.cifs kernel mount options unc=//localhost\Example Share,ip=127.0.1.1,user=me,pass=password,ver=1,rw,noexec,nosuid,nodev,noauto,uid=1000,gid=1000
```

The difference here is that I now have permission to access the share. mount.cifs(8) tries to authenticate to the share as the user specified in the USER environment variable, and prompts me for this user's password. I give it, and I can mount the share. Ta-da! Alternatively, I could have used the mount.cifs semantics of the user options, and given the user credentials when I tried to mount, so:

```
me@localhost:/media$ mount /media/smb_share -o user=me%password
```

From what I've seen, then, I conclude that
1. Both mount(8) and mount.cifs(8) recognise the standard 'user' option, but they interpret the option differently.
2. It seems that neither programs recognise the 'group' option
3. As a consequence of the above, only root or the user that owns the mount point can mount a cifs share.

Anyone else like to clarify or comment on any of the points above, or point out what I've done wrong?

---

### Post by _sAm_ on 2008-04-23
Hi Sondar

Samba is great from Linux to Windows, but if you are using (Ubuntu) Linux on you desktop you should use NFS. Its much more faster then Samba(even when using cifs), can handle lots of load, and it is very easy to use. 
You don't have to deal with permissions, the system will fix that, and all users on your desktop can mount the share, both directly mounting or automatically in fstab. 

I can explain how to do so if you want.

Well, I hope I did understand you correctly.

---

### Post by DShad on 2009-12-13
> **_sAm_ said:**
> Hi Sondar

Samba is great from Linux to Windows, but if you are using (Ubuntu) Linux on you desktop you should use NFS. Its much more faster then Samba(even when using cifs), can handle lots of load, and it is very easy to use. 
You don't have to deal with permissions, the system will fix that, and all users on your desktop can mount the share, both directly mounting or automatically in fstab. 

I can explain how to do so if you want.

Well, I hope I did understand you correctly.

You know what?  I would need your help on that...

I think I messed up BIG time with mount.cifs permission, and still cannot automount my samba share.

1- Did chmod u+s 'which umount.cifs' and same with mount.
2- Add this line to /etc/fstab:

//server /mountpoint cifs users,suid,domaine=xxx,username=xxx,password=xxx,iocharset=utf8,file_mode=0777,dir_mode=0777,auto 0 0

I can mount from terminal with: mount mountpoint

But it doesn't seem to automount like I'd like to be.

Thanks

---

