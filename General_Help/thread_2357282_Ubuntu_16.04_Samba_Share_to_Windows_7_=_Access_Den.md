---
title: "Ubuntu 16.04 Samba Share to Windows 7 = Access Denied"
date: 2017-03-31
forum: General Help
---

### Post by Rumpkie on 2017-03-31
Ubuntu 16.04 Samba Share to windows 7
I know this question has been asked to death on the internet and I have read probably a dozen posts about it, I still haven’t found a working solution:
I am getting a Windows 7 access Denied and windows repromts me for my password when I try to log into a samba share on Ubuntu 16.04.02.
I was concerned that our network policies on my domain workstation may be preventing access so I tried an out of the box windows 7 vm and had the same results.
This works as expected from my Mac.
I have added the following lines to my smb.conf for windows compatibility

And according to the smb log files its authenticating fine or at least the same way my mac does. Any ideas?

[global]
ntlm auth = no
lanman auth = no
client ntlmv2 auth = yes


[jazz]
        path = /pong/sparta/XXXX/jazz
        comment = Flux Data Directory
        guest ok = no
        valid users = @smbaccess
        writable = yes
        browsable = yes

---

### Post by Elkenfugel on 2017-04-01
> **Rumpkie said:**
> 
I am getting a Windows 7 access Denied and windows re-prompts me for my password when I try to log into a samba share on Ubuntu 16.04.02.



How exactly are you attemping to login to the share from Windows? Are you in Backup & Restore, or Windows Explorer, or are you trying to add a network drive?

---

### Post by Rumpkie on 2017-04-02
I am selecting the address bar in explorer and typing in \\the.fqdn.of.my.server\share_name
The name I am entering is the .\theusername which the domain information gets stripped off by samba according to the log.

Then it says access denied and prompts me again.
The samba log shows it authenticating correctly. I just don't know why windows doesn't think that it does.

On my mac I use finder's Connect to Server under the Go menu (actually I use command K) then type in smb://the.fqdn.of.my.server/share_name and it prompts me, and it works.

---

