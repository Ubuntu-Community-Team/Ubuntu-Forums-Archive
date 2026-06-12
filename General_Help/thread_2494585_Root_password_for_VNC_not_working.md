---
title: "Root password for VNC not working"
date: 2024-01-20
forum: General Help
---

### Post by ujjwalrathod007 on 2024-01-20
Hi,

I want to access ubuntu server desktop and for that I created a VNC server on ubuntu running on raspberryPi. I remember that I once or twice got the screen working but now VNC displays screen with root login and the password does not work anymore.

---

### Post by TheFu on 2024-01-20
Never login as root with a GUI under Ubuntu. This causes all sorts of problems.

---

### Post by MAFoElffen on 2024-01-20
+1 -- But...

You need to understand how the Linux Graphics Layer works for Ubuntu. If you understood that, then you would understand that is doesn't work for the root user without a lot of hacking, which in Ubuntu Security terms, opens up some vulnerabilities.

You don't believe me? Start up Ubuntu as Recovery and drop to a root prompt > startx... It fails, because user root is not set up (for security reasons) to start a graphical session...

The correct way to setup a remote login, is to create, and use a remote "User" that has the correct access rights and privileges that you would want to give someone with remote login access. That is not just true for Linux, but any OS. That is just common sense.

---

### Post by ujjwalrathod007 on 2024-01-21
Well, I am not a ubuntu graphics manager expert in any way but seems that I also have less understanding of root user and why login in as root could be problematic. But I am Linux user since long. Hence, whenever I try to login, the display is always comes with root credentials. I am confused how to overcome this situation.
I have even created a new user...

---

### Post by TheFu on 2024-01-21
On the remote system
[LIST=1]
[*]Create a new user, non-root.
[*]Setup that user to run the VNC-server process. Be certain that the older, root-version of vnc-server is NOT running.
[*]Set the login password for that non-root userid.
[/LIST]

On the local workstation:
[LIST=1]
[*]Connect to the VNC-server on the correct port from a different workstation.
[*]Login using the password you just set.
[/LIST]

However, you do realize that VNC is one of the worst solutions for this type if need from both a performance and security aspect.  There are better solutions.  If the raspberry pi is on the same LAN as the workstation you will connect into, just use **ssh -X** to run whatever GUI program you want on the Pi, but have the window for that program displayed on your local workstation.  This has worked since the mid-1990s and it works really well for almost any use.

---

