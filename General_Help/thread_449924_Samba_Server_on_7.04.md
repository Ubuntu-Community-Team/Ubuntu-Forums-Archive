---
title: "Samba Server on 7.04"
date: 2007-05-20
forum: General Help
---

### Post by CarlosinFL on 2007-05-20
I want to make a basic simple Windows share on a box running 7.04. I installed only 2 files:

- samba
- samba-common

I then went to the /etc/samba/smb.conf file and it has a mess of information in there. I was told that 95% of the info or text in that .conf file can be removed however I just renamed the .conf file as smb.conf.orig and then used vi to create a new blank smb.conf. My questions now is what basic info needs to go into my smb.conf so that I can share one simple folder on my home LAN between a Windows XP machine and a Ubuntu 7.04 machine.

They're both on the same subnet and they are both in DNS so they can all address each other by their host name.

Is there a basic example someone can give me?

I do have a shell account on the Ubuntu box however I don't know if I need to add myself as a samba user as well of if the shell account is all I need...

Do I also need to :

```
# smbpasswd -a carlwill
```

Thanks for any info!

---

### Post by jtraub on 2007-05-20
[Examples]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service")

---

