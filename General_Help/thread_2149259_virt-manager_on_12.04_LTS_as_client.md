---
title: "virt-manager on 12.04 LTS as client"
date: 2013-05-28
forum: General Help
---

### Post by Bildge Cricket on 2013-05-28
Hi All

I am by no means an expert on Linux, let a lone Ubuntu. I have however been tasked to get our VM setver in the office up and running. The server is a Ubuntu server running two VMs at the moment.

My machine (that I am trying to connect from) is a MacBook Pro (Intel) running VirtualBox with Ubuntu 12.04 LTS as the VM.

I keep getting the same error when trying to *run sudo virt-manager*:

*  File "/usr/share/virt-manager/virt-manager.py", line 452, in <module>*
*    main()*
*  File "/usr/share/virt-manager/virt-manager.py", line 346, in main*
*    raise RuntimeError(_("Unable to initialize GTK: %s") % str(e))*
*RuntimeError: Unable to initialize GTK: could not open display*

I would be very grateful if someone can point me in the right direction that will enable me to access Virt-manager

Thank You

---

### Post by dino99 on 2013-05-28
[http://askubuntu.com/questions/93147/unable-to-use-virt-manager](http://askubuntu.com/questions/93147/unable-to-use-virt-manager)

---

### Post by btindie on 2013-05-28
You don't need to run virt-manager using sudo. Just make sure your user account is a member of the libvirtd group and it'll have the required permissions to communicate with the daemon via the socket.

```
sudo usermod -a -G libvirtd myuser
```

You may need to log out and in again for that change to take affect under the desktop.

As you're running OSX you should be able to ssh into your Ubuntu VM and use X-Forwarding to run virt-manager locally

from the mac terminal
```
ssh -X ubuntu_user@ubuntu_VM
virt-manager &
```

---

