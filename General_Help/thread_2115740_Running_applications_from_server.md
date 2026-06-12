---
title: "Running applications from server"
date: 2013-02-13
forum: General Help
---

### Post by BStrizzy on 2013-02-13
Hey guys, 

is there a way to have users run an application form an ubuntu home server rather than having to download it first. What im trying to do is have my roomate run an application on his windows machine but through ssh, it makes him download it first. he double clicks the executable while in the server to play form there, but it opens up as a notepad because it does not have the whole folder and dependencies to go with it.

advice?

---

### Post by papibe on 2013-02-13
Hi BStrizzy.

I'm not sure if I understood your concern, but let me show what I think is possible.

[LIST]
[*]Any computer with an ssh client, can log into the server and run a command line program there. It could be even left running on the server without a live connection by using tools like 'screen'.
[*]Any Linux client could run GUI applications that run using CPU on the server, but that are displayed on the client. You can simply use ssh with the trusted X11 forwarding option (-Y).
[*]In order to run a Linux application off a server on Windows, you would need 2 prerequisites:
[LIST]
[*]An native ssh client, Putty is the best IMHO, and
[*]An native X-Server installed on Windows, e.g., Xming or Cygwin/X.
[/LIST]
[/LIST]
I hope that help. Let us know how it goes.
Regards.

---

