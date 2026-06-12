---
title: "An application for viewing open ports?"
date: 2008-06-22
forum: General Help
---

### Post by george9233 on 2008-06-22
Hello.

I would like to know if there is an application, either has CLI or GUI, in the repository that allows me to view all connected ports? so I can get a better idea of what applications are currently connected to the Internet.

Thanks.

---

### Post by p_quarles on 2008-06-22
Yes. I use:
```
netstat -tunva
```
which gives you a rundown on current, listening, recent and persistent connections, both to the loopback device and the "real" network. Read the man page for further options.

Etherape (in the repos) is a graphical application that can show you the same information.

Another command line tool -- nmap -- can also be useful for determining which ports open, regardless of whether they are connecting with anything.

---

### Post by george9233 on 2008-06-22
Thanks. I'll try all these and see which one I like.

---

### Post by cariboo on 2008-06-22
This one doesn't tell you whats connected to the internt but it does tell you what ports are open. Nmap and the gui is nmapfe

Jim

---

### Post by george9233 on 2008-06-22
> **cariboo907 said:**
> This one doesn't tell you whats connected to the internt but it does tell you what ports are open. Nmap and the gui is nmapfe

Jim

Thanks, but I can't find "nmapfe" in the repository.

---

### Post by george9233 on 2008-06-22
To make things clearer, I attached a screenshot of the "TCPView" program.

This is a little program for Windows to view all connected ports including the following information:

[LIST]
[*]names of the process
[*]protocol type
[*]local address
[*]remote address
[*]state
[*]red for download, green for upload
[/LIST]
I would like to see something like this, plus the command line of the program.

---

### Post by mihaiv on 2008-10-03
[Netactview]("http://netactview.sourceforge.net") is a graphical network connections viewer similar with TcpView.

---

### Post by george9233 on 2008-10-03
Thank you so much. This is the one I've been looking for.

---

