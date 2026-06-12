---
title: "Samba permission problem"
date: 2007-01-17
forum: General Help
---

### Post by mizar001 on 2007-01-17
I have a real security problem with samba. 

I mounted an ntfs folder with the command :

smbmount $remoteLocation $targetDir -o     
    credentials=$credFile,
    rw,
    fmask=740,
    dmask=750,
    uid=userA,gid=groupB

what appears is that 
directories have drwx    r-x    --- permissions (owner userA,group userB)
files have          -rwx     r--    --- permissions (owner userA,group userB)

I should not be able as a user of groupB to modify files in $targetDir, or do any write operation.
In facts if i sets these permission without samba mounting things works correctly.

What happens with samba? As user of groupB i don't have write permissions, so i cannot 
upload a file or delete a file or directory. But i discovered that i can change a file, so i have overwrite permission. This is innaceptable.

PS: my credential file make samba log with administrator permission on the ntfs folder.

---

### Post by gaebriel on 2007-01-17
You're mounting it 'rw', read-write which probably has something to do with it. Also, when you mount the share to test the permissions, are you sure you're connecting to the files as different users?

---

### Post by mizar001 on 2007-01-19
Of course. I log in with different users in my shell or in ssh. But i log in samba with administrator powers. This should have nothing to do with local setted permissions.

The permissions are respected, some users can write, some others can't, as espected, but the overwrite permission is ever allowed, that's the problem.

---

### Post by wro on 2007-01-21
I think I've found the same thing.  This is my post from another part of this forum, no-one replied :

[I]"I am trying to get the file permissions set up on a Buffalo 320GB Linkstation Pro.

I have typed the following in terminal:

sudo smbmount //ipaddress/buffalo /media/buffalo -o fmask=0744,dmask=0775,uid=mylinuxusername,gid=buffalo

where uid is the name I log onto ubuntu

gid, called "buffalo" has two users in it, me included.

I thought that the above fmask and dmask commands should give me rwx to everything - which they do.

Anyone in gid to be able to create, delete directories etc, but to only have read only permissions to files.

When I log in as the other user in gid, I can go into a file, change it, and re-save it! Even though if I look at the permissions it says Group - read only.

Also, if I go in as "other", someone who isn't in the group, they can view directories , but can't create or delete - as i would expect, BUT they too can go in and change and re-save a file!

What am I doing wrong?

Any ideas, please?"[/I]

Does this sound familiar?

---

### Post by mizar001 on 2007-01-22
yes. that's it. 
This is a well known bug or what ? 

I think samba permissions are not well trasmitted to and from linux. Or in any other meaning the samba command line is not as intuitive as it seems, when you must decide different permissions over files and directories.

I solved this problem only because i want share this mounted folder through an ftp server, so i can deny write commands to users that shuld not have write permission. But the real problem still exists.

---

