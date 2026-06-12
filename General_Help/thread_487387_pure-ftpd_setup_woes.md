---
title: "pure-ftpd setup woes"
date: 2007-06-29
forum: General Help
---

### Post by nbv4 on 2007-06-29
First I install pure-ftpd from the repos

then I add a new user to ubuntu (via the system - administration - users and groups menu) by the name of "ftp"

the server works fine when I run it via this command:
```

sudo pure-ftpd -S ,830 -p 19830:20000 -C 1 -K -w -B

```

I can log in with my username/pass, as well with the new FTP user/pass

Now I want to set up some virtual users. Specifically I want one account for getting the list, and nothing else. No uploading, no downloading

```

pure-pw useradd look -u ftp -d /home/ftp/uploads -m

```

everything seems fine and dandy, now I'll just start the server via this command:

```

sudo pure-ftpd -S ,830 -p 19830:20000 -C 1 -K -w -l puredb:/etc/pure-ftpd/pureftpd.pdb -lunix

```

logging in with my account works, logging in with the ftp account works, but the look account doesn't work. It gives me this error:

```

nbv4@nbv4:~$ ftp localhost 830
Connected to localhost.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 21:35. Server port: 830.
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (localhost:nbv4): look
331 User look OK. Password required
Password:
421 Service not available, remote server has closed connection
Login failed.
No control connection for command: Permission denied
ftp> quit

```

If I enter the wrong password, it gives me a 530 error. (proving my problem isn't caused by an incorrect password)

Anyone know what I'm doing wrong?

---

### Post by nbv4 on 2007-06-29
bump

---

### Post by alex_marshall on 2008-07-11
Hello,

I've found that pure-ftp sends a 421 error in instances where it's misconfigured, not just when there's something wrong with a firewall.  You may want to double check all your startup options and, as I've found on Google, your authentication methods.  I recently found that I was able to log into an instance of my own from external locations and from the box hosting the server itself, but not any locations on the same internal LAN.  Disabling DNS resolution for the server solved my problem.  Hope it helps.

---

