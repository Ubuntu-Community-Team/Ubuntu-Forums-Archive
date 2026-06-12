---
title: "RDP connection without display from terminal"
date: 2018-12-07
forum: General Help
---

### Post by eddy16391 on 2018-12-07
Hi everybody,
I need to configure a crontab that open an RDP connection once a day and after 30 minutes closes it.
Now I use Remmina that from my notebook works great, but if I try to do the same things on my remote server it doesn't work and Remmina give me this error back:
```
(remmina:1611): Gtk-WARNING **: 12:31:34.600: cannot open display:
```
Any suggestion? Thank you!!

---

### Post by TheFu on 2018-12-07
Welcome to the forums.

You cannot open any GUI programs through cron.  GUI programs require an X-Session to work. Cron is purely a console/non-GUI tool.

If you want to start an rdp service daemon, do that without any GUI. You'll need to ensure the required environment variables are configured.   [https://help.ubuntu.com/community/xrdp](https://help.ubuntu.com/community/xrdp) ; BTW, rdp isn't secure enough to be used without a full VPN. Don't ever allow remote RDP over the internet without a VPN or ssh-tunnel first.

I don't use rdp, but I do use x2go.  There is an x2go-server which runs on a "headless" server here.  The server doesn't have a GPU installed. An x2go-client can connect over the network to the server and display a remote desktop.  I only use this over the internet, only with ssh-keys for authentication, never passwords.  
Whenever on the same LAN, I'll use X11-Forwarding that is built into ssh.  No need to run anything except sshd on the remote system.

---

