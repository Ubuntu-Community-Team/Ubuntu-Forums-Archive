---
title: "Setting custom timeout for Samba"
date: 2022-05-24
forum: General Help
---

### Post by rottendurian on 2022-05-24
Hello,  Is there any way to set custom timeouts for Samba? I'd rather set the timeout to 1 second than the 1 minute that I keep coming across. If someone doesn't have proper access via Samba, why would I want them to wait 1 minute for it to timeout and tell them? It just gives them a reason try and bruteforce.

---

### Post by TheFu on 2022-05-24
1 second isn't really a good timeout. All sorts of things could delay something for a second.  Perhaps 10 seconds?
All the settings are documented in the manpage for smb.conf on your system. It is important to use the system-specific manpages, since the version of samba on my system is unlikely to be the same as on your system.

There are many different timeouts possible in the smb.conf file. Only you can decide which would be important in your situation, if you are running the samba server.

The client system, usually Windows, controls the timeout, not the samba server.  

On Linux, it is unlikely that uses are using a "samba client" - they are probably using a gvfs or gio 'helper' or perhaps udisks2, so any timeouts would be controlled by those tools.

---

### Post by rottendurian on 2022-05-25
Thanks, I actually have an intranet site managed by Samba and OpenVPN. So that's why I wanted to set a custom timeout for 1 second so that if someone doesn't have access, they are timed out right away "mimicking" the way the browser acts when you've tried to access a domain that does not exist on the internet. I used this guide to install both and was successful at creating my intranet sites. [https://www.digitalocean.com/community/tutorials/how-to-create-an-intranet-with-openvpn-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-an-intranet-with-openvpn-on-ubuntu-16-04). I'm also running Ubuntu 20.04.

When users run OpenVPN, it should allow them access to my sites properly. When disconnected from OpenVPN, it seems to take the server about 1 minute, give or take a few to timeout.

10 seconds does sound plausible. Will have to try that.

---

### Post by TheFu on 2022-05-25
A UDP-based VPN has special settings to allow CIFS/Samba access. Are those enabled?  Usually, those settings drastically reduce VPN performance and raise the load on the VPN infrastructure.  We always avoided CIFS access and would actively block it over the VPN where I work.  If people need to access files, they'd need to use a different protocol (usually sftp) or make use of the enterprise document management system. We had a number of different DMS - the most hated was called Sharepoint. It also had the most security issues, since it used WebDAV.  All the other DMS we had worked great under the VPN or at their desks inside a company building.

Just because something is supposed to be possible, that doesn't make it a good idea.

---

