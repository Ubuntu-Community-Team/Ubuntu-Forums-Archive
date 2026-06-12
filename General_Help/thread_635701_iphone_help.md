---
title: "iphone help"
date: 2007-12-09
forum: General Help
---

### Post by n0greenfx on 2007-12-09
i have and iphone that is unlocked to work with t-mobile it has ssh and bsd installed
i am following these instructions....[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

and it doesnt seem to be working here is wat the terminal looks like

god@god-desktop:~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/god/.ssh/id_rsa): 
/home/god/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/god/.ssh/id_rsa.
Your public key has been saved in /home/god/.ssh/id_rsa.pub.
The key fingerprint is:
e0:03:1f:ea:a4:b6:fa:63:fc:c4:1a:9e:e9:b3:b2:6e god@god-desktop
god@god-desktop:~$ ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.1.41
root@192.168.1.41's password: 
Permission denied, please try again.
root@192.168.1.41's password: 
Permission denied, please try again.
root@192.168.1.41's password: 
Permission denied (publickey,password).
god@god-desktop:~$

---

