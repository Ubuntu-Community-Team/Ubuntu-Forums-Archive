---
title: "vsftpd question"
date: 2008-03-08
forum: General Help
---

### Post by 200mg on 2008-03-08
Hello, I am using Ubuntu Gutsy and I installed vsftpd using apt-get. I have configured the /etc/vsftpd.conf file. I left the "listen_port" option alone so it should be default 21. I don't think vsftpd is running though, I start, stop, restart using /etc/init.d/vsftpd start/stop/etc...however after i start it it's not opening port 21 to accept connections. I was wondering if the "No /usr/sbin/vsftpd found running; none killed." is part of the problem, after a restart it says "ok" like it should be running.

```
 * Stopping FTP server: vsftpd                                                  
No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
 * Starting FTP server: vsftpd                                           [ OK ] 

```

So to me the above looks like it should be running, however when i do an nmap to local it doesn't show 21 as being open. Any ideas? TIA

---

### Post by taurus on 2008-03-08
Can you ftp to your machine from another one?

---

### Post by 200mg on 2008-03-08
no, that's what prompted me to investigate this more, and what i have come up with is that vsftpd is running, but it's not opening port 21...

---

### Post by 200mg on 2008-03-08
I figured this out, I was runnning standalone mode and not inet...thanks for the replies

---

