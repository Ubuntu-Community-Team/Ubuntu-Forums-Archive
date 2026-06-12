---
title: "Remote login vs ssh? Need a telecommuting environment"
date: 2006-10-28
forum: General Help
---

### Post by skelooth on 2006-10-28
Because of certain restrictions on my school's network I need to telecommute to a machine at home and use the internet connection there in order to work.

Right now I have open ssh daemon running which works fine but it's a little bit cumbersome in terms of 'clicking pretty icons'. 

Basically I need to be able to upload and/or edit scripts, run many of them at the same time (i've been doing it w/ multiple ssh logins), then I need to somehow download them.

For some reason I can not get proftpd or wuftpd to configure properly, >ftp tells me that the connection is refused.

I see some talk about remote login... how does this work? Will this allow me to use my remote machine via a thin client? Would I be able to use all of my XApps like gaim and GFTP? 

How can this be set up for optimal work performance? Any input, thoughts, and opinions are appreciated.

Edit:

I was considering of training a friend to be a coworker. Is there anyway to restrict access to sudo for an account?

---

### Post by beerfan on 2006-10-28
> **skelooth said:**
> Because of certain restrictions on my school's network I need to telecommute to a machine at home and use the internet connection there in order to work.

Right now I have open ssh daemon running which works fine but it's a little bit cumbersome in terms of 'clicking pretty icons'. 

Basically I need to be able to upload and/or edit scripts, run many of them at the same time (i've been doing it w/ multiple ssh logins), then I need to somehow download them.

For some reason I can not get proftpd or wuftpd to configure properly, >ftp tells me that the connection is refused.

I see some talk about remote login... how does this work? Will this allow me to use my remote machine via a thin client? Would I be able to use all of my XApps like gaim and GFTP? 

How can this be set up for optimal work performance? Any input, thoughts, and opinions are appreciated.

Edit:

I was considering of training a friend to be a coworker. Is there anyway to restrict access to sudo for an account?

You can use SSH to run remote programs, copy files, and do pretty anything else you need to do. You can create a GnomeVFS SSH mount in Places > Connect to server if you just want to drag and drop copy. You can use scp if you are comfortable at a cli. To run remote GUI apps run "ssh -X [email]user@remote.host.com[/email] myApp".

Read the manpages for "sudo" or "sudoers" to find out how that works. If you create new user accounts they should not have sudo capability unless you specifically grant it.

---

### Post by dbott67 on 2006-10-28
> **skelooth said:**
> I was considering of training a friend to be a coworker. Is there anyway to restrict access to sudo for an account?

Yes.  The default user account that you created was placed in the 'admin' group.  If you create a new user account for them, just make them a regular user.  Click on the **user priveleges** tab and uncheck **execute system administration tasks**.

---

### Post by dbott67 on 2006-10-28
For remote access to your home machine, you can tunnel VNC over SSH.  Basically, all VNC traffic (which is normally TCP 5500, 5800, 5900 depending on the mode) can be tunneled through port 22 (the SSH port).  Not only does it encrypt the data, the fact that you can already access your home computer via SSH means that you should be able to get it working.

There are plenty of tutorials on the internet, depending on whether you're going Window-to-Linux, Linux-to-Linux or whatever the case.  Here's a [good one to start with]("http://linuxplanet.com/linuxplanet/tutorials/6155/1/").

---

### Post by skelooth on 2006-10-29
dbott67 I just want to say WOW I had no idea I could mount an SSH connection. You've just increased my productivity right back to as if I were physically sitting behind the computer, and I've solved all types of logistical issues.

THANK YOU!

---

### Post by dbott67 on 2006-10-29
> **skelooth said:**
> dbott67 I just want to say WOW I had no idea I could mount an SSH connection. You've just increased my productivity right back to as if I were physically sitting behind the computer, and I've solved all types of logistical issues.

THANK YOU!

> **beerfan said:**
> ... You can create a GnomeVFS SSH mount in Places > Connect to server if you just want to drag and drop copy. You can use scp if you are comfortable at a cli. To run remote GUI apps run "ssh -X [email]user@remote.host.com[/email] myApp".

Read the manpages for "sudo" or "sudoers" to find out how that works. If you create new user accounts they should not have sudo capability unless you specifically grant it.

Well, it was 'beerfan' that told you, but you're welcome anyhow! ;)

-Dave

---

