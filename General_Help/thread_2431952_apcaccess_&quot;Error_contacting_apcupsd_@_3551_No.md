---
title: "apcaccess &quot;Error contacting apcupsd @ :3551: No such process&quot;"
date: 2019-11-24
forum: General Help
---

### Post by kpatz on 2019-11-24
I solved my problem, but I figured I'd post it anyway in case it helps others.

I was having a strange issue with my Mythbuntu 16.04 box and apcaccess.

When I ran apcaccess (regardless of whether I use sudo or not), I get the error "Error contacting apcupsd @ :3551: No such process".  I've searched for this error online but couldn't find anything (I see plenty of posts about "Connection Refused" but not "No such process").

apcupsd is installed, configured and running.  I can access it using the cgi interface (multimon.cgi), apctest works, and apcupsd logs things successfully.  It's only apcaccess that isn't working.

I tried stopping and restarting apcupsd, no dice.  I verified the /run/apcupsd.pid had the correct PID in it and it did.  I was confused for a bit because of the 3551 thinking it was a PID but it's the port number, so that's irrelevant to this particular error.  Plus the CGI interface wouldn't be working in that case.  

I also have two 18.04 boxes with their own UPSes and they also run apcupsd, and apcaccess works properly on both.  And if I stop apcupsd on those boxes and run apcaccess, I get the "connection refused" error.  But on my 16.04 box, it still gives me "no such process", whether apcupsd is running or not.

**SOLUTION**:  I compared my /etc/apcupsd/apcupsd.conf files between my 16.04 box and one of my working 18.04 installs.  I found that on the 16.04 box, the line:```
NISIP 127.0.0.1
``` was commented out.  Uncommenting this line and restarting apcupsd solved my problem.

Seems odd it would say "no such process" in any case... but who knows.

---

