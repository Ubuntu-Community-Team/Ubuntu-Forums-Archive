---
title: "Ubuntu 22.04.3 LTS on Raspberri Pi Zero 2W and /dev/ttyS0 permissions"
date: 2023-08-24
forum: General Help
---

### Post by c172jeff on 2023-08-24
Hello,
  I installed Ubuntu 22.04.3 LTS on a Raspberry Pi Zero 2W.  I installed the Server version of the  Ubuntu software.  I also installed ROS2 (for Robotics) as well as other software related to accessing a serial port.

After all the software was installed, I am now stuck trying to solve a problem related to the raspberri pi user account (pi) and permissions of /dev/ttyS0.   I have an Arduino connected to the raspberri pi on the tx and rx pins.  

A ls of ttyS0 shows.

pi@CapellaDev:~$ ls -l /dev/ttyS0
crw--w---- 1 root tty 4, 64 Aug 24 16:29 /dev/ttyS0
pi@CapellaDev:~$




I have read the posts that the account pi needs to be a member of the dialout group, for which it is.  It is also a member of the ttys group.

The pi cannot read from /dev/ttyS0

It can in fact write to it.

What is governing the permissons of ttyS0?

When I change it with chmod, it soon changes back.

More importantly, why would ttyS0 have write permissions for group and not read and write?
I think I should probably be using /dev/serial0 , ut that is basically /dev/ttyS0

How can I change the permissions of /dev/ttyS0 so that it is Read and Write for my pi account?

Thanks
Jeff

---

### Post by MAFoElffen on 2023-08-24
As I remember, permissions to serial ttys0 is
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 Aug 23 16:13 /dev/ttyS0

```
So is the 'dialout' group... and if you try to change the port's ownership to a different group, that it ends up only being temporary, because there is a udev rule that checks what the ownership of that is and if different, will reset it back to 'dialout', unless you have another local udev rule written to override that. (see below)

You could create a file called 90-local.rules in '/etc/udev/rules.d' then add the line
```

KERNEL=="ttyS[0-9]*", NAME="tts/%n", SYMLINK+="%k", GROUP="uucp", MODE="0666"

```
and add your user 'pi' to that group... Which is a work-around for minicom, ...or just forego all that and just add user 'pi' to group "dialout", which is the owner's group for that port by default...

Right?

---

### Post by c172jeff on 2023-08-24
Well, that did not work.

In my install, for whatever reason my permissions on ttyS0 are different than yours. If they were the same, I do not think I would have a problem.  The pi user on my install is a member of the dialout group.

When I created the file you mentioned in 

[COLOR=#000000]/etc/udev/rules.d[/COLOR]

that did not fix the problem. After a reboot, the ttyS0 had the same permissions as before.  II tried to add the pi user to the group uucp.

When I did this, I wiped out all the prior groups the pi was previously added to.  I am considering a reinstall of everything.

---

### Post by MAFoElffen on 2023-08-25
I don't understand how adding a user to a group would wipeout all it's previous groups. I honestly have never seen that happen.

I just rechecked my laptop, two of my servers, and my Rasp Pi4... All four of them are running Ubuntu 22.04.3 LTS, and have the same permissions and ownership as I posted-- with owner (user) as root, and owner (Group) as dialout.

The output you posted was this:
```

pi@CapellaDev:~$ ls -l /dev/ttyS0
crw--w---- 1 root [COLOR=#ff0000]tty[/COLOR] 4, 64 Aug 24 16:29 /dev/ttyS0

```
...which doesn't make sense. 'tty' is not a (default) group. ??? Something is wrong there.

---

### Post by c172jeff on 2023-08-25
When I added the pi group to uucp, and wiped out my other groups, I must have done it incorrectly for that to happen.  After I did what I did, my groups for pi were [pi and uucp]
 
I used a command which I though would do the add group safely and it must have used a replacement option instead of one with an add option.9  In any case, the groups were changed.  The new install (today) shows these groups (for reference, for pi user)

[pi adm dialout cdrom sudo audio video plugdev games users input render netdev gpio spi i2c]



ROS2 needed install of 22.04.03 to use binaries that were pre built.

Yesterday, I installed the latest version of Ubunto (trying to rebuild ROS2 from source).  The build of ROS2 did not go so well so I am back to Using 22.04.03.  I just did a reinstall of 22.04.03 to get the groups shown above.

When I installed 23.04 Ubunto, my ls of /dev/ttyS0 shows as yours (correct with the rw attribute).

When I installed 22.04.03 Ubunto, my ls of /dev/ttyS0 shows as before.

pi@CapellaDev:~$ ls -l /dev/ttyS0
crw--w---- 1 root tty 4, 64 Aug  7 11:35 /dev/ttyS0
pi@CapellaDev:~$



I do not understand why ttys0 is in the group tty.  The install just completed and I have not added anything else.

I am using a Pi Zero 2w and a terminal program from Windows 10.
How is this correctable to change the file to be proper so I can work with it?  
I will look more at udev if that is what the fix is.  Maybe I can create  a new device and use that instead of ttyS0?

Jeff

---

### Post by c172jeff on 2023-08-25
Ok, Here is the fix...........

Last login: Fri Aug 25 08:33:41 2023 from 2601:182:700:9940:d136:17b:9fc6:999b
pi@CapellaDev:~$ ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 Aug  7 11:34 /dev/ttyS0
pi@CapellaDev:~$


To achieve this, for future reference

One must install raspi-config on Linux and then disable the serial shell options and enable the serial port for use by applications 

Basically, use rasp-config to fix the problem.

What that does exactly...who knows????

---

### Post by MAFoElffen on 2023-08-25
So... I would post a bug report on that to Launchpad. Just so they are aware there is a problem there, and your fix as a work-around to that problem.

(I feel) It shouldn't do that...

Not sure what to file it against though. 

EDIT: 
In RedHat Bugzilla-- Where I see Bugs filed against ttyS0 expected behaviors get funneled to filed against "kernel'.

---

