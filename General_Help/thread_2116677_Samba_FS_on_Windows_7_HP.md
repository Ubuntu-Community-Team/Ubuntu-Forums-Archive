---
title: "Samba FS on Windows 7 HP"
date: 2013-02-16
forum: General Help
---

### Post by flapjacksmike on 2013-02-16
Hey all,

I'm new to the whole setting up a server thing, but I have a pretty good understanding of the Windows OS and gradually getting a hang of the Linux OS.

Current OS which I wish to interact with Samba FS using Ubuntu Server: Windows 7 Home Premium

My question here is if anyone knows if there is a way to use Samba FS installed on an Ubuntu server to control Windows 7 (below the Pro version) users' files like through the Samba FS. In my situation since the Windows OS is under the Pro version, is it possible to do it through the workgroup rather than the domain route (active domain directory) that you would have to do with a Windows Server.

My situation that I have is setting up a small network for file sharing between Windows and Mac OS. I want to use Ubuntu server since it is more in line with the UNIX structure, and with the Samba plugin I would like to manipulate files for Windows users to.

Thank you for your time.

Mike

---

### Post by flapjacksmike on 2013-02-16
Anyone out there?

---

### Post by gordintoronto on 2013-02-16
Don't use Ubuntu Server, use Xubuntu or Ubuntu or Linux Mint. The command-line interface is gruesome, and you don't need that level of torture.

Install Samba from the software center or Synaptic.

You can set up a shared folder from the file manager (Nautilus) in Ubuntu or Mint. With Xubuntu, you need to install system-config-samba as well as samba. "Samba" appears in System Settings.

If you share a folder or drive in Windows 7, you can "manipulate" it from any of the above distros. From the file manager, click on "network" and follow your nose.

---

### Post by flapjacksmike on 2013-02-17
Much thanks sir. :)

---

