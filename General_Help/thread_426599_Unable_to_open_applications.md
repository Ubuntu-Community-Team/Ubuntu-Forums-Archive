---
title: "Unable to open applications"
date: 2007-04-28
forum: General Help
---

### Post by GVM on 2007-04-28
Hi

When I try to open **system - adminstration - users and groups or synaptic package manager** nothing happens. I have only one user registered on by start up:confused:

---

### Post by taurus on 2007-04-28
Open a terminal, Applications -> Accessories -> Terminal, and post the output of this command.

```
id
```

---

### Post by GVM on 2007-04-28
got the following

gvm02@GVM02:~$ id
uid=1000(gvm02) gid=1000(user) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(user)
gvm02@GVM02:~$ su
Password: 
root@GVM02:/home/user# id
uid=0(root) gid=0(root) groups=0(root)
root@GVM02:/home/user#

---

### Post by taurus on 2007-04-28
Get out of the su and get back to your user account.  Then, what happens when you run this command from a terminal?

```
sudo aptitude update
```

---

### Post by GVM on 2007-04-28
Got this 

gvm02@GVM02:~$ sudo aptitude update
sudo: unable to lookup GVM02 via gethostbyname()
gvm02@GVM02:~$

---

### Post by taurus on 2007-04-28
Okay, you somehow screw up /etc/hosts or/and /etc/hostname.  Can you post both of them here.

```
cat /etc/hostname
cat /etc/hosts
```
The name that you use in /etc/hostname should be the same as the one in /etc/hosts or else you would get that kind of error message.

---

### Post by GVM on 2007-04-28
got this


gvm02@GVM02:~$ cat /etc/hostname
GVM02
gvm02@GVM02:~$ cat /etc/host
cat: /etc/host: No such file or directory
gvm02@GVM02:~$

---

### Post by taurus on 2007-04-28
You are missing an s at the end.

```
cat /etc/host[COLOR="Red"]s[/COLOR]
```

---

### Post by GVM on 2007-04-28
Sorry - got this

gvm02@GVM02:~$ cat /etc/hosts
127.0.0.1 localhost 4217home
127.0.1.1 ubuntu.home.net ubuntu.HOME.NET

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
0.0.0.0 4217home

gvm02@GVM02:~$ cat /etc/hostname
GVM02
gvm02@GVM02:~$

---

### Post by taurus on 2007-04-28
> **GVM said:**
> Sorry - got this

gvm02@GVM02:~$ cat /etc/hosts
127.0.0.1 localhost 4217home
**[COLOR="Red"]127.0.1.1 ubuntu.home.net ubuntu.HOME.NET[/COLOR]**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
0.0.0.0 4217home

gvm02@GVM02:~$ cat /etc/hostname
**[COLOR="Red"]GVM02[/COLOR]**
gvm02@GVM02:~$

That's where your problem is.  Boot into recovery mode from GRUB menu and edit /etc/hosts.

```
nano -w /etc/hosts
```
Then, replace this line

```
127.0.1.1 ubuntu.home.net ubuntu.HOME.NET
```
with this one.

```
127.0.1.1 GVM02
```
Save and exit with <Ctrl>o and <Ctrl>x.  Reboot with

```
shutdown -r now
```
Now, see what happens when you run this command from a terminal?

```
sudo aptitude update
```

---

### Post by GVM on 2007-04-28
Did all that and got this

gvm02@GVM02:~$ cat /etc/hosts
127.0.0.1 localhost 4217home
127.0.1.1 GVM02

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
0.0.0.0 4217home
gvm02@GVM02:~$ cat /etc/hostname
GVM02

gvm02@GVM02:~$ sudo aptitude update
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
gvm02@GVM02:~$

---

### Post by taurus on 2007-04-28
Boot into recovery mode again from GRUB menu and modify /etc/hosts

```
nano /etc/hosts
```
and make it look like this now.

```
127.0.0.1 localhost GVM02
#127.0.1.1 GVM02

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
#0.0.0.0 4217home
```
Reboot back to normal mode and see what happens when you run this command from a terminal?

```
sudo aptitude update
```

---

### Post by GVM on 2007-04-28
did that got this - still not opening user and groups - could it be a case sensitive problem - I use lower case when logging in?

root@GVM02:/home/user# cat /etc/hosts
127.0.0.1 localhost GVM02
127.0.1.1 GVM02

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
#0.0.0.0 4217home

root@GVM02:/home/user# cat /etc/hostname
GVM02

root@GVM02:/home/user# sudo aptitude update
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
root@GVM02:/home/user#

---

### Post by taurus on 2007-04-28
Boot back into recovery mode and place a # in front of this line in /etc/hosts.

```
nano /etc/hosts
```
```
#127.0.1.1 GVM02
```
Also, what does your /etc/sudoers look like?

```
more /etc/sudoers
```
Hit the space bar for the next 24 lines if the file has more than 24 lines.

---

### Post by GVM on 2007-04-28
did that got this

root@GVM02:/home/user# nano /etc/hosts
root@GVM02:/home/user# more etc/sudoers
etc/sudoers: No such file or directory
root@GVM02:/home/user#

---

### Post by taurus on 2007-04-28
> **GVM said:**
> did that got this

root@GVM02:/home/user# nano /etc/hosts
root@GVM02:/home/user# more etc/sudoers
etc/sudoers: No such file or directory
root@GVM02:/home/user#

```
more **[COLOR="Red"]/[/COLOR]**etc/sudoers
```

---

### Post by GVM on 2007-04-28
got this

root@GVM02:/home/user# more /etc/sudoers
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Entries for Smb4K users.
# Generated by Smb4K. Please do not modify!
User_Alias      SMB4KUSERS = gvm02
Defaults:SMB4KUSERS     env_keep="PASSWD USER"
SMB4KUSERS      GVM02 = NOPASSWD: /usr/bin/smb4k_kill
SMB4KUSERS      GVM02 = NOPASSWD: /usr/bin/smb4k_umount
SMB4KUSERS      GVM02 = NOPASSWD: /usr/bin/smb4k_mount
# End of Smb4K user entries.
root@GVM02:/home/user#

---

### Post by GVM on 2007-05-01
As it appeared that I had some how made a mess of the timing on my Ubuntu engine I decided to reload the whole thing. I am now back up and running
Big thanks to Taurus for patients and for the loss of hair that was pulled out. Next time I open the bonnet (hood) on my Ubuntu engine I will get some advice.
Taurus - any time you are in NZ you can have a free night at our B&B Sawmill Cottage

---

