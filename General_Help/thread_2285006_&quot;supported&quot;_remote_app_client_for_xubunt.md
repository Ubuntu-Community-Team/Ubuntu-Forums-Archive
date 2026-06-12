---
title: "&quot;supported&quot; remote app client for xubuntu??"
date: 2015-07-02
forum: General Help
---

### Post by Gary_Hobbs on 2015-07-02
Does anyone know of a Remote App client that is supported for Ubuntu?
One that has a GUI client interface that current office workers that use windows could use?
One that is installed through the software center?  I have a hard time uncompressing and compiling.
My test machine is running vivid but I am planning on using the current LTS to replace windows machines in our corporate office if I can run remote app packages that are currently provided by our Windows Server 2008 R2 running RDP service.

Thinrdc from [www.thinomenon.com](www.thinomenon.com) looked promising but I could not get the package installed.

---

### Post by TheFu on 2015-07-03
Why not just install rdesktop and give them a button on their desktops that makes the connection?  IF their Linux userid matches their Windows userid, this button could be simple: 
```
#!/bin/sh
RES="1280x738"
/usr/bin/rdesktop -u $LOGNAME -g $RES name-or-ip-to-windows-server &

```
There is Remmina Remote Desktop Client, but I find that too complicated. Also, MSFT changed the security for remote desktops sometime around Vista, so it may be necessary to alter the remote desktop settings on the MSFT-side a little. I've been using rdesktop for about ...10 yrs? Can't remember.

If you are compiling things, then you are doing it wrong for something like this ... actually for most things.

---

