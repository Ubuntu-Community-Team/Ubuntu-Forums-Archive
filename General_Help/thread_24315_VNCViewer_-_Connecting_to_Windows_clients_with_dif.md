---
title: "VNCViewer - Connecting to Windows clients with different ports"
date: 2005-04-06
forum: General Help
---

### Post by JGJones on 2005-04-06
I would like to use VNCViewer to access other Windows machines running VNCServer (or using a helpdesk program that does a reverse connection to a listening VNCViewer) but they use different port numbers from the default of 5900 in Linux.

How do I connect to those machines running VNCServer with their port number (NOT display number)?

If I attempt to do it in Gnome Terminal Client software ie as:

<ip number>::<port number> eg like this:

67.123.43.56::7402

I use double : because that's how it is done in Windows, but obviously it does not work in Linux. So I use single : and that does not work either since that's a display number.

How do I set up VNCviewer so that I can connect to different vncserver on different port numbers?

And finally slight different question...I know by default ports are closed on Linux, thus I would need to open some to allow a listening VNCviewer to listen on those ports....how?

At the moment I am dual-booting between Windows/Ubuntu so that I can do the above in Wnidows but I'll like to move it to Ubuntu.

---

### Post by bonifacio on 2005-04-07
Have you tried the applet client?  That will give you an option to type your port number.  I know for one that Real VNCServer has this feature.  It may not be exactly what you want but another way of accomplishing your task.

Fire up your browser.  Type this URL: http://<host>:<port>/

Of course java needs to be installed.

---

