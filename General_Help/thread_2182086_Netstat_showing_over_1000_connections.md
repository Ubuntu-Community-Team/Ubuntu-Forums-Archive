---
title: "Netstat showing over 1000 connections"
date: 2013-10-20
forum: General Help
---

### Post by kersten2 on 2013-10-20
Hi I'm new to Ubuntu having installed ubuntu desktop and server about 2 months ago. I share an internet connection with my flatmate and recently we noticed the internet getting slower and slower. After several conversations with our provider, we were asked to open a terminal and enter 'netstat'.
My flatmates mac showed about 7 connections, mine shows over a thousand.
What are these connections and how do I close them? 
A small sample:
unix  3      [ ]         STREAM     CONNECTED     17231    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16519    
unix  3      [ ]         STREAM     CONNECTED     844049   
unix  3      [ ]         STREAM     CONNECTED     15121    
unix  3      [ ]         STREAM     CONNECTED     13626    
unix  3      [ ]         STREAM     CONNECTED     9607     
unix  3      [ ]         STREAM     CONNECTED     15562    @/tmp/dbus-JSFxppUo13
unix  3      [ ]         STREAM     CONNECTED     14982    
unix  3      [ ]         STREAM     CONNECTED     14178    @/tmp/dbus-JSFxppUo13
unix  3      [ ]         STREAM     CONNECTED     15151    
unix  3      [ ]         STREAM     CONNECTED     799531   
unix  3      [ ]         STREAM     CONNECTED     14987    
unix  3      [ ]         STREAM     CONNECTED     13612    
unix  3      [ ]         STREAM     CONNECTED     11749    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15216    @/dbus-vfs-daemon/socket-5DMXBIdy

As far as I'm aware, i'm not streaming anything and only use my browser. Apache is running but it makes no difference if I shut down apache.
I mainly use this as a desktop pc.
I installed ubuntu 12.04 LTS
How can I find out what these connections are and more importantly, how can I close them? I have run a virus scan and quite a lot showed up, but they've all been deleted now. Can anyone help?

---

### Post by t0p on 2013-10-20
Netcat isn't showing you just connections over the internet, they're mostly internal connections within the operating system.

To see just the internet connections, use command

```

netstat -tcp

```

Then netcat will display the current internet commands.  It'll keep scrolling, showing connections that it's already displayed.  It will show you the IP address of the servers you're connecting to, the status of that connection, and the program that has made the connection. Hit Ctrl-C to stop the display.

---

### Post by kersten2 on 2013-10-20
Thanks very much! At least I now know it's not my pc causing the problem, thanks again.

---

