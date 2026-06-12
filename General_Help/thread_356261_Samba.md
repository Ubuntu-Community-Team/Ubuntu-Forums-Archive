---
title: "Samba"
date: 2007-02-08
forum: General Help
---

### Post by Rich78 on 2007-02-08
Is Samba only used for Linux > Windows networking or can it be used for Linux > Linux networking?

Is it a good method to use for Linux > Linux networking such as File sharing?

I'm wanting to setup a small business network, to replace a currently Windows only setup.  I want to use Ubuntu Server instead of Win 2003 Server and Ubuntu desktops instead of WinXP desktops.

In order to do this though I need to setup a File & Print Server on the main Ubuntu server.

Any recommendations?

Thanks

---

### Post by tocleora on 2007-02-08
Here's a thread that may help answer a few of those questions for you:

[http://www.ubuntuforums.org/showthread.php?t=352335](http://www.ubuntuforums.org/showthread.php?t=352335)

In summary, Samba is good if windows will be included in the sharing, but most people it seems recommend NFS.   If you are going to have windows comps on it too you should use Samba if I'm not mistaken.

---

### Post by rturner on 2007-02-08
I've got an ubuntu box set up as a file server and lampp server for internal testing of web applications.  The rest of the computers are Windows XP.  Samba works fine for that.  I found it easier to have my linux account username/password set up as accounts on the windows machines.  Also, I believe that when you install samba, smbclient also installs.  You should install smbfs as well (includes mount and unmount commands) if you want to mount windows shares from the linux box.  Not sure how to share the print server from linux.  Mine is stand-alone on the LAN and all the machines use it.  I also have static IP address on the linux server and print server.

---

