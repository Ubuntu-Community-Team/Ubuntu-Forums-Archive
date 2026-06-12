---
title: "using ubuntu for nas device"
date: 2008-04-26
forum: General Help
---

### Post by not_yet on 2008-04-26
Hi,

Appologies if this is a dumb question:?:

I have a spare box with Hardy on it. Can this be setup as a NAS device?

Basically I want to backup files, and be able to get at them over the internet if I need to.

Is there a tutorial someplace for this?

thanks

ps: I did google, but couldn't find what I needed.

---

### Post by ryanhaigh on 2008-04-27
If you are using windows on other machines on the local network use samba for that.

For access from anywhere you will need to either have and remember your static ip address that you get from your isp or use something like dyndns. Once you have that setup you may need to do port forwarding if you are behind a router. The protocol that I would use would be ssh as it is secure and common, you can use winscp for accessing your files and putty for controlling your computer.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) 
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

