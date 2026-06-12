---
title: "Why can't I view my own files"
date: 2014-03-15
forum: General Help
---

### Post by bjngchn on 2014-03-15
Installed Lubuntu 13.10. It is always problematic. At some point files became invisible, because they are in encrypted form and don't appear where they are supposed to be (they are not deleted). Home directories of 2 users, both having admin power, are problematic. One of them can't be logged in graphically. The other have files which are in encrypted form and can't be viewed. Problem is mentioned here: [http://ubuntuforums.org/showthread.php?t=2211007](http://ubuntuforums.org/showthread.php?t=2211007) , so I won' duplicate details. Here I ask something else: Why does this happen? ... 13.10 seems to have mount problems both in kubuntu and lubuntu versions. And other versions  (all except 13.10) don't work anymore unfortunately , on any computer I tested. This problem is probably similar to this case: [http://ubuntuforums.org/showthread.php?t=1810825](http://ubuntuforums.org/showthread.php?t=1810825) ...Own files are encrypted but can't be accessed back with any password. If I have the password, why do I have to work hard to get my data back, which just sists there undamaged.

---

### Post by Mark Phelps on 2014-03-15
From my experience, Linux distros do NOT encrypt anything unless you tell them to.  IF you told the installer to encrypt your files, no one can help you out of that problem.

But then, HOW do you know these files are actually "encrypted"?  The problem you reference is your own thread.

---

### Post by bjngchn on 2014-03-15
When installing, I asked the installer to encrypt the whole disk with LVM, and encrypt home directory. It worked with little problems for  days. Of course when I logged in I was seeing files in usual form and didn't need to decrypt them....  And suddenly a mount problem prevents me from accessing parts of home directories. Mounting should be done by computer, not by me.  Instead of giving error, computer should do what it is supposed to do... It seems like 13.10's  have problems with mounting part(titon)s of installation (whatever this means).

---

### Post by buzzingrobot on 2014-03-15
LVM is a partitioning scheme, not an encrypting tool.

The partitions that are mounted at startup are defined in /etc/fstab.  If the file is altered, they may very well not be mounted. (Very likely, the machine won't boot.)

If you have changed anything since the installation, revert those changes.

If you are receiving error messages, we need to see the text of those messages.

---

### Post by bjngchn on 2014-03-16
Didn't make any changes just before this happens, except for adding deleting some files, chmod'ding and chown'ing files and directories (likely , whole home directory of a user), and making secondary user an admin and sudoer. Suggested fix by the system is the code: ecryptfs-mount-private , and the error is: ERROR: Encrypted private directory is not setup properly... ......Can this be the reason?: because encryption requires some extra space(?), if 80 percent of the disk is full, decryption can't be done normally, so I can't be shown files in decrypted form, because the computer have to contain both encrypted version and unencrypted version (?)

---

### Post by buzzingrobot on 2014-03-16
What did you mean when you said "files became invisible"? Don't appear in a directory listing?  Contents cannot be displayed? 

The notion of a "secondary user" is not a Unix/Linux concept. What do you mean by that? 

These things -- "adding deleting some files, chmod'ding and chown'ing files and  directories (likely , whole home directory of a user), and making  secondary user an admin and sudoer" -- hardly amount to "Didn't make any changes.."  Changing permissions and ownership, for example, could easily account for another user being unable to view the contents of the directory.  (I don't encrypt my directories, but I wouldn't be surprised if changing permissions and ownership of an encrypted folder caused problems. If the system decrypts files for someone who is not the owner of the files, what's to be gained from the encryption?))

That said, it wouldn't make sense to maintain encrypted and unencrypted versions of files. Encryption is supposed to be a security feature, which would be negated if unencrypted duplicates were available.  The de-encryption is done on the fly.

---

### Post by bjngchn on 2014-03-17
Files can't be found with dolphin, dir, or ls. But they are there for sure... Secondary user is second user, not the main user created during installation; but given the same rights manually.  I changed ownership for all  files on the  home folder (of the second user)  to this user to make  newly added files  editable by this user. At the beginning this worked well, but later most user  files suddenly became invisible.... Error is about mounting. Mounting not done properly. So what. sudo mount properly, won't work.

---

### Post by bjngchn on 2014-03-17
Fixed by luck.

---

