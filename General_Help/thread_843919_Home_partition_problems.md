---
title: "Home partition problems"
date: 2008-06-28
forum: General Help
---

### Post by MadeOfEyelashes on 2008-06-28
I attempted to place my home drive onto a separate partition, however it didn't work...

I followed the psychocats guide exactly as followed ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome))

However when I boot up Ubuntu(8.04) I get this error:

Users $HOME/.dmrc is ignored
File should be owned by user and have 644 permissions

I push okay then a few seconds later I get this error:

Couldn't locate file /home/nate/.ICEauthority

Help?

---

### Post by pytheas22 on 2008-06-28
Try logging in to the failsafe terminal (you can change the session selecting by clicking on the menu in the bottom-left corner of the login screen) and typing:
```

sudo chmod 755 /home/nate
```

---

### Post by MadeOfEyelashes on 2008-06-29
I tried and it gave me the same errors... :(

---

### Post by drs305 on 2008-06-29
These are the commands you want to run, then reboot.
```

chmod 755 ~/ && sudo chown -R **username** ~/ && chmod 644 ~/.dmrc

```

If it doesn't work, use the recovery mode and do the same from the terminal.

---

### Post by MadeOfEyelashes on 2008-06-29
Sad to say, that didn't work either, it spewed out a whole bunch of errors after I typed it in

---

### Post by bodhi.zazen on 2008-06-30
What errors are you getting ?

What line are you using in /etc/fstab ?

What is the ownership of $HOME and files ?

---

### Post by drs305 on 2008-06-30
The .ICEauthority problem may have started the whole thing, it's not just a .dmrc problem (although that needs solving as well).

Here are two threads that will probably solve the .ICEauthority error. There are suggestions that it occurs due to using sudo instead of gksudo with graphical apps. Maybe...

Anyway, the first thread most closely represents your problem and the second deals primarily with .ICE...

[URL="http://ohioloco.ubuntuforums.org/showthread.php?p=4663269"]! warnings and unable to login
[/URL]

[.ICEAuthority?]("http://ubuntuforums.org/showthread.php?t=824970")

---

### Post by MadeOfEyelashes on 2008-06-30
The line I am using is the next free line that was available 

Every time I try and type in a sudo command I receive a line saying that I can't do a sudo command because of a "setoid" problem 

Also I can't change the permissions of ~/.dmrc and ~/.ICEauthority because it says they don't exist...

---

### Post by drs305 on 2008-06-30
If you can't use sudo, try this:
Reboot to the recovery mode (root command line) via the Grub menu.
Run these commands to change ownership and permissions. The last command will reboot to the normal grub menu/logon:

```

sudo chown nate /home/nate
sudo chmod 755 /home/nate
sudo chown nate /home/nate/.dmrc
sudo chmod 644 /home/nate/.dmrc
sudo shutdown -r now

```

This should eliminate the .dmrc permission problems and may eliminate the .ICE error message. Let us know.

---

### Post by MadeOfEyelashes on 2008-06-30
I don't have recovery mode on my boot menu (my fault >.<)

Is there any other way to access it?

---

### Post by VMC on 2008-06-30
> **MadeOfEyelashes said:**
> I don't have recovery mode on my boot menu (my fault >.<)

Is there any other way to access it?

Have you tried push ESC on reboot and edit grub and then add at end of line "single".

Somewhere recently someone had a quick way to boot down to single user level. If I find it I edit this.

Edit: I found this solution to shutdown to single user:

From a command line, you can use the init command to go immediately into runlevel 1, which is also known as single user text mode. Open terminal and type the following command:

sudo init 1

Again get back to GUI with init 2 command:

sudo init 2

When you type init 1 command your session will then begin to shut down and bring you into single user text mode. When you type init 2 command your session will then begin to shut down and bring you into GUI mode

---

### Post by MadeOfEyelashes on 2008-06-30
I got into recovery mode and I tried doing sudo chown nate /home/nate and it said 

sudo: unable to resolve host (none)
sudo: /etc/sudoers is owned by uid 1000, should be 0

---

### Post by VMC on 2008-07-01
Output the result of:

```
cat /etc/hostname
```

---

### Post by bodhi.zazen on 2008-07-01
> **MadeOfEyelashes said:**
> I got into recovery mode and I tried doing sudo chown nate /home/nate and it said 

sudo: unable to resolve host (none)
sudo: /etc/sudoers is owned by uid 1000, should be 0

To me that error message implies deeper problems then /home and the advice on this thread.

It looks like you changed permissions on system files -> broken ubuntu.

It is often difficult if not impossible to restore system settings, and unless you changed one or two files looks like re-installation is in your future.

My only other thought would be fstab. Can you post the contents of /etc/fstab ?

---

### Post by soccerboy on 2008-07-01
> **bodhi.zazen said:**
> To me that error message implies deeper problems then /home and the advice on this thread.

It looks like you changed permissions on system files -> broken ubuntu.

It is often difficult if not impossible to restore system settings, and unless you changed one or two files looks like re-installation is in your future.

My only other thought would be fstab. Can you post the contents of /etc/fstab ?

check your /etc/hosts file. post contents?

---

### Post by MadeOfEyelashes on 2008-07-01
fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
uuid=f8034d5b-a8f9-4a5a-belc-cff9e7d65d06 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda6
uuid=307ddcf5-37aa-4af2-8302-a835bleabcfb none swap sw 0 0
/dev/scd0 /medai/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /home ext3 nodev,nosuid 0 2




hosts: 
127.0.0.1 localhost
127.0.1.1 nate-laptop

#the following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6=localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


cat /etc/hostname:
ubuntu


Those are the three things people wanted me to post :-P

---

### Post by soccerboy on 2008-07-01
i believe the output of /etc/hostname and the ip address 127.0.1.1 are supposed to read the same thing.

---

### Post by MadeOfEyelashes on 2008-07-01
The last time I did it it was in the Live CD, this time I did it in the failsafe terminal and I got 

nate-laptop

Sorry about that >.<

---

### Post by soccerboy on 2008-07-01
then i am not sure why your hostname is not resolving.  You should be able to do sudo without problems.

---

### Post by MadeOfEyelashes on 2008-07-02
I gave up and reinstalled Linux, thank you very much everyone :)

---

