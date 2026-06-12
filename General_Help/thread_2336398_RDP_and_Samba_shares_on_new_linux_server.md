---
title: "RDP and Samba shares on new linux server"
date: 2016-09-07
forum: General Help
---

### Post by gantww on 2016-09-07
Greetings,
I recently set up a new linux server for file storage (mostly, but I intend to tinker with docker, postgres, dotnetcore, and several other things as soon as possible).

1) Remote desktop from my windows machine to my ubuntu machine. I've enabled remote access on my ubuntu box, but windows won't connect with the credentials on the ubuntu account. I could have sworn I had made an RDP connection from windows in the past though - am I missing something simple? Or is my memory just wrong?
2) I've also set up samba (with the defaults) and shared a directory under my user directory. I can see it in the available shares, but it won't take my login.

I wouldn't normally pack two questions together, but I suspect they both have real simple answers (that I'm missing because I'm rusty), or even the same answer (given that both should theoretically be using the ubuntu login, right?). Any suggestions on where to start? Gut feeling says this is something dumb and something that is linked. Is the ubuntu account the one I should be trying to use for these connections?

---

### Post by TheFu on 2016-09-08
Can't tell from what you've written.

The best, most secure, remote desktop for Ubuntu is **x2go**. It feels 2-3x faster than VNC, another alternative.  RDP is a Windows protocol, as far as I know. Never used any Linux implementations.  Setup **ssh** first and get that working from the client to the server. Then follow the x2go install instructions at their website. They will have you add a PPA to the Ubuntu/Mint/Debian Linux systems.  The only trick on Windows (as the client) is to get the full font package in addition to the normal client install, then tweak the performance settings for bandwidth and image compression to be lower that you really have.  I use the 4Kb pages and only claim ISDN bandwidth for WAN connections. Inside my network, everything is wired GigE, so the defaults work fine.

I've never mounted shares **under** any user-home.  Best to either mount the [homes] using that feature of samba or mount storage outside /home/ to avoid permission issues.  The only real trick to samba is to seed the user-accounts in the smbpasswd file .... use the **smbpasswd** command for that.  All the samba settings are in /etc/smb/smb.conf ... I've **never** used any GUI to configure samba or the shares. I've seen a few how-to guides which do setup samba with only GUIs, but never used any.

---

