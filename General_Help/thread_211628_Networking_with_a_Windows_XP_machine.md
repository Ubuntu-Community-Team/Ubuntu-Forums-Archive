---
title: "Networking with a Windows XP machine"
date: 2006-07-08
forum: General Help
---

### Post by boom2k1 on 2006-07-08
What is the easiest way to network with a Windows XP machine connected using the same wireless router?
THanks!

---

### Post by scxtt on 2006-07-08
samba ... it's already there/config'd on XP - you'd just have to set it up on ubuntu ...

preliminary things you should know:
[indent]-- XP's workgroup name
-- IP addresses of all boxes in question
-- if you can install samba packages in ubuntu[/indent]

---

### Post by Jagot on 2006-07-08
Samba:

[http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server](http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server)

---

### Post by radagast2 on 2006-07-09
Actually, other than adding myself as a samba user (doing "sudo smbpasswd -a username" and "sudo smbpasswd -e username"), I was able to configure my shares entirely through Nautilus (without editing smb.conf).  

Just right click on the folder you want to share, select "sharing" (which will even prompt you to install samba, if it's not already installed, though you'll still need to do the smbpasswd lines after the install), and choose "smb" as the method to share the folder.  I had to check the "Allow browsing folder" checkbox to actually see the share from Windows.

---

