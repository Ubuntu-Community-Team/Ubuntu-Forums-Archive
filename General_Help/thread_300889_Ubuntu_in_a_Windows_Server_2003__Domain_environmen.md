---
title: "Ubuntu in a Windows Server 2003 / Domain environment"
date: 2006-11-16
forum: General Help
---

### Post by brottman on 2006-11-16
I use Edgy on my computer at work, and our environment is all Windows Server 2003 servers and Active Directory. Whenever I try to connect to a server share on our network, it brings up a logon box, and I have to retype the correct domain name as well as my password.

1. I have set my ubuntu username to match my domain username exactly
2. The password is the exact same as well. 
3. I also modified /etc/hostname to be my FQDN:  ubuntu.domainname.local  

But as I said, when I try to connect to a share on our servers by typing "smb://servername/sharename, it pops up the logon box. It keeps defaulting to "WORKGROUP" even though I set the FQDN. Is there any way I can make my ubuntu just authenticate and connect to the shares without any hassle?

---

### Post by der_joachim on 2006-11-16
Have you tried putting the SMB shares in your /etc/fstab? There are some good guides in the HOWTO subforum. Works perfectly for me, both for local and remote servers.

---

### Post by jstueve on 2006-11-16
unless your machine is part of the domain (which means your work IT guys need to add it as a machine) then your stuck with authenticating each time...

---

