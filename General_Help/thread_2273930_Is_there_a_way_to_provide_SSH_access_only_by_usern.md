---
title: "Is there a way to provide SSH access only by username?"
date: 2015-04-16
forum: General Help
---

### Post by shaferwr on 2015-04-16
Hello!

Scenario:

I want to use my Ubuntu VM to house my Cisco configurations using the archive feature of Cisco IOS.  To do this and meet security requirements I have to use SCP.  To use SCP from the archive feature I have to put the commands in the configuration of the router like so:

```
archive
 log config
  logging enable
  logging size 500
  notify syslog contenttype plaintext
  hidekeys
 path scp://cisco:cisco@XXX.XXX.XXX.XXX/$h_
 write-memory
 time-period 1440
```

Basically, what this does is backs up the configuration every time an administrator writes the configuration of the IOS (write mem), or if nothing has changed, copies the configuration of the Cisco device to the server every 24 hours.

What I have done already:

I created a user account on my Ubuntu box with the username "cisco" and the password "cisco".  
Executed a "write mem" on my router and confirmed the connection over ssh.

The problem is that the configuration shows the username and password of a valid user on my Ubuntu server, that has full rights of every other user.  I'd like to limit this user's rights to ONLY ssh (port 22) and no other shell access.

How do I do that?  I'd like to be able to use all commands from the terminal and not the GUI if possible.

Thanks for any and all help you can provide.

-Will Shafer
Cisco Certified Network Professional (CCNP)
Fledgling Ubuntu Rookie

---

### Post by shaferwr on 2015-04-20
Any ideas? Please?

---

### Post by conner_bradley on 2015-04-20
What you're saying is the user "Cisco" is root, it has full control over other users (Possibly the entire system?)

Would you want the user to have sudo access? This may have an effect on the answer

However, you would want to edit your SSH config file
[B]
sudo nano /etc/ssh/sshd_config[/B]

and append the following to it:

PermitRootLogin no
AllowUsers cisco

If you want to get fancy, you can specify the cisco's user IP address 

AllowUsers cisco@192.168.2.1 

If you need more users, say cisco1 cisco2 and cisco3

AllowUsers user1 cisco1@localhost user2 cisco2@localhost

etc etc

Hope this helps,

-C Bradley

---

### Post by shaferwr on 2015-04-20
Thanks for the reply!  I'm kinda desperate here. =(

What I need is the exact opposite of what you said above.  I need a single user account with ONLY ssh privileges.  No RDP, No anything else.  I only want the cisco account to access the cisco home directory and nothing else.

I basically have hundreds of routers/switches all over my network that I need to back up the configurations to over a secure connection, ie: SCP.  SCP is done over an ssh session (port 22).  Because the user id and password MUST be in the running configuration, I don't want anyone else to be able to log in and go anywhere on my Ubuntu server other than the "cisco" folder that houses the backed up configurations.

I hope this is a better explanation.  Thanks again for replying, Conner.

-Will

---

### Post by efflandt on 2015-04-21
Web search "limit ssh to scp". Normal Ubuntu repos do not seem to have **scponly**, but do have **rssh**, which you could set as the login shell for user cisco on the destination. Then you could use keys with no passphrase for authentication.

> rssh is a restricted shell, used as a login shell, that allows users to
perform only scp, sftp, cvs, svnserve (Subversion), rdist, and/or rsync
operations.  It can also optionally chroot user logins into a restricted
jail.

---

### Post by matt_symes on 2015-04-21
Hi

+1 to rssh.

```
sudo apt-get install rssh
```

allowscp only in the rsh config file and chroot the user for added security. Set the mask so that uploaded files are not executable. This can all be achieved from /etc/rssh.conf.

Read the man pages carefully

```

man rssh
man 5 rssh.conf
```

If this VM is only for Cisco configuration saves then really lockdown ports and IP addresses using iptables to ssh and required services such as ntp only. Otherwise lock down as much as possible.

Don't use the user name Cisco and, if you must use passwords, then set up a *long* password with plenty of entropy.

Kind regards

---

