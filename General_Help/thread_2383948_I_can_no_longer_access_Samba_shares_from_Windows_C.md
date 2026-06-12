---
title: "I can no longer access Samba shares from Windows Computers"
date: 2018-01-31
forum: General Help
---

### Post by Chris_Nicol on 2018-01-31
I had previously set up 2 Linux servers for backup and used the walk through at the following link to set up Samba to join my windows domain controller and active directory.

[https://www.tecmint.com/join-ubuntu-to-active-directory-domain-member-samba-winbind/](https://www.tecmint.com/join-ubuntu-to-active-directory-domain-member-samba-winbind/)

It worked well until about 2 weeks ago.  If I do the following command - wbinfo -u no users would be listed.  I tried to completely remove samba and start over on one of the servers.  I was able to get Samba and the dependicies all reinstalled and I was able to use the command knit to test the domain log in.  However, when I try to run this command:

sudo systemctl enable smbd nmbd winbind

I get this response:

~$ sudo systemctl enable smbd nmbd winbind
smbd.service is not a native service, redirecting to systemd-sysv-install
Executing /lib/systemd/systemd-sysv-install enable smbd
nmbd.service is not a native service, redirecting to systemd-sysv-install
Executing /lib/systemd/systemd-sysv-install enable nmbd
winbind.service is not a native service, redirecting to systemd-sysv-install
Executing /lib/systemd/systemd-sysv-install enable winbind

I don't know where to go from here.  Does anyone know if there has been changes that require me to do something different.

Thanks,
Chris

---

