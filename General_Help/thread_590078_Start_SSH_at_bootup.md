---
title: "Start SSH at bootup"
date: 2007-10-24
forum: General Help
---

### Post by Yarbo on 2007-10-24
Hi, so I am new to this linux stuff, but so far am having a good time.

I wasn't sure where to put this, so I put in here in general discussion.

I installed openSSH through the add/remove programs, and made sure that it starts using bum. It all worked great, but lately I have been accessing my linux machine strictly through ssh, so I am restricted to the command line.

I recently compiled a new kernel and installed it, but don't want to reboot remotely, because the last time I did, I was unable to log back in with SSH until I got home to put in the username and password locally.

It appears that when I reboot, SSH does not start until after I get passed the Ubuntu log-on screen.

Is there anyway I can make it so I can SSH into my box even while it is on the log-in screen?

On top of that, is there anyway that I can do all of this remotely?

---

### Post by dayvy on 2007-10-24
You shouldn't have to login in locally to be able to login remotely via ssh. The sshd should start before your computer reaches the login window. Is S16ssh in your /etc/rc2.d directory? 

d.

---

### Post by Yarbo on 2007-10-24
Yes. S16ssh is in my /etc/rc2.d directory.

Maybe it was just a delay thing, cause the last time I used the reboot command to reboot remotely, I was unable to log back in with PuTTY remotely until I had someone actually enter the username and password before I was able to log in again.

---

