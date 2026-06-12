---
title: "need small help fixing a broken ubuntu system"
date: 2008-02-22
forum: General Help
---

### Post by ibuclaw on 2008-02-22
Hi, I don't know how to explain this, but a junior user with sudo privileges on my computer somehow typed in this in the terminal while in his home directory (lets call it /home/user):
```
sudo chown root:root .* -R
```
Which had very disastrous consequencences: For example:
1) Programs couldn't be run
2) Folders couldn't be opened
3) All user folders had been set to ownership to root:root 
4) sudo didn't work
5) su didn't work
6) drives became inaccessible

Apart from booting up and the ability to log in, you name it! It went wrong!

So far I've managed to fix almost everything. In recovery mode:
```

cd /home
chown user1:user1 user1 -R
chown user2:user2 user2 -R
etc...
chmod 4755 /bin/su
chmod 4755 /usr/bin/sudo
chmod 0440 /etc/sudoers

```

That has managed to fix the bulk of everything that went wrong, but I still can't fix the problem with opening disc drives. That includes everything from CDs, DVDs to -Rs and -RWs.

Any quick response help would be appreciated. Thank-you

Iain

---

### Post by ibuclaw on 2008-02-22
OK, more indepth explaination:

The error message:
```

Cannot mount volume.

Unable to mount the volume 'DISCNAME'.

>Details
>>mount: must be a superuser to use mount

```

and my fstab looks like this:
```

# /dev/sdb1
UUID=c698010a-60d1-4133-96de-2794ab67ff50 /               ext3    defaults,erro$
# /dev/sdb3
UUID=3f7dd4b2-b223-439e-ae55-0f9e9f44f18d /home           ext3    defaults     $
# /dev/sda1
#UUID=0EDC5AC0DC5AA1AF /media/.sda1     ntfs    defaults,umask=007       0     $
# /dev/sdb5
UUID=6AB0419AB0416E1F /media/.sdb5     ntfs    defaults,umask=007,gid=46 0     $
# /dev/sdb6
UUID=196d1243-5322-47f6-a969-db99c7064a0d none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by kuja on 2008-02-22
There are a lot of things with unique perms in Linux. Running commands as root is really quite dangerous especially if one doesn't know what they're doing ... If I were you I would be removing that persons sudo privileges :P If there are special cases where this person may need to run certain commands as root you should look into the **sudoers** file(ie: man sudoers). 

If you have a seperate home partition it should be relatively easy to reinstall ubuntu with minimal effort. If you do go this root (which will definitely fix the broken perms), it may be handy to back up the package cache (/var/cache/apt/archives), and the installed packages list (ie: dpkg --list | grep -e ^ii.* | sort | cut -d ' ' -f 3 | tr '\n' ' ' > $HOME/installedpackages .......... sudo apt-get install `cat installedpackages`)

---

