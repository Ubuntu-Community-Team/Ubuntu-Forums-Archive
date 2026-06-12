---
title: "Files initially sending wrong username to server"
date: 2023-08-26
forum: General Help
---

### Post by whairst on 2023-08-26
On my Ubuntu 22.04 machine, I use Files to connect to a ssh fileshare. During the first connection, I told Files to remember the username and password for this fileshare. In examining the logs on that server, I'm finding that each time Ubuntu connects to it, it tries to authenticate using the LOCAL username first, fails, then successfully connects using the stored username for that server. In Ubuntu Files, I can't see any of this; it simply takes a moment to connect.

Has anyone else seen this behavior?

Munged log exerpt is below. I replaced the usernames; localuser is the username I'm logged into on the Ubuntu machine, while serveruser is the username for the remote server that is saved in Files (Seahorse?).

Aug 26 08:59:25 server sshd[14968]: Invalid user localuser from 192.168.2.120 port 44372
Aug 26 08:59:25 server sshd[14968]: input_userauth_request: invalid user localuser [preauth]
Aug 26 08:59:25 server sshd[14968]: Postponed keyboard-interactive for invalid user localuser from 192.168.2.120 port 44372 ssh2 [preauth]
Aug 26 08:59:25 server sshd[14972]: Accepted keyboard-interactive/pam for serveruser from 192.168.2.120 port 44380 ssh2
Aug 26 08:59:26 server sshd[14972]: pam_unix(sshd:session): session opened for user serveruser by (uid=0)

---

### Post by TheFu on 2023-08-26
If you are going to save the password, why not setup ssh-keys from your local user to the remote user@system and never be bothered with this again?
2 commands:> 
Step 1:  Run on the client as the normal user:
```
   $ ssh-keygen -t ed25519
```

Step 2:  Run from the client to the server:
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub serveruser@remote
```

Step 3: Setup ~/.ssh/config  on the client. An example:
```
host remote
  user serveruser
  hostname 192.168.2.155
  port 22
```

whenever you run "ssh remote", it will convert that to **ssh -p 22 serveruser@192.168.2.155** ... and the same for sftp, scp, rsync, and 50 other ssh-based connections.  The hostname can be an IP address or the DNS or mDNS name. Your choice.
If you do step 3 first, then step 2 would be **ssh-copy-id -i ~/.ssh/id_ed25519.pub remote**

BTW, not that it matters, but ssh doesn't do file transfers.  That will be sftp, so gnome-files isn't really using ssh, it is using sftp://.  Gnome is dumbing down things again and being inaccurate doing it. They aren't the first and this isn't the only place where Gnome does it ... incorrectly.  And people wonder why computers are difficult?  It is because incorrect terms are used inconsistently.  Who can keep up with all these mistakes?  That's always been the situation with computing.

---

### Post by whairst on 2023-08-30
Simple answer - because I can save the password by clicking one simple checkbox, instead of a 3-step procedure. And this doesn't address the question - why is Ubuntu sending the LOCAL username first, getting rejected, then sending the REMOTE username? As for ssh vs sftp, I'm not particularly concerned about what the systems call it, and the server (a CentOS machine) uses logwatch to list the logins under sshd.

---

### Post by TheFu on 2023-08-30
> **whairst said:**
> Simple answer - because I can save the password by clicking one simple checkbox, instead of a 3-step procedure. And this doesn't address the question - why is Ubuntu sending the LOCAL username first, getting rejected, then sending the REMOTE username? As for ssh vs sftp, I'm not particularly concerned about what the systems call it, and the server (a CentOS machine) uses logwatch to list the logins under sshd.

It is Gnome-files, not Ubuntu.  Open a bug with them - the gnome project.  Gnome does lots of less than smart things.

OTOH, if you use ssh-keys, it will be more secure, more seamless AND more convenient.  I know of no other subsystem where that applies.  Plus, it isn't just for ssh, but any ssh-based connection between the two systems.

---

### Post by whairst on 2023-09-02
Thanks for letting me know it's Gnome-files. No, I'm not interested in using ssh-keys; telling Files to remember the login information is more seamless and more convenient (being one checkbox) rather than setting up keys on the client and server.

---

### Post by TheFu on 2023-09-02
[https://security.stackexchange.com/questions/69407/why-is-using-an-ssh-key-more-secure-than-using-passwords](https://security.stackexchange.com/questions/69407/why-is-using-an-ssh-key-more-secure-than-using-passwords)
I'll leave you alone now.

---

