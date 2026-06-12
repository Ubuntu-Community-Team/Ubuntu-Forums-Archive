---
title: "Permission Denied"
date: 2008-05-24
forum: General Help
---

### Post by ragflan on 2008-05-24
Hey, I'm using Hardy Heron. I have this problem with 'Permission Denied' prompts. 

- I'm the only user account on the computer and I'm the administrator. 
- I installed Songbird and I wanted to create a shortcut in the Menu for it. 
- I open up 'Main Menu' under Preferences then I go to the Sound and Video and create new item. 
- I enter Name and Command (under /opt/Songbird) and this error comes up:

[IMG]http://s14.divshare.com/files/2008/05/24/4573102/Screenshot-gnome-desktop-item-edit.png[/IMG]

The same error comes up when I try to change the default media player for *.avi files from Media Player to VLC. Am I doing it the wrong way or something?

---

### Post by sisco311 on 2008-05-24
Open a terminal(Applications -> Accessories -> Terminal) and post the output of:
```
ls -la /home/$USERNAME/.local/share/applications/
```

---

### Post by ragflan on 2008-05-24
total 12
drwxr-xr-x 2 root    root    4096 2008-05-23 03:07 .
drwxr-xr-x 7 ragflan ragflan 4096 2008-05-23 05:11 ..
-rw-r--r-- 1 root    root     100 2008-05-23 03:07 defaults.list

---

### Post by feest on 2008-05-24
try to do 
sudo chmod 777 /home/$USERNAME/.local/share/applications/
in the terminal and try again

---

### Post by sisco311 on 2008-05-24
For some odd reason the folder is owned by root. Run: 
```
sudo chown -R $USERNAME:$USERNAME $HOME
```to restore the ownership on your home directory.
[About file permissions, users and groups.]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by ragflan on 2008-05-24
Hey! That worked! Thanks a lot!

One more question. Everytime I open a large movie file (say around 500mb), the computer screen goes like haywire and system locks up. I have to power down system using the power button. Media Player had this problem and VLC as well. 

Can it be because I'm using Advanced Desktop Effects? I installed the Compiz Config Settings Manager as well.

---

### Post by ragflan on 2008-05-24
> **sisco311 said:**
> and:
```
sudo chown -R $USERNAME:$USERNAME $HOME
```

chown: cannot access `/home/ragflan/.gvfs': Permission denied

I get that error. I type sudo chown -R $USERNAME:$USERNAME $HOME, right? And I substitute $USERNAME with $myusername, correct? I did it without changing anything and i still get the same permission denied error.

---

### Post by sisco311 on 2008-05-24
You don't need to change anything in the command. Ignore that error.

$USERNAME is a bash variable.

Try this command:
```
echo $USERNAME
```

---

### Post by ragflan on 2008-05-24
> **sisco311 said:**
> You don't need to change anything in the command. Ignore that error.

$USERNAME is a bash variable.

Try this command:
```
echo $USERNAME
```

I do the echo $USERNAME and I get my username: ragflan. But for the previous command, I got the same error again: Permission Denied.

---

### Post by sisco311 on 2008-05-24
> Gvfs is a userspace virtual filesystem with backends for things like sftp, ftp, dav, smb, obexftp, etc.  It is the replacement/successor of gnome-vfs.Don't worry about the error. The command failed just on the ~/.gvfs directory and worked on the rest.

If you type
```
ls -la /home/$USERNAME/.local/share/applications/
```you will see that the directory is owned by you.

> 
total 12
drwxr-xr-x 2 **ragflan ragflan**    4096 2008-05-23 03:07 .
drwxr-xr-x 7 ragflan ragflan 4096 2008-05-23 05:11 ..
-rw-r--r-- 1 **ragflan ragflan** 100 2008-05-23 03:07 defaults.list     


---

### Post by jimbob on 2008-05-24
You can't do anything to the .gvfs directory because it is currently mounted by the gvfs-fuse-deamon.  Type in sudo mount and you will see it in the list.  Don't worry about that one.

---

### Post by broomie on 2011-06-20
I had similar issues with ownership of HOME in Ubuntu 11.04 and Dropbox and this cleared it all up!

---

