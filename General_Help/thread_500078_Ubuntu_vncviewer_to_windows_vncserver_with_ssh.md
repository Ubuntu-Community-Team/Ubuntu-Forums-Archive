---
title: "Ubuntu vncviewer to windows vncserver with ssh"
date: 2007-07-13
forum: General Help
---

### Post by tthkbw on 2007-07-13
I have looked and looked and can't find the answer to this problem.

I have a windows machine running vncserver at work, and an Ubuntu desktop box at home.

I want to connect to the windows machine's vncserver with vncviewer from my home Ubuntu machine.  I have been able to do this using an OpenVPN server on the work network, but now I must make the connection using ssh and tunneling.

The ssh connection to the windows box works fine.
I connect to the Windows box using:

   ssh -L 5903:127.0.0.1:5903 bigbox

This connects fine.

Then, in a separate terminal window on the Ubuntu box, I do:

  vncviewer localhost:3

I get the following:

UbuntuLittleBox:~ 347> vncviewer localhost:3

VNC Viewer Free Edition 4.1.1 for X - built Jan  7 2007 17:30:38
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri Jul 13 08:51:56 2007
 CConn:       connected to host localhost port 5903

Fri Jul 13 08:51:57 2007
 CConnection: Server supports RFB protocol version 3.6
 CConnection: Using RFB protocol version 3.3
 main:        Your connection has been rejected.

I know the Ubuntu desktop by default uses vino for remote connections, and I have used system/preferences/remote desktop to disable this, but I still get this error.

I know I should be able to make this work--any help?

thanks

Terry Brown

---

