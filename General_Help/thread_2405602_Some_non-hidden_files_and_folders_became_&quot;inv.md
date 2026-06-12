---
title: "Some non-hidden files and folders became &quot;invisible&quot;"
date: 2018-11-08
forum: General Help
---

### Post by ari.maidana on 2018-11-08
Something very strange is happening in my computer, and I haven't found any similar case so far in any forums. Some files and folders in my home directory have became "invisible". They are not hidden. They just don't show up in the file manager, they don't show up either with ```
ls
``` (not even ```
ls -a
```).

However, if I write the exact path I can access them:
For example, ```
ls
``` doesn't show any directory named "Downloads". Writing "Down" and then hitting tab doesn't complete the word. But if I write ```
cd Downloads
```, I enter the directory.

I don't know where to start with this.

---

### Post by ajgreeny on 2018-11-08
Let us start with command ```
ls -la
``` and if that does not show anything try ```
sudo ls -la
``` to see if we can figure out the ownership and permissions of everything in your home; we can then move on from there.

---

### Post by ari.maidana on 2019-02-03
Both commands 

```
ls -la
```

and

```
sudo ls -la
```

show the same files and directories I can see with a file manager, and have the right permissions and ownership. The "invisible" mentioned before items don't show up at all.

Here are the first lines:

```
ariel@Lutetia:~$ sudo ls -la
[sudo] contraseña para ariel: 
total 492
drwx------ 92 ariel ariel  24576 feb  3 18:51 .
drwxr-xr-x  7 root  root    4096 oct 13 11:54 ..
-rw-rw-r--  1 ariel ariel    166 jul 23  2017 .apport-ignore.xml
drwxrwxr-x  2 ariel ariel   4096 sep 23  2017 .aria2
drwxrwxr-x  4 ariel ariel   4096 nov 30 12:16 .audacity-data

```

**Important information I forgot before.** My home directory is encrypted with Ecryptfs.

---

### Post by HermanAB on 2019-02-04
Note that apart from the common ownership and permissions, there are also lesser known ACLs, AppArmor and SELinux, which can hide stuff from you.  A slightly corrupt file system can also be to blame.

So, I would first schedule a fsck, reboot and then check the permissions, ACLs and AppArmor:

[https://wiki.archlinux.org/index.php/Access_Control_Lists](https://wiki.archlinux.org/index.php/Access_Control_Lists)

[https://help.ubuntu.com/lts/serverguide/apparmor.html.en](https://help.ubuntu.com/lts/serverguide/apparmor.html.en)

---

### Post by ari.maidana on 2019-02-16
I think the problem is related to Ecryptfs. 

If I log in to a virtual terminal, after the usual Ubuntu messages I get this:
```

Could not find key with description: [<key_description>]
Could not find valid key in user session keyring for sig specified in mount option: [<key_description>]
Error parsing options; rc = [-2]
```

Running ls from a virtual terminal (not from a console window) provides this error message:
```
Could not find key with description: [<key_description>]
ecryptfs_parse_tag_70_packet: Error attempting to find auth token for fnek sig [<key_description>]; rc = [-2]
```

before showing only the "visible" files and folders.

---

