---
title: "Ubuntu 16.04LTS boot time errors - part 2"
date: 2020-09-23
forum: General Help
---

### Post by Frank P on 2020-09-23
I get the following error on bootup
```

unsafe symlinks encountered in /var/run/sshd refusing

```

followed by some other errors I'll leave for now

There is no file or directory called sshd in /var/run
Can anybody tell me whats going on and how to fix it?
Thanks

---

### Post by #&amp;thj^% on 2020-09-23
Just for good measure would you also show:
```
stat /root
```

---

### Post by Frank P on 2020-09-23
Results of stat /root
```

  File: '/root'
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d    Inode: 9699329     Links: 9
Access: (0700/drwx------)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2020-09-23 16:09:01.546352772 -0400
Modify: 2016-09-10 21:57:23.580336529 -0400
Change: 2016-09-10 21:57:23.580336529 -0400
 Birth: -

```

---

### Post by #&amp;thj^% on 2020-09-23
Thanks, looks like this should work for you.
```
chown root.root / 
```
Show any Diff's

---

### Post by Frank P on 2020-09-23
no output from chown root.root /
output from rerunning stat /root

```

  File: '/root'
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d	Inode: 9699329     Links: 9
Access: (0700/drwx------)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2020-09-23 16:09:01.546352772 -0400
Modify: 2016-09-10 21:57:23.580336529 -0400
Change: 2016-09-10 21:57:23.580336529 -0400
 Birth: 

```

what now?

---

### Post by #&amp;thj^% on 2020-09-23
> **Frank P said:**
> 

what now?

IDK, gosh its been 7 years or more since I used 16.04.
I remember issues with systemd and the new way it started "sshd ".
Outside of this is there any other problems with this system? It runs though right?
Memory jog>>>you did use
```
sudo chown root:root /
``` right?

Now a quick glance at some old notes i keep, I found that **/var/run** is a symbolic link to** /run**, I do not know why this is needed, but when I modified the content of the file **/usr/lib/tmpfiles.d/sshd.conf** from:
```

d /var/run/sshd 0755 root root
```

to:
```

d /run/sshd 0755 root root
```

if everything goes well on system startup, the SSH service is started normally and should be able to log-in via SSH.
Hope something here helps you.

---

### Post by Frank P on 2020-09-23
server was running fine prior to the update about a week or so ago. I think it failed updating openssh-server. Not positive but thats the problem now.
You can ping to it or from it; openssh-client is still working; apache2 and mysql are both okay; nfs & samba both okay.

The only problem is trying to reinstall openssh-server. It errors with
```

dkpg error processing openssh-server (--configure)
subprocess installed post-installation script returned error exit status 1
```

There are a couple of other errors I never noticed but I think they've been there a long time and don't cause any problems -
    failed to create volatile files and directories
    cannot connect to upstart

---

### Post by #&amp;thj^% on 2020-09-23
> **Frank P said:**
> 

The only problem is trying to reinstall openssh-server. It errors with
```

dkpg error processing openssh-server (--configure)
subprocess installed post-installation script returned error exit status 1
```

There are a couple of other errors I never noticed but I think they've been there a long time and don't cause any problems -
    failed to create volatile files and directories
    cannot connect to upstart

Now it's coming back to me "upstart" and "systemd" what fun that was early on....anyway see this to possibly help:[https://askubuntu.com/questions/810523/can-not-install-openssh-server](https://askubuntu.com/questions/810523/can-not-install-openssh-server)

---

### Post by #&amp;thj^% on 2020-09-24
Hello Frank P
How do we set right now?
If facing the same problems, please also show this:>(**_Before moving on _**to the workaround)
```
journalctl -b 0 -u systemd-tmpfiles-setup.service
```
And also
```
uname -a
```
Also one more check on permissions:
```
stat -c "%U %G" /

```
Should look like:
```
root root
```
And this too:
```
stat -c "%U %G" /var/

```
Should look like:
```
root root
```
Seems there was a recent update that did not mix well with systemd.
A fix/workaround was posted to downgrade systemd via:
Run one line at a time:
```
cd /home/
wget launchpadlibrarian.net/392626140/libsystemd0_229-4ubuntu21.5_amd64.deb
wget launchpadlibrarian.net/392626138/libpam-systemd_229-4ubuntu21.5_amd64.deb
wget launchpadlibrarian.net/392626148/systemd_229-4ubuntu21.5_amd64.deb
dpkg -i libpam-systemd_229-4ubuntu21.5_amd64.deb systemd_229-4ubuntu21.5_amd64.deb libsystemd0_229-4ubuntu21.5_amd64.deb
apt-mark hold systemd libsystemd0 libpam-systemd
reboot
```
At this point if nothing I've shown has worked, Then I strongly urge an upgrade to 18.04LTS, as a good system practice. (If possible)

---

### Post by Frank P on 2020-09-24
[COLOR=#000000]Still the same problem. Here are responses

If facing the same problems, please also show this:>([/COLOR][B]_Before moving on _to the workaround)
Code:
journalctl -b 0 -u systemd-tmpfiles-setup.service
no entries
And also
Code:
uname -a
linux t110 4.4.0-190generic #220-ubuntu Fri Aug 28 etc
Also one more check on permissions:
Code:
stat -c "%U %G" /
0 0
And this too:
Code:
stat -c "%U %G" /var/
root root
Seems there was a recent update that did not mix well with systemd.
A fix/workaround was posted to downgrade systemd via:
Run one line at a time:
Code:
cd /home/
wget launchpadlibrarian.net/392626140/libsystemd0_229-4ubuntu21.5_amd64.deb
wget launchpadlibrarian.net/392626138/libpam-systemd_229-4ubuntu21.5_amd64.deb
wget launchpadlibrarian.net/392626148/systemd_229-4ubuntu21.5_amd64.deb
dpkg -i libpam-systemd_229-4ubuntu21.5_amd64.deb systemd_229-4ubuntu21.5_amd64.deb libsystemd0_229-4ubuntu21.5_amd64.deb
apt-mark hold systemd libsystemd0 libpam-systemd
reboot


[/B]The recent update would seem to be the problem. I'll wait till you've had a look at this reply before I use the work around.
I don't want to risk an upgrade to 18.04 on a broken system. Did that about a year ago on a test system and it was a real mess. Had to fall back
Oops - sorry for the formatting

---

### Post by #&amp;thj^% on 2020-09-24
I don't like this:
```
stat -c "%U %G" /
0 0
```
Are you logged in as Root?
If needed:
```
whoami
```
EXAMPLE:
```
whoami
me

```
Normal^^^^
And
```
# whoami
root

```
ROOT^^^^

---

### Post by Frank P on 2020-09-27
have found a partial solution on google but it generates another question
After rebooting and openssh server failing ran following 

```

sudo mkdir /var/run/sshd
sudo service sshd start

```

can now ssh in but when the server is rebooted the /var/run/sshd is no longer there.
How do I make the fix permanent
Thanks

---

### Post by Frank P on 2020-09-28
found a hopefully, permanent, solution via google
```

[COLOR=#242729][FONT=Arial]Modify /usr/lib/tmpfiles.d/sshd.conf in the following way:[/FONT][/COLOR]
d /run/sshd 0755 root root

```

my previous fix had to be reentered after a reboot
Thanks

---

