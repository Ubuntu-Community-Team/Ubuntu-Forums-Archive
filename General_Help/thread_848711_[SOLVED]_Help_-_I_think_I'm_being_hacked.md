---
title: "[SOLVED] Help - I think I'm being hacked"
date: 2008-07-03
forum: General Help
---

### Post by dash86no on 2008-07-03
Guys, 

I was trying to debug some issues with a Shoreline firewall running on Ubuntu Server 8.04. I was digging around the log files and found the following alarming alerts in auth.log

Jul  4 07:31:25 DC-FS-UBUNTU001 sshd[7433]: Failed password for invalid user slap from 118.98.212.214 port 4089 ssh2
Jul  4 07:31:26 DC-FS-UBUNTU001 sshd[7436]: Invalid user shell from 118.98.212.214
Jul  4 07:31:26 DC-FS-UBUNTU001 sshd[7436]: pam_unix(sshd:auth): check pass; user unknown
Jul  4 07:31:26 DC-FS-UBUNTU001 sshd[7436]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.98.212.214 
Jul  4 07:31:29 DC-FS-UBUNTU001 sshd[7436]: Failed password for invalid user shell from 118.98.212.214 port 4184 ssh2
Jul  4 07:31:31 DC-FS-UBUNTU001 sshd[7438]: Invalid user ls from 118.98.212.214
Jul  4 07:31:31 DC-FS-UBUNTU001 sshd[7438]: pam_unix(sshd:auth): check pass; user unknown
Jul  4 07:31:31 DC-FS-UBUNTU001 sshd[7438]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.98.212.214 
Jul  4 07:31:33 DC-FS-UBUNTU001 sshd[7438]: Failed password for invalid user ls from 118.98.212.214 port 4266 ssh2
dash@DC-FS-UBUNTU001:/var/log$ cat auth.log | tail
Jul  4 07:31:26 DC-FS-UBUNTU001 sshd[7436]: Invalid user shell from 118.98.212.214
Jul  4 07:31:26 DC-FS-UBUNTU001 sshd[7436]: pam_unix(sshd:auth): check pass; user unknown
Jul  4 07:31:26 DC-FS-UBUNTU001 sshd[7436]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.98.212.214 
Jul  4 07:31:29 DC-FS-UBUNTU001 sshd[7436]: Failed password for invalid user shell from 118.98.212.214 port 4184 ssh2
Jul  4 07:31:31 DC-FS-UBUNTU001 sshd[7438]: Invalid user ls from 118.98.212.214
Jul  4 07:31:31 DC-FS-UBUNTU001 sshd[7438]: pam_unix(sshd:auth): check pass; user unknown
Jul  4 07:31:31 DC-FS-UBUNTU001 sshd[7438]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.98.212.214 
Jul  4 07:31:33 DC-FS-UBUNTU001 sshd[7438]: Failed password for invalid user ls from 118.98.212.214 port 4266 ssh2
Jul  4 07:39:01 DC-FS-UBUNTU001 CRON[7447]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  4 07:39:01 DC-FS-UBUNTU001 CRON[7447]: pam_unix(cron:session): session closed for user root
dash@DC-FS-UBUNTU001:/var/log$ cat auth.log | tail
Jul  4 07:31:26 DC-FS-UBUNTU001 sshd[7436]: Invalid user shell from 118.98.212.214
Jul  4 07:31:26 DC-FS-UBUNTU001 sshd[7436]: pam_unix(sshd:auth): check pass; user unknown
Jul  4 07:31:26 DC-FS-UBUNTU001 sshd[7436]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.98.212.214 
Jul  4 07:31:29 DC-FS-UBUNTU001 sshd[7436]: Failed password for invalid user shell from 118.98.212.214 port 4184 ssh2
Jul  4 07:31:31 DC-FS-UBUNTU001 sshd[7438]: Invalid user ls from 118.98.212.214
Jul  4 07:31:31 DC-FS-UBUNTU001 sshd[7438]: pam_unix(sshd:auth): check pass; user unknown
Jul  4 07:31:31 DC-FS-UBUNTU001 sshd[7438]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.98.212.


this seems to have been happening for over an hour: | head output:

Jul  4 06:45:22 DC-FS-UBUNTU001 CRON[28689]: pam_unix(cron:session): session closed for user root
Jul  4 06:45:23 DC-FS-UBUNTU001 sshd[32328]: Invalid user dowjones from 118.98.212.214
Jul  4 06:45:23 DC-FS-UBUNTU001 sshd[32328]: pam_unix(sshd:auth): check pass; user unknown
Jul  4 06:45:23 DC-FS-UBUNTU001 sshd[32328]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.98.212.214 
Jul  4 06:45:23 DC-FS-UBUNTU001 sshd[32213]: Failed password for invalid user oliver from 118.98.212.214 port 1143 ssh2
Jul  4 06:45:23 DC-FS-UBUNTU001 sshd[32215]: Failed password for invalid user mlagos from 118.98.212.214 port 1144 ssh2
Jul  4 06:45:24 DC-FS-UBUNTU001 sshd[32224]: Failed password for invalid user warner from 118.98.212.214 port 1156 ssh2
Jul  4 06:45:25 DC-FS-UBUNTU001 sshd[32334]: Invalid user mmelo from 118.98.212.214
Jul  4 06:45:25 DC-FS-UBUNTU001 sshd[32336]: Invalid user werner from 118.98.212.214
Jul  4 06:45:25 DC-FS-UBUNTU001 sshd[32335]: Invalid user olivia from 118.98.212.214


What is the appropriate response to this? Do I need to report this to somebody?

Your help is much appreciated.

---

### Post by NetworkGuy on 2008-07-03
Just have your firewall block everything coming from that subnet  118.98.212.0/255.255.255.0

---

### Post by shae on 2008-07-03
There really isn't anyone to report such action to, but it seems like someone is trying to brute force your ssh.  Follow the steps outlined here to protect you from such an attempt in the future.

[http://nixcraft.com/networking-firewalls-security/726-failed-ssh-login-attempts-how-avoid-brute-ssh-attacks.html](http://nixcraft.com/networking-firewalls-security/726-failed-ssh-login-attempts-how-avoid-brute-ssh-attacks.html)

---

### Post by dash86no on 2008-07-03
the attack seems to have begun yesterday afternoon:

Jul  3 17:28:13 DC-FS-UBUNTU001 sshd[26037]: Failed password for invalid user test from 218.22.9.118 port 41661 ssh2
Jul  3 17:28:15 DC-FS-UBUNTU001 sshd[26039]: Invalid user guest from 218.22.9.118
Jul  3 17:28:15 DC-FS-UBUNTU001 sshd[26039]: pam_unix(sshd:auth): check pass; user unknown
Jul  3 17:28:15 DC-FS-UBUNTU001 sshd[26039]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.22.9.1

Also, it seems to have stopped now. Just a coincidence? I did a who is on the IP and also put it into my web browser to bring up a website. Did this alert the attacker I was on to them?

Also, the above IP address is different so I'm guessing this guy is maybe directing attacks through proxies?

It seems from the mistaken guesses that this guy is just having a go; I don't think this is someone who knows me personally. 

Anyone else experienced this?

---

### Post by dash86no on 2008-07-03
> **shae said:**
> There really isn't anyone to report such action to, but it seems like someone is trying to brute force your ssh.  Follow the steps outlined here to protect you from such an attempt in the future.

[http://nixcraft.com/networking-firewalls-security/726-failed-ssh-login-attempts-how-avoid-brute-ssh-attacks.html](http://nixcraft.com/networking-firewalls-security/726-failed-ssh-login-attempts-how-avoid-brute-ssh-attacks.html)

Thanks for that Shae, will implement ASAP

---

### Post by brian_p on 2008-07-03
> **dash86no said:**
> 
Also, it seems to have stopped now. Just a coincidence? I did a who is on the IP and also put it into my web browser to bring up a website. Did this alert the attacker I was on to them?

Also, the above IP address is different so I'm guessing this guy is maybe directing attacks through proxies?

It seems from the mistaken guesses that this guy is just having a go; I don't think this is someone who knows me personally. 

Anyone else experienced this?

This happens all the time. There is no 'guy' directing an attack at you personally, just an automated script looking for easy pickings. But you have a strong password or are using ssh keys so there is nothing to worry about. Note that none of the usernames tried exist on your system.

If it annoys you the denyhosts package is to recommended as an easy way reduce the noise in your logs.

---

### Post by p_quarles on 2008-07-03
You can also set your SSH service to listen on a non-default port. That will cause these attempts to be silently dropped. These kinds of automated brute forcing scripts will never -- under normal circumstances -- be able to detect a service running on an alternate port.

---

### Post by AnarkistNZ on 2008-07-03
> **shae said:**
> There really isn't anyone to report such action to

Incorrect.

If you WHOIS the IP address, you're able to report such abuse to the [email]abuse@isp.com[/email] email address reported in the WHOIS details.

If the ISP is a decent one and pro-actively monitors their abuse queue (which is a bit of a hopeful assumption admittedly) then the user should have be  warned and/or have their services removed.

---

### Post by dash86no on 2008-07-07
Cheers for all your help the other day chaps.

I followed Shae's weblink and there was some great advice on there for securing SSH.

Also, I got a tip from digging around on google so I thought I'd share it here with everyone. (if you are running shorewall) Add the following to your Shorewall firewall rules table:

ACCEPT	net	$FW	tcp	xxx - - 1/min:2

where xxx is the port you will accept the connection on.

This will restrict failed logins to one per minute (2 in the first 60 seconds). Which should reduce the strain failed logins put on your system as well as keeping things pretty well locked down. 

Also, digging around on google I noticed this is not a rare occurrence. People are scanning IP addresses by the millions using automated tools and you need to be very careful to secure SSH. I was luckly to have noticed and taken action in time. 

Cheers,

---

### Post by hyper_ch on 2008-07-07
```

sudo apt-get install denyhosts

```

after too many unsuccessfull authorization tries within a too small timeframe the IPs will get automatically blocked.

---

