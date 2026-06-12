---
title: "Nasty tsclient error"
date: 2005-04-01
forum: General Help
---

### Post by NTolerance on 2005-04-01
I am running the tsclient 0.132 on hoary Ubuntu and am getting this error when I try to connect to a Windows VNC server using fullscreen mode:

[img]http://img92.exs.cx/img92/2594/screenshotterminalserverclient.png[/img]

Windowed mode works fine other than an error message on exit, but if I enable fullscreen mode all I get is the above error.  It looks like a generic invalid syntax error, so I have really nothing to go on.

---

### Post by airflow on 2007-08-31
Nearly two and a half years later, I find this post because I'm having exactly this problem. Does anyone have a clue on how to solve this?

Is it possible to use the gnome tsclient to connect to a VNC-server using fullscreen? There seems to be a syntax error in tsclient, because when you check the option for fullscreen in tsclient, all you get is the above error-message which indicates that vncviewer was launched with wrong paramters.

Thanks a lot,
airflow

Update: Seems to be a bug, which nobody wants to fix: [https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/38281](https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/38281)

---

