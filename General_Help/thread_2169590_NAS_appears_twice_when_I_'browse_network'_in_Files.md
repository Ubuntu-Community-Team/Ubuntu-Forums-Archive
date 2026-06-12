---
title: "NAS appears twice when I 'browse network' in Files."
date: 2013-08-22
forum: General Help
---

### Post by stephencweston on 2013-08-22
Hi all,

I've recently installed a new NAS (a Netgear ReadyNAS 102) into my home network. Setup seemed to be quite smooth and all seems to work. I can access it both on my Windows 7 laptop and my Ubuntu 13.04 desktop machine.

The query I have is as to why the NAS seems appear twice when I 'browse network' in Files on the Ubuntu machine. One is called 'ReadyNAS102 (SMB)' and the other is 'READYNAS102' (picture attached). Both appear to work fine, although when I open the first one it calls itself 'Windows share on 'readynas102.local' and the other refers to itself as 'Windows share on readynas102'.

What is the different between the two and can I make one of them disappear (just as a matter of keeping things looking tidy). Just to clarify, in Windows the share only appears once.

Thanks in advance for any help in understanding this.

Stephen

[ATTACH=CONFIG]245596[/ATTACH]

---

### Post by steeldriver on 2013-08-22
It probably just means that you are exporting shares from your NAS using both the NFS (Unix native) and CIFS (aka SAMBA aka SMB) protocols - they may be the same shares, or different ones, depending how your NAS is configured. Because Windows only 'speaks' SMB you only see that one when you connect from a Windows client, whereas Linux clients can speak both protocols - so they display them as separate network 'locations'.

FWIW I also have a Netgear ReadyNAS (one of the old Sparc-based Duos) and by default *that* exports everything as NFS, SMB *and* AFP (the Apple file protocol) so it's possible you're seeing AFP as well as / instead of NFS export(s)

If it really bugs you, and you mostly use Windows clients then I guess you could turn off NFS and/or AFP on the NAS

---

### Post by stephencweston on 2013-08-22
Thanks steeldriver,

I had considered that and I had already switched all other services (apart from smb) off, including nfs and afp. This did actually remove a third reference to the NAS called 'ReadyNAS 102 (AFP)', but was still left with the ones mentioned in the previous post.

Still stumped. Although it does annoy me a little, I can live with it.

Stephen

---

### Post by stephencweston on 2013-08-22
UPDATE..

I had a play with turning the smb service on and off. Turning it off seemed to remove both references mentioned earlier to the NAS and switching it back on seemed to have restored only the one reference (the one called 'ReadyNAS 102 (SMB)'. So I guess I've solved my problem.

Thanks for your help.

Stephen

---

### Post by stephencweston on 2013-08-23
NEW UPDATE..

Restarted my computer today and both references to my NAS are present again. On further investigation I can access the NAS by typing into the 'run a command' (Alt-F2):
smb://READYNAS102
smb://ReadyNAS102.local

From that I gather that they are both samba (smb) shares and other share protocols being used by the NAS are not the issue.

Any further suggestion/help would be much appreciated.

Stephen

---

