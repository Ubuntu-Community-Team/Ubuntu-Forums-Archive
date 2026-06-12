---
title: "Fail to remote access VM"
date: 2018-01-31
forum: General Help
---

### Post by satimis on 2018-01-31
Docker on Ubuntu 16.04 as VM
Host - Ubuntu 16.04 desktop
VirtualBox

On Docker
=========
ip: 192.168.8.59
darktable installed

Edit /etc/ssh/sshd_config
change 
ForwardX11 no
to
ForwardX11 yes

Reboot Docker

On Host Terminal
=============
Run;
$ ssh 192.168.8.59
$ export DISPLAY=:0
$ darktable```

[defaults] found a 64-bit system with 1016044 kb ram and 1 cores (0 atom based)
[defaults] setting very conservative defaults
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(darktable:2549): Gtk-WARNING **: cannot open display: :0

```

Failed

Please help

satimis

---

### Post by TheFu on 2018-01-31
try: **ssh -X 192.168.8.59**
and there's no need to set the DISPLAY.

The virtualbox/docker setup isn't clear. Doubt that matters.

---

### Post by satimis on 2018-01-31
> **TheFu said:**
> try: **ssh -X 192.168.8.59**
and there's no need to set the DISPLAY.

The virtualbox/docker setup isn't clear. Doubt that matters.
Hi,

Thanks for your reply.

If I recall correctly I followed below document installing docker;

How to Install and Manage Docker CE on Ubuntu 16.04 & 14.04 LTS
[https://tecadmin.net/install-and-manage-docker-on-ubuntu/#](https://tecadmin.net/install-and-manage-docker-on-ubuntu/#)

on Ubuntu 16.04 server.

X11 app not installed yet.

I'm not quite clear.  Should I install X11 app I can start X on docker VM itself.   I don't need remote access docker VM. 

What I expect to achieve is running darktable.  I don't mind running it on docker VM or remotely on Host.  Can I use X11 on the Host to get it work?

A further question:
==============
Docker has been installed quite sometime but not running.  It is for testing only.

Can I install KVM or VirturalBox on docker?  That is running another virtual machine on a virtual machine?  But the OS is Ubuntu 16.04 server, NOT desktop.

If it is possible then I'll install a new VM for running darkroom on the new virtual machine

Please advise.

Thanks

Regards
satimis

---

