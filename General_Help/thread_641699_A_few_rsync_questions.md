---
title: "A few rsync questions"
date: 2007-12-15
forum: General Help
---

### Post by broth420 on 2007-12-15
I have two servers in different physical locations.  I would like to be able to add data and have it copied automatically from one server to the other over the internet.  For these questions, lets assume the following
Server 1: 
192.168.0.10
username:  user
password:  password
directory to sync:  /home/user/data

Server 2:
192.168.0.11
username:  user
password:  password
dirctory to sync:  /home/user/data

I would like to use rsync over ssh to copy.
The ISP blocks ports below 1024, so the ssh port will need to be changed
I would like to run this as a service so when there is new data, it just automatically happens, either at a certain time, or real time.
Either server could have data added to it, and that data needs to be sync'ed to the other.

Is there anyone who can give me a hand and show me how I can do this.  I have found bits and pieces of info, but there seems to be several things going on.

Thanks in advance.

---

### Post by ectospasm on 2007-12-15
I suggest you read the rsync manual page.  It can connect via SSH, and even may do so by default.  Check this out:

[Linux Server Hack #38:  Using rsync over ssh]("http://www.oreilly.com/pub/h/38")

---

### Post by broth420 on 2007-12-16
It isn't so much the rsync stuff I need help with.  The biggest issue is changing the ssh port they are using, bi-directional sync, and sending to IP instead of name.
Just a simple command would be great.  I can figure out how to get the script to run in cron.  Anyone....?

---

### Post by broth420 on 2007-12-28
solved:
[http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

---

