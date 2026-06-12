---
title: "Cannot lock /etc/group or cannot lock /etc/passwd"
date: 2014-03-06
forum: General Help
---

### Post by Upsys on 2014-03-06
Hi - tearing my hair out on this one - I hope somebody can help.

None of the things I've found in other threads here have worked.

Ubuntu 12.04 LTS

Running normally in all other respects. 

When I try any user or group operation (useradd, groupadd, usermod etc) I get the error message:

"Cannot lock /etc/group; try again later."   or the equivalent message for /etc/passwd.

It makes no difference if I get admin privilges by putting "sudo" before the command I am trying,  or by "sudo bash" and then run the command from the root shell prompt.

Other admin only commands work fine.

Rebooting the machine makes no difference.

Other threads suggest deleting lock files, but I cannot find any.

ls -al *.lock finds nothing.

ls -al .*lock finds only .pwd.lock, which is a zero length file.

If I rename or delete .pwd.lock,  then it gets re-created when I try any user or group command, with the same error message.

I have read-write access, because I can modify and delete files in .etc no problem.

I can "chmod 777 /etc/group" and it takes the new permissions, but I still get the same error if I try any group command.

ls -al group*   gives the following output:

-rwxrwxrwx 1 root root 2078 Jul 12  2013 group
-rwxrwxrwx 1 root root 2072 Jul  3  2013 group-

I'm not sure what the group- file is, but re-naming it makes no difference. As you can see, I've set that to permissions 777 as well, in my desperation!

Are there any other lock files hidden away somewhere I need to check?

Help!!!

Many thanks,

Pete

---

### Post by Upsys on 2014-03-12
Looks like nobody has any suggestions :(

Can anyone suggest any other forum where it might be worth posting the question?

Thanks,

Pete

---

### Post by Iowan on 2014-03-12
What's in your */etc/sudoers* file?

---

### Post by steeldriver on 2014-03-12
I suggest you put everything back to the correct default permissions to start

```

$ ls -ald /etc/{,group,passwd,shadow}
drwxr-xr-x 116 root root   12288 Mar  7 06:57 /etc/
-rw-r--r--   1 root root     859 Dec 19 19:23 /etc/group
-rw-r--r--   1 root root    1499 Jan 28 03:17 /etc/passwd
-rw-r-----   1 root shadow  1316 Mar  3 15:21 /etc/shadow

```

You can use lsof to see if there are any other open (potential lock?) files

```

sudo lsof +D /etc

```

Not sure what else to suggest...

---

### Post by matt_symes on 2014-03-13
Hi

As a test, can you edit the files if you enter a root shell ?

```
sudo -i
```
```

usermod ...
useradd ...
...etc...
```

if so then that would suggest a problem with your sudoers file as suggested by iowan.

Kind regards

---

