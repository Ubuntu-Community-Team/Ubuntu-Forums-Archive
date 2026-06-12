---
title: "NoMachine NX/FreeNX and Ubuntu? (remote admin)"
date: 2004-12-01
forum: General Help
---

### Post by A1ex on 2004-12-01
Has anybody tried using the NX packages ([http://www.nomachine.com/](http://www.nomachine.com/))with Ubuntu?

I love Ubuntu and the only thing stopping me moving it from the VM to my hard disk is the lack of remote admin in linux.

Let me clarify before I get a torrent of "webmin","vnc", "XDMCP" etc :) 

Specifically remote admin that mimics windows 2003 terminal services, where a session can be left running after I log out, then I can reconnect to the session again. 

Currently I use xvnc so I get the benifits of VNC and a proper login but I still can't leave a session running. NX looks like the only product that actually offers this functionality but seems broken on debian/ubuntu.

Has anybody tried the NX packages or knows a way to get this functionality without using NX?

---

### Post by quick_snack on 2005-05-07
Can this be done by adding a user 'remadmin' in ubuntu a as remadmin starting  vncserver :screennumber with password xxxx.

When connecting to ip:screennumber you would get a remote screen that would remain after you logged out.

---

