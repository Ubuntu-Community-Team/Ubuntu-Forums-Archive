---
title: "permissions problem with Samba server"
date: 2014-03-07
forum: General Help
---

### Post by wikeyo on 2014-03-07
Hi all,

I am a linux noob and trying hard to set up a samba server in my home that users can backup to and use for additional storage etc. I have just added a hard drive to the system, but despite my best efforts users only have read permissions for the share on the hard drive! Previously my share folder was on the same drive as the OS and worked perfectly.

This is my smb.conf:


```
workgroup = HOUSE BACKUP
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword$
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

~~~~~~~~~

[Media]
        comment = Ubuntu File Server Media
        path = /mnt/WDRed1/samba/share/Media
        browsable = yes
        guest ok = yes
        read only = no
        directory mask = 0777

```

Here is an la of the folder:  

```
drwxrwxr-x 3 [user] [user] 4096 Mar  6 21:55 Media

```




and a cat /etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3dd66c5e-5f44-4d05-82f0-c7cfa502c579 /               ext4    errors=remount                   -ro 0       1


```

I've tried changing the ownership of the drive to [user]:[user], both at mnt/WDRed1 and at dev/sda & sda1 (the drive appeared as sda rather than sdb at installation), just because I don't know what I'm doing and thought it might help. 

As a bit of a noob I'm sorry you guys probably get this all the time and I've done something a bit stupid somewhere, but any suggestions on where I should begin on solving the problem would be greatly appreciated! Please let me know if there's any further information I could provide that would help diagnose the problem

---

### Post by zero2xiii on 2014-03-07
Hey,

Try these two things:
add to samba.conf
```
 create mask = 0775
```

also do not use 777

```
directory mask = 0775
```

if that does not solve you problem make sure your mount permissions (fstab) is as follow:
```
defaults,umask=000
```

If that does not solve it for you, I am at a loss.

Cheers

---

### Post by wikeyo on 2014-03-07
Hey man, thanks for replying!

I tried this; 

```
[Media]
        comment = Ubuntu File Server Media
        path = /mnt/WDRed1/samba/share/Media
        browsable = yes
        guest ok = yes
        read only = no
        create mask = 0775

```

and restarted smbd, but to no avail.


Thanks for the other suggestion;

```
defaults,umask=000
```

but I'm not entirely sure I've implemented it correctly. I entered; 

```
user@user:/mnt/WDRed1$ umask 000
```

And now my fstab looks like this;

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3dd66c5e-5f44-4d05-82f0-c7cfa502c579 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8be2f4c2-a498-4cee-9346-068a3e9e33f6 none            swap    sw              0       0
/dev/sda1 /mnt/WDRed1 ext4 defaults 0 0

```

I've rebooted the system and smdb but unfortunately no change in access for my windows client.

[IMG]http://i.imgur.com/OySI013.png[/IMG]

Would you have any other suggestions? As I've said, I don't really know what I'm doing so any suggestions would be brilliant. I haven't entered any users in my smb.conf, is that an oversight or is it unnecessary for me?

Thanks again.

---

### Post by wikeyo on 2014-03-09
Does anyone have any other suggestions for what I might have done wrong here? I'd really appreciate any thoughts.

---

### Post by wikeyo on 2014-03-09
Not that anyone was following this, but in case anyone stumbles across this thread in the future:

The problem for me was that I had given the drive an owner. What solved the problem was to run the following command;

```
sudo chown nobody:nogroup -R /mnt/[name of drive]
```

---

### Post by zero2xiii on 2014-03-15
Hay,

Glad you got it solved, sorry for the late reply. If you implemented my above fix of the umask, you would have solved it also. The thing is, the problem is going to reoccur and you will need to chown the drive again after a while. Every file/folder that gets created with an owner will give issues.

See the google lord to find out how to use the fstab to set drive/mount permissions.

Cheers

---

