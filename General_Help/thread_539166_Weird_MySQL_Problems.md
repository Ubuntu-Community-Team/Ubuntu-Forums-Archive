---
title: "Weird MySQL Problems"
date: 2007-08-30
forum: General Help
---

### Post by waveslider on 2007-08-30
Hello everyone,

I'm having some weird problems using MySQL server 5.0. I've never had trouble with MySQL in the past on Edgy or Dapper.

I have purged & reinstalled MySQL twice now. The first time, I was unable to login at all. I found out that the problem had to do with a change in the way MySQL stores passwords now in the latest version.

However, after purging and reinstalling MySQL, I was still unable to login to the root account. I had to login to the debian-sys-maint account and change the password for root, and create an account for my username (I use MySQL Administrator for all of this).

The problem now is, even after changing the root password several times, ensuring that I made no typos, in MySQL Administrator with the debian-sys-maint account, I still cannot login to the root account, although I am able to log into my personal mysql account. The mysql server keeps telling me the root account is not authorized to login. It says "Access denied for 'root'@'localhost' (using password YES).

Any ideas what's going on & how to fix?

Thanks!

---

### Post by waveslider on 2007-08-31
Anyone have any idea how to fix this?

---

### Post by gkestrel on 2007-11-04
Try this in a terminal
 sudo dpkg-reconfigure mysql-server-5.0 and set the root password from there, this worked for me when i had the same problem.

---

