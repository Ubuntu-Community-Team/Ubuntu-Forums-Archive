---
title: "configuring ssh"
date: 2014-03-14
forum: General Help
---

### Post by sniper8752 on 2014-03-14
I am trying to allow for ssh access onto my Ubuntu server.  I am not able to login. When I add the following to sshd_config:
```
Match Group sftpusers
ChrootDirectory %h
AllowTCPForwarding
```
I get a "Network error: Software caused connection abort."
My user that logs in is part of the following groups:
accounting sftpusers departments

---

### Post by Lars Noodén on 2014-03-14
Is the directory specified by %h owned by root and writeable only by root?  For sshd's built-in chroot to work, it has to be that way.  Individual files and subdirectories can be owned and writeable by whoever but the chrootdirectory is for root only.

---

### Post by sniper8752 on 2014-03-14
%h = /home/username, right?  so I have to make each one owned by root, and writable only by root?  how can I have the users add files and folders then?  I would like the users to be locked to their own directories, and not be able to traverse outside of them.

---

### Post by efflandt on 2014-03-14
In order to chroot, any binaries (programs) or other things they need have to be within the chroot directory, since they would not have access to things like /bin in the parent file system.

Typically in Ubuntu, user's home directories are in the same group as their username. So if you remove **read** and **execute** permission for **others** from their home directories, nobody would be able to see into any other user's home directory.

for example:```
efflandt@xps8100-1204:~$ ls -dl /home/*
drwxr-xr-x  2 deffland deffland 4096 Oct 27 06:00 /home/deffland
drwxr-xr-x 66 efflandt efflandt 4096 Mar 13 19:26 /home/efflandt

efflandt@xps8100-1204:~$ ls ../deffland
examples.desktop

efflandt@xps8100-1204:~$ sudo chmod o-xr /home/*
[sudo] password for efflandt: 

efflandt@xps8100-1204:~$ ls -dl /home/*
drwxr-x---  2 deffland deffland 4096 Oct 27 06:00 /home/deffland
drwxr-x--- 66 efflandt efflandt 4096 Mar 13 19:26 /home/efflandt

efflandt@xps8100-1204:~$ ls ../deffland
ls: cannot open directory ../deffland: Permission denied
```

---

### Post by sniper8752 on 2014-03-16
I just thought of something - I was logging in as root before, so maybe that's why it was letting me traverse outside of the directory?  
When I edit a file on my client in filezilla, then save and upload, I get this error:
```
Status:	Starting upload of C:\Users\username\AppData\Local\Temp\fz3temp-1\test.txtCommand:	PASV
Response:	227 Entering Passive Mode (192,168,153,128,29,230).
Command:	STOR test.txt
Response:	553 Could not create file.
Error:	Critical file transfer error
```

What does this mean?  When I log into the server as the user that owns the file, and attempt to write to it, I get a "-sh: 11: cannot create test.txt: Permissions denied".  It is owned by root and the root group.  Looking back at one of the previous posts, I see it says the main folder (/home/Bob, in this case) has to be owned by root, then the following sub-items can be owned by the user.  Is this my issue?

---

### Post by Lars Noodén on 2014-03-16
That's correct, usng SFTP's built-in chroot you have to have the chrooted directory (e.g. %h) owned by root and not writeable by others.  The downside is that as another user you cannot create files in that directory.  However, you should be able to write to the subdirectories which you own.  Can you 'cd' to a subdirectory and write there?

---

### Post by sniper8752 on 2014-03-16
ok - i did a chroot for files/directories, and it looks like the user can create/modify items.  i noticed that when I did the chown, the group changed from root to accounting, which bob is part of.  was this changed to bob's group that he is part of?  and if that group is listed, then are they all allowed to access/modify the file/folders?

---

### Post by Lars Noodén on 2014-03-16
I'm not sure that it matters which group the chrooted directory can be, as long as it is not writeable by other than root.  If there is a permissions problem in that regard, you will get an error like "Write failed: Broken pipe
Couldn't read packet: Connection reset by peer"  You can always create files inside the chrooted directory and chown them to be owned by the user.  Then you can overwrite them but not create.

---

### Post by sniper8752 on 2014-03-16
Sorry - meant the sub items in the chroot directory were owned by the accounting group.

---

