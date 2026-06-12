---
title: "chown command with guest"
date: 2008-07-08
forum: General Help
---

### Post by M4rotku on 2008-07-08
Hello all,

I just added a shared folder for my ubuntu guest in a ubuntu host and I had to use "sudo" in order to use the mount command.  Now, root owns the shared folder and I can't access it.  I tried the ussual "chown" command:

> sudo chown joey /home/joey/Share

and the line was accepted and then the ownership stayed as root.  As far as I know, this should've changed the ownership to "joey".  Can anyone help me get this permission changed?

Much thanks,
M4rotku

---

### Post by M4rotku on 2008-07-08
bump

---

### Post by M4rotku on 2008-07-09
bump

---

### Post by Felson on 2008-07-09
What is the ownership of the folder before mounting? Also, you may want to change owner and group, not just ower.
```

chown joey:joey /home/joey/Share

```

---

### Post by M4rotku on 2008-07-09
It still won't let me access it.  I tried the command you game me.

I also tried using "sudo nautilus" and then changing the ownership via grub, and when I changed it to "joey" it automatically changed back to "root"

very confused :confused:

---

### Post by Felson on 2008-07-10
Lets see the output of
```

cd /home/joey/
ls -lF | grep Share

```

---

### Post by M4rotku on 2008-07-10
This is the output I got:

> drwxrwx--- 1 root root 4096 2008-07-07 23:58 Share/

and it still won't let me change the permissions or the group.

---

### Post by Felson on 2008-07-10
Thats a mounted mount point?

---

### Post by M4rotku on 2008-07-10
I don't understand what you are asking.  yes, it's a mount point and yes it has something mounted to it.  doesn't the latter make the former?  :confused:

---

### Post by Felson on 2008-07-10
LOL ya, it does. Bad way to ask I guess :p
I asume it's a smb share? If so, what was the command used to mount it? (X out user and pass of course)

---

### Post by M4rotku on 2008-07-10
It's not a smb share.  I am using virtualbox and I used the share command that the user manual told me to use:

> sudo mount -t vboxsf sda2 /joey/home/Share

I tried to mount without using sudo, but it told me that I had to use sudo in order to use the mount command.

---

### Post by Felson on 2008-07-11
Ok, first add your user to the "disk" group. Unmount the drive, then we need to add a line to the very end of fstab file.
```

sudo usermod -G disk joey
sudo gedit /etc/fstab

```
The line to add:
```

/dev/sda2 /home/joey/Share vboxsf users,rw 0 0

```
And then try and mount it as your normal user.
```

mount /home/joey/Share

```
I "think" this will solve your problem.

---

### Post by M4rotku on 2008-07-11
I still get the same error message.  :(

---

### Post by Felson on 2008-07-11
Here I thought I figured it out :p
What is the ownership of the Share folder when not mounted? Did you type the mount command exactly as I did, or did you use your original one?

---

### Post by bodhi.zazen on 2008-07-11
Well, it also depends on the file system.

You can not chown or chmod with FAT or NTFS partitions.

With those file systems, ownership and permissions are set at the time of mount.

To make matters worse, vboxfs has it's own terminology.

Try :```
sudo mount -t vboxsf sharename /home/username/mountpoint -o rw,exec,uid=1000,gid=1000,dev
```

If that works, update fstab with those defaults.

=====

The other option is to use a standard network sharing protocol such as NFS, samba, ssh (scp), ftp, sshfs, http ...

Here is an example with samba :

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

Yes, it is VMWare, but here's the thing, network shares are more flexible.

---

