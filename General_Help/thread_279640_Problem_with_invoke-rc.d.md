---
title: "Problem with invoke-rc.d"
date: 2006-10-18
forum: General Help
---

### Post by nevyndweomer on 2006-10-18
I have just upgraded from breezy to dapper and now I have strange behaviour while using invoke-rc.d 

what is happening is this  ...

When I run the invoke-rc.d exim4 stop
I check with ps -ef and there is still an exim process running
[115      14932     1  0 Oct17 ?        00:00:00 /usr/sbin/exim4 -bd -q30m]

I am still able to send e-mail using my outlook client from a remote machine

if I run an invoke-rc.d exim4 start
I get errors saying port 25 already in use
[2006-10-18 12:01:29 socket bind() to port 25 for address (any IPv6) failed: 
Address already in use: waiting 30s before trying again (9 more tries)]
and ps -ef shows two exim processes running ...
115      14932     1  0 Oct17 ?        00:00:00 /usr/sbin/exim4 -bd -q30m
root     18514     1  0 12:01 ?        00:00:00 /usr/sbin/exim4 -bd -q30m

If  I do another "stop" they are both still there

Why is the invoke-rc.d successfully starting the process but unable to stop it

---

