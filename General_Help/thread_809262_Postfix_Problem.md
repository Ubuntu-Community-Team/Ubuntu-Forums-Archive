---
title: "Postfix Problem"
date: 2008-05-27
forum: General Help
---

### Post by Black Mage on 2008-05-27
Hey guys,

I am having a problem with postfix. I cannot login as a user even though I did a sudo useradd -m -s /bin/bash jjohnson. The rror looks like this:

```

root@mainserver:/etc/postfix/ssl# telnet 192.168.1.201 110
Trying 192.168.1.201...
Connected to 192.168.1.201.
Escape character is '^]'.
+OK Hello there.
user jjohnson
+OK Password required.
pass testpassword
-ERR Login failed.


```

Any ideas why I can't login?

Thanks

---

### Post by Monicker on 2008-05-27
Check your postfix logs.

/var/log/mail.log
/var/log/mail.info

---

### Post by Black Mage on 2008-05-27
Here is my mail.log

```

May 27 09:04:39 mainserver imapd: Connection, ip=[::ffff:75.160.207.30]
May 27 09:05:09 mainserver imapd: LOGIN FAILED, user=jjohnson, ip=[::ffff:75.160.207.30]
May 27 09:10:38 mainserver courierpop3login: Connection, ip=[::ffff:75.160.207.30]
May 27 09:11:00 mainserver courierpop3login: LOGIN FAILED, user=jjohnson, ip=[::ffff:75.160.207.30]
May 27 09:12:18 mainserver courierpop3login: LOGOUT, ip=[::ffff:75.160.207.30]
May 27 09:12:18 mainserver courierpop3login: Disconnected, ip=[::ffff:75.160.207.30]

```

---

### Post by Monicker on 2008-05-27
I would imagine you set the password for that account after creating it, correct?  Did you verify the password is correct?

What happens if you do
```

su jjohnson
```

Is the password for that account accepted?

---

### Post by Black Mage on 2008-05-27
Yes, I can login no problem. The password works from the command line.

---

### Post by Monicker on 2008-05-27
Sounds like you need to take a look at courier.   Postfix itself does not do imap or pop3, so it would be something with the applications handling those specific functions.

---

### Post by Black Mage on 2008-05-27
Where are the courier log files located? They are not in my /var/log.

---

### Post by Monicker on 2008-05-27
I do not know.  I have never used Courier.

This might help: [https://help.ubuntu.com/community/Courier]("https://help.ubuntu.com/community/Courier")

Check your configuration files to see if they show where the log files are written.

---

### Post by Black Mage on 2008-05-27
Ok, thanks.

---

### Post by Black Mage on 2008-05-27
Could the problem be access permissions? That courier cannot access the folder?

Because I followed the tutorial

```

chown -R myuser:usergroup /home/myuser/Maildir
chmod -R 700 /home/myuser/Maildir

```

And when I tried to do an su to jjohnson and then a cd /Maildir, i got a permissons denied. And in the chown -R myuser:usergroup, I did not add a group, only a user. 

I also did a telnet localhost 25 and sent a message. I then when so the root user and checked and the message is there. So could it be a permissions problem why courier can't login?

---

