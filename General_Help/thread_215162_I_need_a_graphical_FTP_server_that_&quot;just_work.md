---
title: "I need a graphical FTP server that &quot;just works&quot;"
date: 2006-07-13
forum: General Help
---

### Post by Boomy on 2006-07-13
I have wasted my entire morning messing around with proftpd and pureftpd and they don't work. I can see myself logging into pureftp, but it won't pop up a password box in the web browser and I get authentication failed when I try to connect to the server. I need to transfer some files to a buddy and I need an FTP server that works. I don't want to spend hours in a terminal messing around, I just want to host the files for him to download. Is there anything like Bullet Proof FTP for Linux? Maybe I can just install that with wine. :evil:

---

### Post by Valehru on 2006-07-13
Try installing gproftpd.  That did it for me...

sudo apt-get install gproftpd

---

### Post by Boomy on 2006-07-13
I tried that, didn't work at all.

---

### Post by cleentrax on 2006-07-13
I've been using gftp. It has a lot of nice features, and it's easy to use, though it occasionally crashes for no obvious reason.

---

### Post by Boomy on 2006-07-13
It looks like gftp is just a client not a server. Well I installed Bullet Proof FTP server under wine and within 3 minutes I had my files online and accessible. I thought for sure there would be tons of good FTP servers to choose from for Linux but the 2 that are avaialable are garbage.

---

### Post by Poka64 on 2006-07-13
> **Boomy said:**
> It looks like gftp is just a client not a server.

well, gftp is a client, gproftpd is a gui frontend for proftpd.

Edit: sorry, You already know this..

---

### Post by nix4me on 2006-07-13
Proftpd is far superior to any graphical server your use to in Windows.  Servers are servers, not pretty applications that look good.

Proftpd is very easy to set up a simple standalone server.  I'm not sure why you had such a problem.  There is also an excellent howto on the forums.

Anyway, glad you were able to get up and running quickly anyway.

nix4me

---

### Post by taurus on 2006-07-13
Another option is vsftpd!!!

---

### Post by CymPhreak on 2006-07-13
Why not use sshd instead? It was pretty simple to install and set up and it is supported by clients such as gFTP and KBear in Linux and WinSCP in the Windows world. Just a thought.... ;)

---

