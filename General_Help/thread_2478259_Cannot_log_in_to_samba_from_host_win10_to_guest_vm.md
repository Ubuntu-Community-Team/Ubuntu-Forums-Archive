---
title: "Cannot log in to samba from host win10 to guest vmware ubuntu 22.04"
date: 2022-08-21
forum: General Help
---

### Post by yogevch on 2022-08-21
[COLOR=#232629][FONT=-apple-system]I have a Windows 10 host, on which I run guest VMware Ubuntu 22.04.
Samba is installed on the guest. I've added the [homes] section in /etc/samba/smb.conf[/FONT][/COLOR]
```
[homes]
    comment = Home Directories
    browseable = yes
    path = /home/me
    valid users = me
    read only = no
```
[COLOR=#232629][FONT=-apple-system]Also set a samba password:[/FONT][/COLOR]
```
(echo me; echo me) | sudo smbpasswd -s -a me
sudo systemctl restart smbd
```
[COLOR=#232629][FONT=-apple-system]But I cannot log in from the host to samba.
wireshark recorded on the guest, shows the host resets the connection:
[/FONT][/COLOR][IMG]https://i.stack.imgur.com/SIceV.png[/IMG]

[COLOR=#232629][FONT=-apple-system]How can I fix it? Which more information is needed?[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Thanks[/FONT][/COLOR]

---

### Post by SeijiSensei on 2022-08-21
Why all the "echos" in the smbpasswd command? Usually I just use
```
smbpasswd -a username
```
and enter the password at the prompt.

For more debugging, look at the logs in /var/log/samba.

---

### Post by yogevch on 2022-08-21
Thanks for the reply!
The echos are because I wanted to make this part automatic and not interactive.

Actually there's nothing in the logs - I mean, no new logs are added

---

