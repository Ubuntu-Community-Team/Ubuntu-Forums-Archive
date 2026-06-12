---
title: "Quick and easy telnetd?"
date: 2006-07-20
forum: General Help
---

### Post by Mr. Picklesworth on 2006-07-20
I am having trouble with running a quick local telnet server in Ubuntu.

I have installed [this package]("http://packages.ubuntu.com/dapper/net/inetutils-telnetd"), restarted, tried running telnetd, checked running processes to find inetd which is present.
Telnetd does not seem to have opened a port.

Restarting the computer does not change anything, and I have uncommented the telnet lines in inetd.conf.

However, the connection fails when trying telnet from anything.
The plan is to Telnet to my PC using DSLinux on a Nintendo DS. I I doubt the problem is the router, as the DS can run telnetd just by me executing "telnetd", and anything on the network can connect to it.
Not much use, of course :P

Clearly, I really don't know what I'm doing.

I can't find a wiki entry, so is there a guide or a really nice forum thread about running a telnet server in Ubuntu?

For whatever help you can give, thanks in advance!

Edit:
Sorry to the below; Turns out the port was 21 :S
Don't know how I read that wrong...
Using telnet locally does not work, error is: Connection Refused.

---

### Post by swamytk on 2006-07-20
can you post the exact error message? are you able to login to telnet locally?

---

### Post by Mr. Picklesworth on 2006-07-20
Allright, my above problem was me coming back to a problem and forgetting that I had produced a simple and silly error while trying to fix it, thus assuming that the simple error was the problem... so ignore it.
After installing another telnetd package (just plain telnetd this time), port 23 is opened and the error message has changed.

Windows's telnet client freaks out and tells me the same old 'It Doesn't Work!' error message.
DSLinux and the computer running telnetd both give me the following error message when attempting to telnet (to localhost on the computer running the server, of course): "Connection closed by foreign host".


Edit:
Meh, Dropbear works :D

---

