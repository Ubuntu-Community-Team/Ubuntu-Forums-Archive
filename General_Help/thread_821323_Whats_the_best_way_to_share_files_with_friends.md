---
title: "Whats the best way to share files with friends?"
date: 2008-06-07
forum: General Help
---

### Post by Tomatz on 2008-06-07
Whats the best way to share files with friends over the internet without using p2p?

---

### Post by lisati on 2008-06-07
> **Tomatz said:**
> Whats the best way to share files with friends over the internet without using p2p?

Email? Some kind of VPN (Virtual Private Network)?

---

### Post by Tomatz on 2008-06-07
> **lisati said:**
> Email? Some kind of VPN (Virtual Private Network)?

Email is annoying. Thought of a vpn but there must be a simpler way also i dont want to share files all the time, just when i need to :)

---

### Post by Tomatz on 2008-06-07
[edit]

---

### Post by Tomatz on 2008-06-07
Bump

---

### Post by rampageoberon on 2008-06-07
Probably create an ftp server or webserver to let people access your files. I would much prefer a P2P application as that is what you want to do.

---

### Post by Monicker on 2008-06-07
> **Tomatz said:**
> Bump

You could set up an ftp server on your side.  Then they could use any of several ftp clients to connect and get files from you.  If you go that route I would suggest using SSL/TLS so that the data is not in the clear. Gproftpd could be used for a gui frontend to configuring an ftp server.

You could also install openssh server, which will give you encryption by default, and then they could use an sftp client to get files.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSHHowto#head-1aa0ea24fdf28c7516f58131897fa15691d8e58d](https://help.ubuntu.com/community/SSHHowto#head-1aa0ea24fdf28c7516f58131897fa15691d8e58d)

---

### Post by jras20 on 2008-06-07
Me and a friend use yousendit, it sends 100mb a day free.

[www.yousendit.com](www.yousendit.com)

---

### Post by Tomatz on 2008-06-07
> **Monicker said:**
> You could set up an ftp server on your side.  Then they could use any of several ftp clients to connect and get files from you.  If you go that route I would suggest using SSL/TLS so that the data is not in the clear. Gproftpd could be used for a gui frontend to configuring an ftp server.

You could also install openssh server, which will give you encryption by default, and then they could use an sftp client to get files.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSHHowto#head-1aa0ea24fdf28c7516f58131897fa15691d8e58d](https://help.ubuntu.com/community/SSHHowto#head-1aa0ea24fdf28c7516f58131897fa15691d8e58d)

Thanks for the tips :)

This sounds exactly like what i want to do.

---

### Post by dagnabit dang doohickey on 2008-06-07
[box.net]("http://box.net/")
[Orbitfiles]("http://www.orbitfiles.com/")

---

### Post by d.kusummmanth@gmail.com on 2008-06-07
> **Tomatz said:**
> Whats the best way to share files with friends over the internet without using p2p?
AS LONG AS UR FILES R NOT COPYRIGHTED, u'll have no problem with creating ur own ftp server. Else, u can use a file hosting site.

---

