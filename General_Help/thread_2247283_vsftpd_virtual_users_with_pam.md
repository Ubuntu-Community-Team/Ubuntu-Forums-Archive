---
title: "vsftpd virtual users with pam"
date: 2014-10-07
forum: General Help
---

### Post by Xanthius on 2014-10-07
I've been struggeling with this for hours, searching the internet reading guides but non of them seems to be offering the setup i want.
I'm looking for a simple setup of configuring my ftp server with users and a few unique users with special home folders and I'm lost with this.

I want to have the following users with the directory's setup:
root **/**
xanthius **/home/xanthius**
apache **/var/www/**
apachewebuser **/var/www/somewebsite**
guest **/var/ftp/guest**

virtual users:
user1 **/var/ftp/users/user1**
user2 **/var/ftp/users/user2**

I've changed my configuration so many times got things to work, but not all of it and now it broke down completely.
Can someone help me with this?

---

### Post by bashiergui on 2014-10-09
Please list the detailed errors you are receiving.

---

