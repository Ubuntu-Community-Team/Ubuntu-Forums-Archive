---
title: "Root user creates files as other user"
date: 2012-10-21
forum: General Help
---

### Post by kwinsw on 2012-10-21
Hi,

I have two Ubuntu 12.04 systems, one Desktop one Server, in an otherwise Windows-only home network. I'm using them to teach myself Ubuntu Linux so that we can give the kids Ubuntu machines in their rooms in a year or so - along with an Ubuntu file and print server for the whole family. 

I explain this, only because it hopefully makes clear why I have a slightly odd file-sharing setup, it's so I can learn as much as possible, and why I'm posting about servers in the beginner's forum: because I'm a relative beginner and I'm stumped. 

Anyway.... On the server I have several shared folders. These are shared with the Windows machines using Samba and with the Ubuntu Dekstop using NFS.

I've noticed that any files created by the root user on the server, when copied to shared folders, show up on the desktop as having been created by one of the normal user accounts on the server. Look at the same file on the server or one one of the Windows machines and the permissions appear to show, correctly, that the owner is the root user on the server.

I don't even know where to start troubleshooting this. I've checked the force-user settings in Samba, and they bear no relation to what's happening. The user who appears as the owner in the NFS shares isn't named in any of the force-user settings.

If anyone can give me a clue as to what might be happening so that I have something to go on (and Google on) it would be much appreciated.

Thanks

kwinsw

ps. this came to light when I was backing up sshd_config configuration files for server and desktop, copying them to a share in preparation for writing them to a CD. That's why I'm copying root-owned files out to a shared location.

---

