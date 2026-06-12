---
title: "libreoffice files not writeable in nfs mounts"
date: 2018-05-02
forum: General Help
---

### Post by bilkay on 2018-05-02
This started when I "upgraded" my server to 16,04. When I open any libreoffice file on an nfs mount, I get a message that the file is locked by an unknown user. This doesn't happen with sshfs mounts. When this started, the laptop mounting the files was 14.04, but nothing changed after it was "upgraded" to 16.04.

Everything I've found trying to research this points to apparmor, but turning apparmor off on both the client and server doesn't solve the problem. I'm currently using sshfs with autofs but that has another big problem: when I save a file on the client, its ownership changes to root:root on the server.

---

### Post by TheFu on 2018-05-02
Is lockd running?
export options would be useful too.

For the sshfs, which userid is making the mount? That userid will provide the permissions. In short, don't use root for sshfs.

---

### Post by SeijiSensei on 2018-05-03
I have all my documents on an NFS share.  The only time I encounter this problem is with standard LibreOffice file locking.  Then the application will pop up a dialog box to let me choose how to handle the locking.  LO lock files are "hidden," meaning their filenames begin with a dot. They look like this: .~lock.20140410_kynectEnrollmentData.csv#

I've used both NFSv3 and NFSv4 protocols without any locking problems.

It's easy to have stale LO lock files.  The one I listed above is four years old since I haven't tried to open the locked file since.

You can usually enable viewing of hidden files in programs like Nautilus or Dolphin (Alt-period in the latter).  Even easier is to use the command "ls -a" from the command prompt.

---

### Post by bilkay on 2018-05-03
There are no hidden lock files.

```
root@Server:~# ps -ef |grep lockd
root        31     2  0 05:14 ?        00:00:00 [kblockd]
root     18921     2  0 11:12 ?        00:00:00 [lockd]
root     19328 18359  0 11:21 pts/3    00:00:00 grep --color=auto lockd
```

Typical exports options: Laptop(rw,async,no_subtree_check,no_root_squash)

---

### Post by TheFu on 2018-05-03
no_root_squash?  I've never used that. Security issues.

Looks like nfsv4 handles locking internally. It isn't clear how nfsv4 daemons running in v3 mode work to me.
I've never had locking issues.  Just a shot in the dark, but do all userids exist with the same uid/gid numbers on the systems involved?

---

### Post by bilkay on 2018-05-04
> **TheFu said:**
> Just a shot in the dark, but do all userids exist with the same uid/gid numbers on the systems involved?


No problem there. I found another "solution" that didn't work. Commenting out the following lines in /usr/bin/libreoffice was supposed to fix this. It didn't.


#SAL_ENABLE_FILE_LOCKING=1
#export SAL_ENABLE_FILE_LOCKING

---

### Post by SeijiSensei on 2018-05-05
I use no_root_squash all the time. It has no effect on locks if all the uid and gid line up.

---

### Post by bilkay on 2018-05-06
Failed to mention previously that I upgraded Libreoffice to 6 on my laptop. It didn't help.

---

