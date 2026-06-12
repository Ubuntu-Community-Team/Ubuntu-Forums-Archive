---
title: "command line"
date: 2013-01-17
forum: General Help
---

### Post by Leo Matheus on 2013-01-17
I want to send a file using the ftp protocol to a server.
The think is, i want to send a file that was the last write on the directory. Is there any linux command that can do some think similar to this? 
im using ubuntu 12.04 LTS

---

### Post by papibe on 2013-01-17
Hi Leo Matheus.

There's no command that does that exactly, but if you don't mind doing a little scripting there are always solutions.

For instance, this comes to mind:
```
ls -t1 | head -n 1
```
where
[LIST]
[*]ls list the files on the directory
[*]-1 option presente them on one column.
[*]-t sort them newer first.
[*]head filter from the beggining of the list.
[*]-n1 gets you the very first (the newer).
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Leo Matheus on 2013-01-17
i think this is what i need.
i will make the script and them, if it works, i will post it here.:p

---

### Post by Lars Noodén on 2013-01-17
You won't need much of a script.  The package ncftp contains the tool ncftpput which will make it easier to upload with FTP.  The regular FTP client could be used too, it has a batch mode.

---

### Post by Leo Matheus on 2013-02-20
well, i just dicovery that the on the network im using is there a firewall an proxy that are blocking the ftp protocol, so i have to use another way :(. thanks any way guys.

---

### Post by Lars Noodén on 2013-02-20
Try using sftp instead then.  It is secure, unlike ftp.  And it has batch mode capabilities, too.

---

### Post by Leo Matheus on 2013-02-20
well, i think the only protocol that im able to use is http, the rest is blocked

---

### Post by Lars Noodén on 2013-02-20
Better test to see if it is really blocked.  If it is, it won't hurt to ask them to open up SFTP.  There are no security reasons to deny it and the worst (usually) they can do is say no.

---

### Post by Leo Matheus on 2013-02-20
i had think that, but thre is some politics involved on that, so im trying to use another way.

---

