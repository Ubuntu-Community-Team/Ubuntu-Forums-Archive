---
title: "GPROFTPD &amp; .exe files"
date: 2008-05-14
forum: General Help
---

### Post by ddixonr on 2008-05-14
I can't believe I've been running this program for almost a year and just now ran into this problem.

Gproftpd will not let me download .exe files. I added a new folder to put in some program files, dropped it into the ftp directory, and when I tried to save the file (right-click, save target as...), the error was "source file could not be read."

I wanted to make sure the entire folder wasn't misconfigured, so I dropped an exe into my music folder and the same thing happened. Then I dropped a music file into the programs folder and it opened just fine.

Also, just so I am clear, the file name, size, and timestamp of all the program files are visible in the list.

Please help. Thanks.

---

### Post by kellemes on 2008-05-14
Do you actually mean download? Or upload to a server?
The things that comes to mind is that a lot of servers are configured to not accept exe-files. Have you tried renaming the files?

---

### Post by ddixonr on 2008-05-14
I mean downloading. I can add the files to the ftp folder that is configured for the server, then I am able to view the entire list of files, but no way of saving them on another machine over the internet.

---

### Post by Monicker on 2008-05-14
How many different locations have you tried to download them from?  I wonder if something is filtering the ftp transactions.  At work we had a security appliance which could block the transfer of exe files in email and ftp.

---

### Post by ddixonr on 2008-05-14
Well, I am just able to test within the network- which should be the easiest place to download from, I think. By the "something" that is filtering, do you mean my isp?

---

### Post by Monicker on 2008-05-14
You mentioned trying to save from a machine over the internet, so I wasn't sure if you were trying to download them from within the same network as the ftp server or from a remote location outside of your network.  If you were trying to download from work, for example, then filtering is more likely.

---

### Post by ddixonr on 2008-05-14
Right, sorry about that. Yes, I am attempting to download from within my own network, and have not tried any other outside machines.

---

