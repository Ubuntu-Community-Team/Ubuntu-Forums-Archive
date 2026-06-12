---
title: "Remote Desktop with Fresh Install"
date: 2018-08-27
forum: General Help
---

### Post by neutronforrest on 2018-08-27
Dear All,

I just did a fresh install of Ubuntu 18.04.  I have set the static IP address and can ssh into the machine.  I then setup remote desktop sharing.  When I try to connect with a another computer I cannot get the remote desktop.  I am using Remmina on another Ubuntu machine.  I get the following error:

SSH password authentication failed:  Access denied.  Authentication that can continue: publickey,password.

Can someone help me understand what I am doing wrong.  Thank you ahead of time.

CJ

---

### Post by HermanAB on 2018-08-27
Well, if the network is not configured right, then services on top of the network obviously won't work.

So do a few tests on BOTH computers and from the one to the other and carefully look at the error messages to figure out who is blocking/denying who:
$ ssh -vvv username@localhost

If that doesn't work, then the SSH daemon isn't running (or the username/password is wrong).


$ ssh -vvv username@ipaddress

If that doesn't work then it is likely that the network packet filter is blocking the access (or the username/password is wrong).

---

### Post by HermanAB on 2018-08-27
Read the error messages carefully.  SSH error messages are very specific.  They tell you exactly what is wrong.
"pam_unix(sshd:auth): check pass; user unknown"

So, you probably misspelled the user name.

---

### Post by neutronforrest on 2018-08-27
Hi Herman,

If I use Remmina with SSH everything connects fine.  Once I switch to VNC it gives the user unknown.  I am confident I have the name as password correct.  In the log file it says cforrest is user unknown.  This is the essential error I believe.

---

### Post by neutronforrest on 2018-08-27
I believe my issue is that Vino is not running.  I am unable to get Vino running.  Is this a known issue?

---

