---
title: "ssh dies after a few minutes, and locks out server"
date: 2020-03-20
forum: General Help
---

### Post by jdmccue927 on 2020-03-20
I have been fighting this for three days. I've been all over the internet for answers and nothing has worked. 

After installing ubuntu server (18.04, 18.04.3, and 18.04.4) ssh sessions either halt after a few minutes or the connection times out. Once the timeout happens it's nightmare to get working again. Multiple reboots, deleting **known_hosts** etc. 

I've modified the **ssh_config** and **sshd_config** for KeepAlive settings according to a Stack Overflow article. 

I've opened port 22 on ufw, enabled it and disabled it, etc. etc. nmap shows the port open and happy. Still cannot connect, or connection halts and will not resume, and then cannot connect. 

```

01:~$ nmap -p 22 192.168.1.119

Starting Nmap 7.60 ( https://nmap.org ) at 2020-03-20 16:46 EDT
Nmap scan report for 192.168.1.119
Host is up (0.00034s latency).

PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds
```

next attempt after above.

```

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds
-01:~$ ssh goober@192.168.1.119
ssh: connect to host 192.168.1.119 port 22: Connection timed out
```

Anyone with any ideas is appreciated. 

Thank you 
John

---

### Post by HermanAB on 2020-03-20
From my past ssh experience, you could have a bad ethernet device somewhere:
a. Check your ethernet switches and cables.  
b. Check the ifconfig error count on the ethernet ports.
c. Check the system logs for duplicate MAC and IP address warnings.

---

