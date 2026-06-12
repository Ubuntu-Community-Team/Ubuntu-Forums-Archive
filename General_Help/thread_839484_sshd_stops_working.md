---
title: "sshd stops working"
date: 2008-06-24
forum: General Help
---

### Post by Ancan on 2008-06-24
Hi!

I have moved from using Windows to a x64 edition of Ubuntu 7.10  as a VMware Server host. I'm mainly a Windows-guy, but I'm trying to move away from windows for my home network. Still, the linux-competence is still very lacking.

The problem is that after a couple of months or so, sshd seems to stop working. If I try to connect to the server via ssh/putty, i get to enter my username/password, but immediately get a "connection closed by host" message.
I've tried running the sshd in debug mode ("sshd -dD" I belive I used), and the console then showed a "signal 11 recieved". I'm quite new to linux, but some googling gives the impression that this is some kind of general crash-code.

I have run in to this issue twice now, but the first time I hade to reinstall the server for other reasons, and it disappeared. Now it's here again, and it's quite frustrating since it removes the only comfortable way I have to administer the server.

Some help would be much appreciated.

Regards,
Anders

---

### Post by geirha on 2008-06-24
Check what /var/log/auth.log says.

---

### Post by HermanAB on 2008-06-24
Run ssh in debug mode:
ssh -vvv user@server

Cheers,

H.

---

### Post by jimv on 2008-06-24
Probably something got f'd up in the config files.  Here's what I would do (unless you have some special configuration for ssh):

Open a terminal on the server and type:

sudo apt-get remove --purge openssh-server
sudo rm /etc/ssh/sshd_config
sudo apt-get install openssh-server

And then on the client:

mv ~/.ssh/config ~/.ssh/config.bak

^That file might not exist.

---

### Post by Ancan on 2008-06-27
Got it working now. Did a uninstall like jimv suggested. When installing again, I had do manually create the /etc/ssh directory, or it didn't install.

A bit strange that sshd just stops working. When I left for vacation, four weeks ago, it worked. When I came back it did not, and the only thing the server has been doing is working as a VMware host.

Thanks all,
Anders

---

