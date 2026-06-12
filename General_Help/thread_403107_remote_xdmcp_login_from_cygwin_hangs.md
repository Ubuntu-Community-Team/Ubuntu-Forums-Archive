---
title: "remote xdmcp login from cygwin hangs"
date: 2007-04-06
forum: General Help
---

### Post by srhlefty on 2007-04-06
Hello everyone,
I've got what appears to me to be a funny problem.  I'm trying to log in remotely from windows to my Edgy box at home via cygwin/X's XDMCP method.  I can successfully reach the graphical login screen, so I know the connection is working correctly.  I can also ssh into my machine, also with success.  X-forwarding works as well.

However, when I try to login via the xdmcp method, I never actually get to my desktop.  The login screen goes away, and I'm just left with the mouse (which is still responsive) and an otherwise blank screen.

Here's another twist:  the ubuntu machine loads Beryl at login.  Could that be a source of problems?

I'm grateful for any insights or methods to help me debug this problem.

---

### Post by solar george on 2007-04-07
See if you can login to a failsafe session.

---

### Post by srhlefty on 2007-04-07
same result.  tomorrow I'm going to try disabling beryl and then attempt a log in.

---

### Post by srhlefty on 2007-04-07
(failsafe terminal works, but not failsafe gnome)

---

### Post by srhlefty on 2007-04-08
here's some more data:  after a failed login, I went home and looked at the logs in System->Administration->System Log

In syslog, I found the following line:

Apr  8 11:07:07 host-box gdm[5209]: gdm_slave_xioerror_handler: Fatal X error - Restarting remote.box:0

(where I have replaced the remote computer's ip with remote.box, and my local computer name with host-box)

---

### Post by ScottMorris on 2007-04-08
I had this same problem with Edgy but not with 7.04 Herd 5.  It would do just as you described.  I think its something with Cygwin as a Linux XDMCP client would login.

---

### Post by srhlefty on 2007-04-09
Interesting, I will have to try that.  I wonder if this isn't a new problem, because I have Dapper installed too, with the same result.

---

### Post by srhlefty on 2007-04-20
upgraded to Feisty last night, no problems there.  But my remote login still doesn't work from cygwin :( 

Suggestions on what to check?

---

