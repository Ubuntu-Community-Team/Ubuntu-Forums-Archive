---
title: "Viewing webpage over network - default firewall?"
date: 2007-06-11
forum: General Help
---

### Post by harner on 2007-06-11
I installed 2X ThinClientServer on a Kubuntu Server 7.04 box.  Before you close this thread, let me tell you what is it.  2X TCS allows me to boot an image over the network, using a tftp/pxe solution.  Okay, before I can even get the TFTP and PXE off the ground, I need to configure it with the web interface.

This box is not a typical LAMP server.  It uses its own DB via port 3306, and its own tftp server.  It hosts the web interface on port 980.

When I type [http://###.###.##.###:980](http://###.###.##.###:980) into an address bar in Firefox, I get an error stating Access Denied!

When I type in the URL:port on the actual kubuntu box, it works just fine.  Is there a built-in firewall?  I can ping it, but can't get in there to access the page.  Help?

---

### Post by harner on 2007-06-12
bump

---

### Post by timcredible on 2007-06-12
if you get that message, that means you got to the server.  sounds like the application itself is denying the connection.  i would check the app first.

also, along the same lines as 2x, have you tried pxes?  boots off cd and runs nothing except your choice of xdmcp, citrix client, rdesktop, so you can access a server.  similar concept, just different place for the actual processing (2x puts the processing on the thin client, pxes puts it on the server).

---

### Post by harner on 2007-06-12
I'm only trying 2X, because they have an image built which shoots to the terminal servers.  Does PXES have an image?

I did attempt PXES but couldnt figure out how to get the netboot working.  Also, I do know it has a cd image, but some machines I'm using Citrix with will be winterms.

Thanks for the advice!

---

