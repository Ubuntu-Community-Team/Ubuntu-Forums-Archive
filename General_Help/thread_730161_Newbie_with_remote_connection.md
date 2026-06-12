---
title: "Newbie with remote connection"
date: 2008-03-20
forum: General Help
---

### Post by Darkz_Soul on 2008-03-20
ok i have one simple problem my Vista machine will not connect to the Ubuntu 7.10 one. I can see the computer and use it shared drives but i cannot figure out how to remote connect. Can i use remote connection in windows? i don't want to install to many programs, and i want a GUI interface...the ubuntu machine can connect to the windows one but not vice versa. Please tell me what to do
Nate
The irony of my life

---

### Post by michaelaly on 2008-03-21
Look for a VNC viewer that runs on Vista, I've sucessfully done remote desktop from Vista to Ubuntu using a free program. I can't recall the name at the moment, but it was something like VNC Viewer, found on [www.download.com](www.download.com), just make sure your Ubuntu machine is setup to accept remote connections and it should work fine.

---

### Post by xarquid on 2008-03-21
Let's go over a few things to make sure this is accurately explained. To view your Linux box from your Windows machine, we need to make sure your VNC Server is running. To do this, simply go to:

[INDENT]Open the SYSTEM menu.
Click on REMOTE DESKTOP.
Under Sharing ensure "Allow others to view your desktop" is checked.
Under Security ensure "Require user to enter password" is checked (and enter a security password/phrase). This is for added protection.[/INDENT]
*NOTE: There are extra options available in this dialog that you may wish to configuration. Feel free!*

I recommend TightVNC as your viewer FROM your Windows machine. You can get it from:
[http://www.tightvnc.com/]("http://www.tightvnc.com/")

Download the Windows client (free one). Set it up. And you're pretty much good to go. Just run it.

What you will need to enter to access your remote desktop via VNC on your Ubuntu/Linux machine is the IP Address or host name on the LAN. 
*NOTE: If it is NOT ON THE LAN and on a WAN (such as you accessing your home machine from work), you'll have to make sure the port is properly forwarded through your router which is an extra step. If this needs to be done, please tell us. For now, I'll assume you just meant accessing through your LAN.*

Now to configure TightVNC over your LAN on your Windows machine, just open it up. 
[INDENT]Open the CONNECTIONS tab.
Enter the IP address of the Linux/Ubuntu machine you wish to access that you just configured and the rest of the settings prompted for in this menu.
Enter the password if you set one up in the previous step.
The screen should now load properly and display the desktop![/INDENT]

TightVNC assumes port 5900. I will assume you did not mess with the VNC port on Ubuntu. If you did, please enter/change the default port.

This should have you up and running remote desktop in no time.

If you need a client recommendation for viewing your WINDOWS DESKTOP -FROM LINUX/Ubuntu- I recommend Gnome-RDP. Just use Synaptic to install it. You can then access your Windows Desktop remotely from Ubuntu. :-)

Good luck! Please respond if you have any further questions or issues. If you have a router and need to forward a port just make sure to forward port 5900 (or the VNC port) to the proper machine/IP externally to internally (PORT FORWARDING in your router's settings, after logged in) and then it should work externally. You can usually find a guide on how to do this for your specific router if you do a Google search on your specific router with port forwarding added in the search phrase.

Sincerely,

Craig Huffstetler / xq / xarquid

---

### Post by Darkz_Soul on 2008-03-21
Thank you Vncviewer was great thank you i had never setup the ubuntu's remote settings just the program that i had installed...i have lost many hours reaserching for this

---

