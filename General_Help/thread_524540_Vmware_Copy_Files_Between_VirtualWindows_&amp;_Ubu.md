---
title: "Vmware: Copy Files Between VirtualWindows &amp; Ubuntu or even other NTFS Drives??"
date: 2007-08-13
forum: General Help
---

### Post by OzzyFrank on 2007-08-13
I've seen it asked before, but no one is answering. I assume people who use Vmware are primarily running Windows in it, so how do you copy/share between Windows/Vmware and Ubuntu? So far I've had to burn data discs, hehehe. There has to be a simpler way, non? And hopefully not some complicated and confusing network solution. Wouldn't be so bad if the Fake Windows recognised the real Windows drive, or even just the other NTFS partition I have on my Ubuntu drive.

Actually, maybe I should be asking how to get the virtual Windows to recognise more than just itself, the floppy and DVD drives? If it could just see the other NTFS drives, that would be just fine.

---

### Post by ukripper on 2007-08-13
Not sure about vmware but in virtualbox I use samba configured for network sharing and share files with other machines if i need to transfer something from within VM i transfer to other machine and then back to my host ubuntu/XP machine under ubuntu. as it is using same IP it would be difficult to share it on same machine

---

### Post by OoooMatron on 2007-08-13
you can use shared folders in vmware or you can you use samba and then going to run and //ipaddress in the box while in XP.
if you enable shared folders in the client program (vmware) you can browse your XP network neighbour hood and access them there.

I use the samba method.

---

