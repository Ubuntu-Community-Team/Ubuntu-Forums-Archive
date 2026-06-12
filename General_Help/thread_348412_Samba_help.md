---
title: "Samba help"
date: 2007-01-28
forum: General Help
---

### Post by bugs_bunny_61 on 2007-01-28
Hi everybody,

I need some help with Samba and sharing with Windows boxes on my network.

I have Ubuntu Edgy and I try to share some folders with my other Windows XP boxes. After reading a few tutorials about Samba I ended up doing the following:

- installed (with Synaptic) samba and smbfs;
- edited /etc/samba/smb.conf and added/changed the following:
   [global]
   workgroup = MSHOME
   netbios name = myserver

####### Authentication #######
  security = user
  username map = /etc/samba/smbusers

#======================= Share Definitions ================

[homes]
   comment = Home Directories
   browseable = yes 

- entered in terminal and added password for 'myuser':
sudo smbpasswd -a mysuser

- my /etc/samba/smbusers has one entry (my username created when I installed Ubuntu):
system_username = myuser

- entered in terminal the following:
  sudo testparm
  sudo /etc/init.d/samba restart

After all this I go on a Windows box, I ping my Ubuntu box and I get reply, so both machines are OK in my network and the router let them see each other. On a Windows box, I open Windows Explorer and I enter "\\myserver\". I get "Windows cannot find '\\myserver\'...". I try to browser MSHOME and my Ubuntu box is not there.

Any suggestions?

Thanks,

---

