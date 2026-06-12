---
title: "FTP Connection very slow"
date: 2007-05-04
forum: General Help
---

### Post by Jordanwb on 2007-05-04
I was able to install SSH and Proftpd successfully and everything was configured. The very first time I was able to ftp successfully it was very fast (within a network) but now it takes about a 1 minute to list the directories contents and to a single file. :confused:

I found out that IPv6 is currently on which of course I don't want which is probably why it's so slow.

Edit #2:

Nope it's not IPv6

---

### Post by RichGuk on 2007-05-05
How are you running the FTP server? Inetd or standalone?

Just from experience I found inetd to be slow at brining up directory lists. Maybe try standalone?

```
sudo dpkg-reconfigure proftpd
```

---

### Post by Jordanwb on 2007-05-05
It's currently set to standalone. I think. I'll check. I reset it to standalone and it's still really slow at connecting and loading the lists.

---

### Post by ariejan on 2007-06-01
Your problem probably is ProFTPd lookup your hostname when you connect. (which fails, and that's why you have to wait for that to time out).

[http://ariejan.net/2007/05/29/slow-connections-with-proftpd/](http://ariejan.net/2007/05/29/slow-connections-with-proftpd/)

Read more in this article on how to solve the issue easily. (just add a line to your config and restart). 

Cheers!

---

### Post by Jordanwb on 2007-06-21
Tried that and FTP is still incredibly slow.

---

### Post by ktrnka on 2007-07-24
I had the same problem and what worked was to change UseReverseDNS to off.

---

