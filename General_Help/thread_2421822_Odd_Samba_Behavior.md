---
title: "Odd Samba Behavior"
date: 2019-06-27
forum: General Help
---

### Post by TPrime on 2019-06-27
Hello,

I am experimenting with setting up a file server. I began by setting up a "Common" share that anyone can access. This worked without issue. I then set up a user-specific share that will only be accessible by myself. I created the share, set permissions, enable the user in samba. When I tried to access the share it asked for a username and password, which I provided. Now it did not work, but that I can understand. The odd behavior is that now when I try to access the "Common" share I am also asked for a username and password, and it also fails. This problem now persists even after I reverted the smb.conf file to the previous configuration.

Why would creating a new share break a previously working share?

(I can't post my configs until I get home, unfortunately. But I will post any data that's requested when I am able.)

---

### Post by ccor58 on 2019-06-28
Have you thought of maybe using NFS file system shares for your user specific shares and just samba shares for all others? Or are you needing to access shares from a windows PC or laptop yourself as well?

---

### Post by HermanAB on 2019-06-29
IMHO, an Anonymous FTP server is the easiest to set up, NFS is 10 times more hassle and SMB is about 100 time more hassle than that.  

All of them provide rudimentary controls over which users can access what, but all of them are insecure and can be broken into quite easily with the right tools and all of them are supported by Linux, BSD, Apple and Windows.  With Windows, you have to install something from MS Technet to make NFS work, but it is free.

---

