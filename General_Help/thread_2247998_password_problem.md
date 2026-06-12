---
title: "password problem"
date: 2014-10-11
forum: General Help
---

### Post by jgw on 2014-10-11
I am running with ubuntu 14.04  I was having a problem with passwords on one of 4 machines on my network.  Now, however, I no longer have a functional sudo password.  I still have a functional su password, however.  I can also restart my machine and get logged in automatically.

As far as I can tell I have a samba password (have no idea what the password is, however) which may be my problem on this machine.  As far as the sudo password is concerned I have no idea how to change that, or enter a new one.  The sudo password has been working fine and then no more.  This is all very strange to me.  I thought of using passwd to fix this problem but I have no idea what password that program is dealing with as I seem to have a lot of different passwords.  I read some documentation that said that passwd is available to deal with the user account password.  I always thought that the user account password was the main password to login with but I guess that's not right.

Thank you................

---

### Post by TheFu on 2014-10-12
switch to root, then run 
# **passwd** {username}
to set a new password for that other account.

**man passwd**
will explain any more details you need.

The system you are on is confusing you due to the automatic login. Normally, the same password is used for
* login on the console
* sudo
* login from remote systems via ssh

The samba password may or may not be the same.  Use smbpasswd to reset it to match the Linux password - most samba configurations will keep those synchronized going forward.

---

### Post by jgw on 2014-10-12
Thank you for the reply.

Went to a terminal and did an su - that took me to the root too
I then did passwd username

I then did smbpasswd name and reset that password

I then tried sudo and that worked fine (sudo gedit and gksu gedit)

then I went to browse network, clicked on this machine, it asked for a password and I gave it the same one I gave to both the above.  That one failed.   I am half there, now.  All I have to figure out is what password I could possibly need to open this machine when doing it through the network.  (It behaves exactly the same when trying to access this machine with another - just keeps asking for the password)  I have, obviously, setup this machine wrong.  I can access 3 of the other network machines but this one, while recognized, has some kind of strange password which I have not been able to figure out.  I have no idea what is asking for the password nor what it might be.

---

### Post by TheFu on 2014-10-12
I think part of the confusion is that you are using "root" when Ubuntu is designed NOT to use root at all. Instead, Ubuntu is designed around using "sudo" to temporarily elevate the privilege level. 

Mixing a root password into this seems to be confusing.  There isn't ANY reason to have a root password on an ubuntu system today.  Use **sudo -i** or **sudo -s** if you want more than one command with elevated privileges. Normally sudo cmd should be used.

BTW - be very careful running GUI programs as root or with sudo. There are many reasons to avoid this, mainly because preferences will be owned not by the userid, but root. This can be bad later, unless the -u option is specified.

The **passwd username** - should have set the new password for "username" - use that to connect from remote locations with standard UNIX tools (ssh, sftp, scp, etc). NOT for CIFS file access via samba. That uses the password set via smbpasswd - if those are NOT the same ....  I don't use CIFS very much, preferring more secure methods like sftp instead.  The file manager from almost any Linux GUI will support sftp:// .

The error you describe above could be that nmbd wasn't restarted or that the host trying to access the server doesn't have a good mapping in the /etc/hosts or via DNS too. Hard to tell from here.

---

### Post by jgw on 2014-10-12
Thanks for the reply.

I have tried ssh and failed miserably.  If I try and connect the machine I am using the connection is refused.  If I try to access another machine (which I can get to with browse network) I get nothing, just a blinking cursor.  I, obviously, am doing something wrong.  My attempt at another machine was "ssh 192.168.0.5" (that's the only other ip address I know on my network).

---

### Post by TheFu on 2014-10-12
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH) should be helpful - I suspect the **openssh-server** hasn't been installed on the remote machine. The ssh-client does get installed everywhere - plus there are clients for every platform I know that supports networking. It is not installed on desktops by default (for some unknown reason).

---

### Post by jgw on 2014-10-13
thank you............

I installed openssh-server and restarted and it made no difference.  I do know that one machine is using eth1 and the other eth0 (have no idea if that makes any difference at all.

I have now, however, lost the password to unlock my ring.  Its as if I have something in my machine that is messing with one password at a time.

---

### Post by TheFu on 2014-10-13
Check the firewall.  If that doesn't solve this, I'd wipe the disk and reload.
ssh is one of those things that is 10 seconds of effort normally. There is something odd about the setup you have. Get this working on the other machines, then try on the trouble box.

---

