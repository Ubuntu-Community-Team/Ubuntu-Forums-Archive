---
title: "Make NFS share universally writable"
date: 2014-04-12
forum: General Help
---

### Post by CaptainMark on 2014-04-12
I'm pretty new to most networking so please bear with me if I use the wrong terminology.

I have a network of PC's at work which I wanted to connect with a shared documents folder to allow people to access documents anywhere. I found out about NFS which is new to me so thought I'd try it. I set up an NFS share on the server and all is running quite well, it's quite easy except an issue I have with permissions, obviously any files made on one pc will be owned by that user and are not writable on another PC. I would like the NFS share to be readable and writable by all computers, I want to make it so that all new files created on the NFS share (no matter which user made them) are writable by any other user on any other computer on the network, there is no internet access so security can be relatively lapse. Can this be done by the NFS setup itself or by basic file permission setups. 

What are my options?
The best I can figure out on my own are to either set a cron script that runs often that runs chmod 777 recursively on the share directory (obviously this is not a good option) or to use a FAT formatted USB for the share directory so that permissions do not apply (I don't even know if that's possible but it's a thought). I hoping people who know more about this subject have more practical and insightful ideas.

Some things to know:
I am not the sysadmin but I do have root access
The owner of the PC's (the director) is quite happy for me to do this but the IT people are not willing to help, although quite happy to look the other way
PC hostnames and usernames cannot be changed
No internet access
The PC's are not very up to date (running 10.04 I think)


Thanks for any help provided
Regards
Mark

---

### Post by SeijiSensei on 2014-04-12
Probably the easiest solution is to put all the users into a group in /etc/group, then give the group ownership of the directory and set the permissions to 2775.  The "2" sets the sgid bit so that files created by any user inherit the group's ownership.  With the default Ubuntu umask of 0002, files should be readable and writable by any of the group's members.

---

### Post by CaptainMark on 2014-04-13
This is the sort of answer I was hoping for. I am back at work tomorrow so I will give this a try and report back. Thanks.

---

### Post by CaptainMark on 2014-04-14
That suggestion done the trick mostly (so thanks) except some clients but not all seem to be overriding the file permissions from gnome only. On the problem clients (about half of them) and file created from the command line works fine however any file created from gnome/nautilus is created with 700 permissions. Any suggestions to work around this, failing that I'm back to the idea of a FAT formatted usb for the share.

I've checked in .profile .bash_profile for any lines that change the umask but found nothing

PS. This is Gnome 2 from the good ol' days

---

### Post by SeijiSensei on 2014-04-14
A quick Google search for "nautilus umask" brings up a raft of posts about how Nautilus seems to ignore the umask set in .profile.  One suggestion was to create a .bash_profile, which Ubuntu does not typically use, and put the umask command there.  However the range of queries and comments left me confused as to what the correct approach should be.

Since I'm a KDE user I'm afraid that's all the help I can give with this problem.

---

### Post by CaptainMark on 2014-04-14
Well thanks for the assist figuring out the problem, I got tunnel visioned onto gnome when it is just literally only files made via a nautilus right click menu that have the permissions issue. Seen as no one is likely to be doing that here I'm not going to consider it a problem.

Many thanks

---

### Post by SeijiSensei on 2014-04-14
Glad I can help. You should mark this [SOLVED] using the "Thread Tools" drop-down at the top of the page.

---

### Post by LewisTM on 2014-04-27
For the record, the "official" way of granting full access to an NFS share is with the following setup (which bypasses file permission issues):
In your /etc/exports file (on the server), your share should contain the **all_squash** parameter. This will make all guests appear as the anonymous user. You can then elevate the anonymous user to the UID of any server user, with parameters **anonuid=<uid>** and **anongid=<gid>**
That way, anyone connecting to the share will appear as the same server user, no matter who they are, and will have shared ownership of everything. If you don't have one, you should create a user on the server (e.g., nfsuser) for that purpose, and chown all files in the share to match.
Cheers!

---

### Post by CaptainMark on 2014-04-29
This is definitely good to know, Thanks.

---

### Post by SeijiSensei on 2014-04-29
> That way, *anyone connecting to the share will appear as the same server user*, no matter who they are, and will have shared ownership of everything. If you don't have one, you should create a user on the server (e.g., nfsuser) for that purpose, and chown all files in the share to match.
Like the Samba force user/group directives, that approach will not allow you to audit files by username.  If you care about which files little Billy is storing on the server, you need to use a method that allows billy to write files there with his username.  If you don't care about tracking ownerships, then the method LewisTM describes will be fine.

---

