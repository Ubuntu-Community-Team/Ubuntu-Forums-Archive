---
title: "VNC Viewing Bugs?"
date: 2007-10-13
forum: General Help
---

### Post by #Reistlehr- on 2007-10-13
I have about 9 computers in my house running some sort of linux from freebsd to fedora 8, to ubuntu. I cant seem to figure out the problem.

Problem: When connected remotley to another computer, FROM ANY computer, VNC changed to not get updated in the viewer, but you can view the changes on the server you are connected to.

To explain a little better, if you are sitting next to the computer you are remoted into, and use the server's screen, you can control everything fine. If you use the VNC Viewer/client of any type, windows OR linux, any changes you make are not displayed on the client, only the server.

Example: Using the client you drag a window. The window is moved on the server, but it is not moved on the client. It's like you're staring at a screenshot that wont refresh evern when forced.

Any help would be appreciated.

---

### Post by #Reistlehr- on 2007-10-24
Upgrading to gutsy, i finally have control. When i move a window, it moves on both the host and the viewer. Only thing is, it's so laggy, it's not useable.

---

### Post by Mantastic on 2007-11-06
I'm having similar problems.  I'm connecting to my Gusty Gibbon machine through my local network from a Windows machine.  It appears that GUI widgets are having trouble updating on my VNC client.

For example, if click on the "Places" menu nothing will show up on my VNC client until I mouse over each menu item.  Then only that menu item will appear and there will be gaps in between each menu item widget.  This leads me to believe that my problem lies in system calls for updating a GUI widget not being caught on my client.

...or something.  I don't know.  Any ideas what I can do?

Oh, and I'm using the VNC server that comes with ubunutu and RealVNC client on the windows machine.  No config files have been touched (yet).


EDIT - Ah ha!  I fixed it.  I didn't touch any config files, but I DID enable restricted video driver's for my ATI video card (9600 to be exact).  To fix the problem, I went to System -> Administration -> Restricted Drivers Manager.  Then I unchecked the Enabled box next to ATI accerlated graphics driver.  This solved all the problems and it runs great now.

---

