---
title: "FreeNX problem"
date: 2007-10-14
forum: General Help
---

### Post by elmagozizou on 2007-10-14
Hi, Im trying to use FreeNx, but i get this message:

Info: Display running with pid '3572' and handler '0x502b4'.



NXPROXY - Version 3.0.0



Copyright (C) 2001, 2007 NoMachine.

See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.



Info: Proxy running in client mode with pid '3668'.

Session: Starting session at 'Sun Oct 14 15:53:35 2007'.

Warning: Connected to remote version 2.1.0 with local version 3.0.0.

Info: Connection with remote proxy completed.

Info: Using LAN link parameters 1536/24/1/0.

Info: Using pack method 'none' with session 'unix-application'.

Info: Not using NX delta compression.

Info: Not using ZLIB data compression.

Info: Not using ZLIB stream compression.

Info: Not using a persistent cache.

Info: Forwarding X11 connections to display ':0'.

Info: Forwarding auxiliary X11 connections to display ':0'.

Session: Session started at 'Sun Oct 14 15:53:35 2007'.

Info: Established X server connection.

Info: Using shared memory parameters 0/0K.

Error: Connection with remote peer broken.

Error: Please check the state of your network and retry.        <----------------

Session: Terminating session at 'Sun Oct 14 15:53:37 2007'.

Session: Session terminated at 'Sun Oct 14 15:53:37 2007'.



Before instaling FreeNX i was using the NoMachine server and all was find. Now I continue using the nomachine nxclient but in the server  i install freenx.

If you look the nxclient message you can see that the conection and the autentication is good, but then i dont understand why it fails.

Note: Sorry for my bad english, im doing what i can to comunicate whith you.

---

### Post by OffHand on 2007-10-16
I have this problem as well after my upgrade from Feisty to Gutsy. I will try to sort it out tonight and report back if I have found a solution...

---

### Post by OffHand on 2007-10-16
I have uninstalled FreeNX and installed the Free Server from:

[http://www.nomachine.com/download-package.php?Prod_Id=6](http://www.nomachine.com/download-package.php?Prod_Id=6)

I have used this guide to install it:

[http://ubuntuforums.org/showthread.php?t=493983&highlight=free+nx+server](http://ubuntuforums.org/showthread.php?t=493983&highlight=free+nx+server)

Works smoothly.

---

### Post by daflame on 2007-11-22
If you update to the latest version of FreeNX I have fixed these issues.  Try the packages for yourself.

Click [here]("http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx") to see the post.  Please contribute to the refinement of the installation.

---

