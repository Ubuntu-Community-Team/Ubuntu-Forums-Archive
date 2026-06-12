---
title: "&quot;transfer&quot; file ownership without root access?"
date: 2007-12-17
forum: General Help
---

### Post by jjalocha on 2007-12-17
I am trying to "transfer" file ownership to another user, without using sudo for root access. (In my case this is not an option, since I'm setting this up for other non-privileged users).

I would like to change the following file:
```

-rw-rw-r-- 1 user-a user-a ... testfile

```
so that it belongs to user/group 'user-b'.

I have the following set-up:
[LIST]
[*]file in '/home/user-a' directory, mounted in '/etc/fstab' as '/home ext3 defaults 0 2'.
[*]'user-a' user belongs to 'user-a' and 'user-b' groups.
[*]'user-b' user belongs to 'user-a' and 'user-b' groups.
[/LIST]

I can't change ownership as 'user-a':
```

user-a@myhost:~$ chown user-b: testfile
chown: changing ownership of `testfile': Operation not permitted

```

I can't change ownership with 'sudo -u':
```

user-a@myhost:~$ sudo -u user-b chown user-b: testfile
chown: changing ownership of `test': Operation not permitted

```

I've also tried the 'chown user-b:user-b' variant without success. Anyone knows what I'm doing wrong?

---

### Post by geraldm on 2007-12-17
Do not confuse write permissions in the group of a file with who has permission to change ownership of the file.  The group permissions deal only with permission to change the contents of the file.  
To change the owner of a file, control of both the user and the new owner is needed.
Root can do this; any one user cannot change it in most systems.  
There is some fine tuning of the sudo command that can be done when the system is set up to allow transfer of ownership under sudo.  Refer to the manpage for sudo to identify what is needed to make such a transfer (it appears to be possible only in specific directories, with the use of a timestamp).  How to setup the system to allow sudo ownership transfer is a dark art.

Gerald

---

### Post by bingoUV on 2007-12-17
You have to be root once to give the users the permission to run a command as root.
Edit the /etc/sudoers file to allow the non-root user to run this particular command, with or without giving their password (their own password , not root password). This link gives a way to run a command as root without password.

[http://ubuntuforums.org/showpost.php?p=3768173&postcount=7](http://ubuntuforums.org/showpost.php?p=3768173&postcount=7)

---

### Post by Dryw Paulic on 2007-12-17
Hi jjalocha,

It is also important to note that chown is supposed to act this way for security reasons.  When chown was originally created any user could run chown. However that led to problems with people getting around disk quota limits and breaking other users files, so they changed it so only root can run chown.

As Geraldm said, you can configure sudo to do more fine-grained control of thus stuff. For example, I setup a test bed with user-a and user-b as you did, but then added the following to my sudoers file.

```
# User alias specification
User_Alias CHOWNERS = user-a, user-b
```

```
# User privilege specification
root    ALL=(ALL) ALL
CHOWNERS ALL =  /bin/chown
```

This allows user-a and user-b to use sudo to run chown as root. Note. This is very dangerous if these users simply exist on your system, as it gives them the ability to run chown **anywhere** on the system. If you do not want this, the only way I know of somewhat restricting the usage of the command would be to jail the two users. 

A good example on how to do so could be found here:

[http://olivier.sessink.nl/jailkit/howtos_chroot_shell.html](http://olivier.sessink.nl/jailkit/howtos_chroot_shell.html)

-Dryw

---

### Post by geirha on 2007-12-17
If user-b has read access to the file (which it has in your example), user-b can copy the file. The new file will then be owned by user-b, while the original will be owned by user-a. 

And also, if user-b has write access to the directory containing the file, user-b can delete the original file afterwards (as long as the directory containing the file doesn't have the sticky-bit set)

And if the operation happens to be on the same filesystem (and the filesystem supports hardlinking), you can hardlink instead of copying.

So it is somewhat possible without root access, but both users need to be involved, and should have a group in common.

---

### Post by jjalocha on 2007-12-17
I really got a lot of answers!
Thank you very much for all your help!

[LIST]
[*]I really don't want other users to have access to chown, since this is really very dangerous in the hands of unqualified users.

[*]I thought that having access to both groups should grant me the right to change the file's ownership. I see, that this is really not possible in Linux. (This looks like a design flaw to me.)

[*]Setting up a jail is overkill for this specific case.
[/LIST]

Thus, I will stick to the method I've been using so long: I will change ownership myself whenever this is necessary. I really feel more comfortable this way.

Anyway, all the suggestions/links made a very interesting reading, and I got a deeper understanding of chown and sudoers.

Thank you very much for that!

---

### Post by jjalocha on 2007-12-17
geirha: I just read your post, after writing the previous answer.

Your solution works perfect for me. It's no very elegant, but it does the job perfectly. And since I want to run this from a script, it shouldn't be too hard for the user.

My setup:

[LIST]
[*]'user-a' user belongs to 'user-a' and 'user-b' groups.
[*]'user-b' user belongs to 'user-b' group.
[/LIST]

How it works:
```

user-a@myhost:~$ sudo -u user-b cp testfile testfile.tmp
user-a@myhost:~$ rm testfile
user-a@myhost:~$ sudo -u user-b mv testfile.tmp testfile

```

Note, that the 'rm' command can also be performed as 'user-b'.

Thanks!

---

