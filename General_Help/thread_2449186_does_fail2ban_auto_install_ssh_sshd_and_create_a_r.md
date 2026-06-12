---
title: "does fail2ban auto install ssh sshd and create a root account in ubuntu"
date: 2020-08-21
forum: General Help
---

### Post by xtenr on 2020-08-21
does fail2ban auto install ssh sshd and create a root account in ubuntu  are ssh and sshd installed by default on ubuntu? how would i see if there are installed in sudo apt what?  also i have been messing around im 99.9% sure i have not created a root user but how would i check, whats the command that only me standard user with sudo is enabled and not the root  if i have accidently installed a root user whats the command to remove it and do i need to reboot after?  thx

---

### Post by xtenr on 2020-08-21
are ssh and sshd installed by default on ubuntu? how would i see if there are installed in sudo apt what?  also i have been messing around im 99.9% sure i have not created a root user but how would i check, whats the command that only me standard user with sudo is enabled and not the root  if i have accidently installed a root user whats the command to remove it and do i need to reboot after?  thx

---

### Post by guiverc on 2020-08-21
You haven't provided any OS/release details so this may not perfectly match what you're after.

Generally `openssh-client` ([https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=openssh-client&searchon=names](https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=openssh-client&searchon=names)) is pre-installed for all Ubuntu **desktop** releases.

The `openssh-server` (allowing incoming `ssh` connections) is not pre-installed on **desktops** ([https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=openssh-server&searchon=names](https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=openssh-server&searchon=names))

The root user I believe is created by default, but **disabled**.  You need only add a password to *enable* the root account (it's all I remember doing anyway).

 To know if you've enabled 'root' on a box, I'd look in the *passwd* or really *shadow* file, eg.

```
sudo grep root /etc/shadow
```

 and expect to see the encrypted password for 'root' when enabled.  It's visible on this box, yet on a fresh QA-test install the field is empty (or more accurately a "!" which is likely an invalid encrypted-key)

---

### Post by HermanAB on 2020-08-22
There are three commands called *who*, *users* and *groups*, which may also be useful to you.

---

### Post by The Cog on 2020-08-22
The root user always exists - it's fundamental to the operation of the system. There are always lots of processes running with root's id.

By default, root's *password* is disabled so nobody can log in directly as root. But you can run commands or processes as root by using sudo. "sudo -i" will give you a command prompt as root. You can see if root's password is set by using the command below. The second field of the output shoud be an exclamation mark.
```
sudo grep root /etc/shadow
```
You can lock root's password with the command 
```
sudo passwd -l root
```

---

### Post by coffeecat on 2020-08-22
Threads merged.

---

### Post by HermanAB on 2020-08-22
Some commands for you to explore:
$ whereis ssh
$ whereis sshd
$ ssh localhost
$ sudo apt update
$ sudo apt install openssh-server
$ sudo systemctl status ssh
$ sudo systemctl restart ssh
$ sudo ufw allow ssh

After you  have gone through that and googled a bit to see what it all means, you'll be OK with SSH.

---

