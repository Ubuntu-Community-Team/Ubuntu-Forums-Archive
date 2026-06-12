---
title: "Reduced X server through VNC"
date: 2007-04-23
forum: General Help
---

### Post by gejr on 2007-04-23
Does anyone know why this happens? I try to vnc into my opensuse box from ubuntu, but i only get that REALLY reduced X window. How can I make it show properly?

[http://geo.norvegium.no/Screenshot.png]("http://geo.norvegium.no/Screenshot.png")

---

### Post by dannyboy79 on 2007-04-23
not exactly sure but this is a setting on the vncserver as the vncviewer will only display what the server is serving. also, is it possible that the x-server version is different on ubuntu than on opensuse?

---

### Post by jtonk on 2007-04-23
you need vnc to to run a decent session manager try this for a gnome session in that console

gnome-session

If you want to make it permanent you can put

gnome-session &

in your ~/.vnc/xstartup

hope this helps :-?

---

### Post by dannyboy79 on 2007-04-23
jtonk, this is a little off topic, but I can't seem to get an X11vnc server to tunnel thru putty. The Xubuntu Edgy server is running ssh with firewall open on port 22 and it's running X11vnc on port 5900 with the firewall port closed as I only want to allow local connections.

The remote os is Windows XP Pro, I start putty and chose the source port as 5901 and the desitination as localhost:5900. I hit open and log into the machine and I receive a ssh session (my zonealarm alerts me that putty is trying to act as a server so it appears to work). Now I minimize that and then I open tightvncviewer and I type in localhost:0 but it states that it can't connect to server. I ahve tried :1, :5900, :5901 and nothing will connect. Can you suggest anyything or do you not tunnel vnc thru ssh?

---

