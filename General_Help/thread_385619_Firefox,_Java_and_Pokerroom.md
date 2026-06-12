---
title: "Firefox, Java and Pokerroom"
date: 2007-03-15
forum: General Help
---

### Post by b0z0 on 2007-03-15
Hi,

I have a small problem with Firefox and Java. To let you know I'm running x86_64 Edgy.

When I go to pokerroom.com and want to start the java client, sometimes(not always) firefox just 
quit without any error on screen.  Sometime the client loads but when I want to join a game it crash.  Sometime I can play for hours without nothing happening.  But as soon as I leave the table and try to join another, it can crash.  

Here's a snippet from the hs_err_pid file.  I have a bunch of them since sometime it can take up to 15 time before I can start to play.  Very frustrating.

Any idea anyone

Unexpected Signal : 11 occurred at PC=0x2ACE48D49DAA
Function=(null)+0x48D49DAA
Library=/usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so

NOTE: We are unable to locate the function name symbol for the error
      just occurred. Please refer to release documentation for possible
      reason and solutions.


Current Java thread:
	at sun.plugin.navig.motif.AThread.handleRequest(Native Method)
	at sun.plugin.navig.motif.AThread.JNIHandleLoop(AThread.java:35)
	at sun.plugin.navig.motif.AThread.run(AThread.java:27)

---

