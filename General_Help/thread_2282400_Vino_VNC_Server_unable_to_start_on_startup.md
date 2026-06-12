---
title: "Vino VNC Server unable to start on startup"
date: 2015-06-14
forum: General Help
---

### Post by Bugh on 2015-06-14
So I am trying to get the Vino VNC Server to startup on boot, meaning I don't have to login to have the VNC Server start. I am on Ubuntu GNOME 15.04, and I have already added ```
/usr/lib/vino/vino-server
``` to 'Startup Applications', like so: [IMG]http://i.imgur.com/wWH4T3r.png[/IMG]. However, the VNC Server still won't start as soon as I boot up. I have to login in order for the VNC Server to start. What should I do?

---

### Post by nerdtron on 2015-06-14
does vino server start when you run it from the terminal directly by typing: "/usr/lib/vino/vino-server"?

You may need to delay the startup of vino to let all components of the load itself before starting vino-server. Try to set it command as: "sleep 20; /usr/lib/vino/vino-server"
This will wait for 20 seconds before starting vino server.
Example here: [http://www.howtogeek.com/189995/how-to-manage-startup-applications-in-ubuntu-14.04/](http://www.howtogeek.com/189995/how-to-manage-startup-applications-in-ubuntu-14.04/)

---

### Post by Bugh on 2015-06-14
> **nerdtron said:**
> does vino server start when you run it from the terminal directly by typing: "/usr/lib/vino/vino-server"?

You may need to delay the startup of vino to let all components of the load itself before starting vino-server. Try to set it command as: "sleep 20; /usr/lib/vino/vino-server"
This will wait for 20 seconds before starting vino server.
Example here: [http://www.howtogeek.com/189995/how-to-manage-startup-applications-in-ubuntu-14.04/](http://www.howtogeek.com/189995/how-to-manage-startup-applications-in-ubuntu-14.04/)

Yes, the Vino Server does start if I type it from the terminal, but before that, it is already started. After I tried adding the sleep 20 tag, Vino was unable to start up properly. It looks like I need to add it to systemd. Does anybody know how to do it?

---

