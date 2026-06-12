---
title: "VNC viewing problem"
date: 2008-01-27
forum: General Help
---

### Post by harrybazeegar on 2008-01-27
I am running Ubuntu 7.04 and i installed vncserver and viewer on my computer...

The server starts without any problems... 
but when i connect to myself 
```
$ vncviewer localhost:1
```

i am not able to view my desktop... i get a window like this:

[[Screenshot]]("http://www.mediafire.com/?0mxndz3u0y1")

I googled about this problem and i found out that i am supposed to have some xstartup file in my ~/.vnc directory... but I dont have any such file... all the files in that directory are :

bazeegar:1.log  bazeegar:1.pid  passwd 

(bazeegar is my host name)
so whats the prob? :(

---

### Post by HermanAB on 2008-01-27
People coming from Windowsland always want to try out VNC, since it is similar to Windows RDP.  However, you'll have better luck with SSH.  SSH is secure, very easy to set up and use and can do many things that VNC cannot do.

---

### Post by kendalc on 2008-01-27
Yeah kinda unrelated but seemingly much simpler...

I was just about to post my problem about vnc on here...  I can't connect to my Windows comp on the same LAN...  I opened up port 5900 through the firewall and set no authentication, and even set a static IP address of the form '192.168.1.5#'.  I've tried just about every IP or comp name combination in vncviewer.  Anyone know what form it wants/ something I'm missing???  Tried XXX.XXX.X.XX and XX.XX.XXX.XXX both, along with :5900 and .5900, as well as the computer name.  Yes, server is running on the other comp...

---

### Post by HermanAB on 2008-01-27
This may help:
[http://aeronetworks.ca/vnc-howto.html](http://aeronetworks.ca/vnc-howto.html)

Usually w.x.y.z:5901 or some such.

---

### Post by harrybazeegar on 2008-01-27
I am pretty comfy using ssh.. the problem comes when i want to use some IDE like Eclipse on my comp from elsewhere...  is the resolution of the display causing problems?

also plz tell me what i could do via ssh that i cannot do on vnc... jus want to know :)

---

### Post by mortsahl on 2008-01-27
On my home network I've got 5 machines ... 2 Ubuntu, 3 windows.  I use RDP for the windows boxes as it's much faster than VNC.  On windows you'll have to set it up to allow RDP ... On the other Ubuntu box I use VNC ... all that was needed was to install the VNC server on it, then the VNC viewer on my main machine, and it worked.  I don't use a firewall inside my network ... I've got a hardware firewall facing the outside world.

Good luck.

---

