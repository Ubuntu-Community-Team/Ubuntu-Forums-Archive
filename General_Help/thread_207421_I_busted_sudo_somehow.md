---
title: "I busted sudo somehow"
date: 2006-07-01
forum: General Help
---

### Post by vicarious on 2006-07-01
This problem exists on a new install of Dapper Server.

I installed the server, everything went well. Afterwards, I wanted to install a bunch of things and got tired of using sudo repeatedly so I set up a root password. Later on, I started reading the manual (heh, *after* installation) and saw that I could use 'sudo -i' and I did not need a root account. So I logged into the server via ssh, su'd to root one last time, double checked the /etc/sudoers file (it is unchanged from install), and issued 'passwd -l root' and then logged out.

I am not sure the first part is related to my problem, but I included it just to be complete. Later when I went to do some maintenance, I logged back on and sudo does not work. **The command when entered by itself, 'sudo', spits out the help message as expected. When I enter 'sudo' and then a command or a flag afterwards, nothing at all happens.** The command does not get executed, there are no errors, nothing. 

e.g. I can enter 'sudo I am a hairy newt' and it doesn't complain. I can enter 'sudo echo foo' and nothing happens.

So, now I can't do anything that requires root privledges (without chrooting from the livecd and setting the root password) and I don't know what else to do to troubleshoot sudo. The /etc/sudors file, like I said earlier, is unchanged from a default install.

---

### Post by AlphaMack on 2006-07-01
Are you listed in the admin group?  Have you tried to boot into SUM and use adduser?

```
adduser username admin
```

Where username is your user name.

---

### Post by tonyr on 2006-07-01
Well, 'passwd -l root' **locks**  the root password/account; it does not **delete** the
password.  
With 20-20 hindsite, you should have said 'sudo passwd -d root', which would have left
the root account intact but without login access.

I'm not sure if this will work, but you could try **sudo passwd -u root**.  I know, it
appears on the surface to be fruitless, but who knows?

Another approach is to do that thing you said, boot the live cd, and edit 
**/etc/shadow** in the real root partition to remove the root password.

---

### Post by vicarious on 2006-07-01
[QUOTE=alphasubzero949]Are you listed in the admin group?  Have you tried to boot into SUM and use adduser?

```
adduser username admin
```

Where username is your user name.[/QUOTE]

Yeah, that fixed it. Thank you.

---

### Post by zek725 on 2006-11-02
my sudo problem is that anything that goes with sudo returns these errors:
```
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
```

I'm in Xubuntu. For networking reasons, I tried smb4k (with which Konqueror came with it). I think that was the cause. I believe Kubuntu does not use sudo but su instead. But then, I'm unfamiliar with Kubuntu so this has become a hassle. Help! How do I restore/fix this sudo problem!

---

### Post by aysiu on 2006-11-02
> **zek725 said:**
> my sudo problem is that anything that goes with sudo returns these errors:
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

I'm in Xubuntu. For networking reasons, I tried smb4k (with which Konqueror came with it). I think that was the cause. I believe Kubuntu does not use sudo but su instead. But then, I'm unfamiliar with Kubuntu so this has become a hassle. Help! How do I restore/fix this sudo problem!
This link will help you out:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by zek725 on 2006-11-02
Ah yes. thank you! I don't know how these lines were inserted in /etc/sudoers

```
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
```

Ah yes. I remember another terminal with konqueror launched from the terminal was open. Ha! It doesn't make sense!

---

