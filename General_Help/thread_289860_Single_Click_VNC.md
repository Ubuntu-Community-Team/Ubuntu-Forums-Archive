---
title: "Single Click VNC"
date: 2006-10-31
forum: General Help
---

### Post by kverde on 2006-10-31
Is there something like single-click VNC for Linux?  Or, is there a way to easily get remote GUI access to a machine that is behind a router?  

Single-click VNC  [(Read about it here]("http://ajaxtricks.blogspot.com/2005/11/put-geeksquad-out-of-business.html")) is incredibly useful for helping people.  It is for Windows.  But basically, you just point someone to an EXE file, when the run it you have access to their PC even if they are behind a firewall/router.  

I want to be able to access my parent's new Ubuntu Edgy Eft PC from my home so  I can help them if they run into problems.  

Thanks for any tips.

---

### Post by MetalMusicAddict on 2006-10-31
I dont know too much about single-click VNC but I run VNC on my server. I have other machines on the network with a launcher in their menus. I click on the launcher and Im there. 1 click. I dont see why you couldnt doo this over the net also. Just have all the IPs right in the launcher.

---

### Post by gumbald on 2006-10-31
FreeNX is far better than VNC, works on similar principle to Windows RDP. Can't remember which thread I used previously, but [http://www.ubuntuforums.org/showthread.php?t=241651&highlight=freenx](http://www.ubuntuforums.org/showthread.php?t=241651&highlight=freenx) looks a good place to start...

---

### Post by Ares139 on 2006-11-02
Hello, I'm a moderator from the UltraVNC forums.  Unfortunately, as far as I know, there is no way to get the SC server to work on Linux.  You can, however, use the UltraVNC viewer with WINE in order to connect to a Windows box running the SC server.  Note that you can't use the DSM plugin (although some people have reported that the plugin works if ran as root).

You're probably better off trying to use FreeNX and opening the ports in the router/firewall (or just use the built in Remote Destkop VNC built into Ubuntu and open port 5900 in the router/firewall).

For what it's worth, I'd love to see something like this for Linux as well.


-Ares

---

