---
title: "SSH brute force attack blocking?"
date: 2008-05-03
forum: General Help
---

### Post by StOoZ on 2008-05-03
there is someone/or more than one from several IP's who are trying to access my system via the SSH, very rapidly, is there anyway to block IP's for a  certain amount of time if they didnt managed to log-in lets say,for example, after 3 times??

---

### Post by DBrocks on 2008-05-03
First of all change your ports. That will stop automated-script kiddies from annoying you. Also, check out fail2ban, or DenyHosts. Also, you may want to enable you SSH for key-based login.

---

### Post by upthelum on 2008-05-03
> **DBrocks said:**
> First of all change your ports. That will stop automated-script kiddies from annoying you. Also, check out fail2ban, or DenyHosts. Also, you may want to enable you SSH for key-based login.

Please, how do i change port number allocation?

---

### Post by DBrocks on 2008-05-03
Changing your port is not a sure-fire way to protect yourself. However, it is a way to protect yourself from those annoying script-kiddies, who just scan on port 22 (Default SSH port). So, to change your port, edit /etc/ssh/sshd_config and look for the line that says "port 22". change from port 22 to say, port 1024, or something you won't forget. Restart ssh.
```

/etc/init.d/ssh restart
```

---

### Post by Monicker on 2008-05-03
> **upthelum said:**
> Please, how do i change port number allocation?

From a command line

```
sudo nano /etc/ssh/sshd_config
```


Change the line which reads
```

Port 22
```


Restart the ssh daemon

```
sudo /etc/init.d/ssh restart
```


*Ack. Too late for me.  :P*

---

### Post by rogblake on 2008-05-03
> **StOoZ said:**
> there is someone/or more than one from several IP's who are trying to access my system via the SSH, very rapidly, is there anyway to block IP's for a  certain amount of time if they didnt managed to log-in lets say,for example, after 3 times??

This can be done easily with an iptables firewall. See:

  [http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

---

### Post by upthelum on 2008-05-03
Monicker and DBrocks thanks

---

### Post by DBrocks on 2008-05-04
However, that is security through obscurity. You may want to enable keys. What are keys? Keys are little packets of information that only you have. The server also has it's own unique key. When you SSH into the desired host, the host verifies your key against it's own. It it passes, it lets you in. If it fails, you are blocked. This is a great tutorial here:
[URL="http://howtoforge.com/ssh_key_based_logins_putty"]
http://howtoforge.com/ssh_key_based_logins_putty[/URL]

---

