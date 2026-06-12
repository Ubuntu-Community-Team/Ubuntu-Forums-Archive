---
title: "[B]XDMCP + many users + user/group permissions[/B]"
date: 2007-06-27
forum: General Help
---

### Post by srangelov on 2007-06-27
Hi, all!

I need a server with XDMCP where employees will log in from their PC and work with two or hree programs. Here is where I am:
I created two users - added both of them to one group. Since I didn't managed to find a way for them to have one and the same home folder (it is essential all users to work in one folder and have access to same files), I created a folder in the home folder of the one user and a link to this folder in the other user's home folder. Now the two users have access to one and the same folder (if anyone has a better decision for this - please, post it). The problem is now that both users need equal permissions on these files, i.e. rwx, but none of the users can write the files created by the other user.
I would appreaciate any suggestions.
Sotir

---

### Post by McNils on 2007-06-27
Put the users in same primary group, the group specified in /etc/passwd, and make sure that they have a umask that does not remove write access for the group,  like 0002.

---

### Post by srangelov on 2007-06-28
How to set the umask???
I set the default umask to 0002 by typing in the terminal
```
umask 002
```
then I check the umask by typing
```
umask
```
and it says
```
0002
```
But whenever I creat new file its permissions are the same as before - Owner - write and read, groop - read only, others - read only???

---

### Post by McNils on 2007-06-28
Try to set it in /etc/profile. I beleave that file is sourced when a user log in via XDMCP. 

This setting can be overrided by the users  ~/.bash_profile and ~/.bashrc files.

---

### Post by srangelov on 2007-06-28
Hi, McNils!
Thanks for the replies, but nothing's changed. In /etc/profile the umask was 022 and I changed it to 002, in ~/.bash_profile and ~/.bashrc the umask is marked with # - I did not change it. I tried again - created a file and its permissions were as before - wr for owner and read only for group and others.
If this matters I am testing with the default (/root) user without XDMCP using OpenOffice Word Processor and saving files at the Desktop.

P.S I read somewhere that a folder can be set to a specific user and/or with a specific permissions, thus each file created in this folder will be owned by that user and/or each file will have that specific permissions. But I do not know how to do that.

---

### Post by McNils on 2007-06-28
Did you log in again? /etc/profile is only sourced on log in.  You can try this to see the effect of changing umask.

```

umask 022
touch bar
umask 002
touch foo
umask 000
touch foobar
ls -l bar foo foobar

```

---

### Post by bodhi.zazen on 2007-06-28
To set ownership and permissions of a folder (directory) :

Put both users in a group, say share.

Then make a directory, say /home/documents

```
sudo mkdir /home/documents
sudo chown root.share /home/documents
chmod 770 /home/documents
chmod g+s /home/documents

ln -s /home/documents /home/<user_one>/documents
ln -s /home/documents /home/<user_two>/documents
```

The chmod g+s /home/documents sets the group ID of the directory ;)

See here for a more detailed explanation: [http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

I think that would be a better solution then umask :)

---

### Post by srangelov on 2007-07-02
Thanks McNils and bodhi.zazen!

I'll try later today and post if there are any issues.

---

