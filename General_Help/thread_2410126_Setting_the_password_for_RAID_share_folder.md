---
title: "Setting the password for RAID share folder"
date: 2019-01-11
forum: General Help
---

### Post by Purple_Unicorn on 2019-01-11
Hello guys. I implemented a RAID1 system in my office. Im using that computer for file sharing on our local network.
All of the other computers have Windows installed. Is there any way to put a password on my /mnt/raid folder, so when Windows users want to enter it they have to type a password?

Sharing with permissions is working just fine, everything is working. I just want to limit the access, so I as admin have to type the password on the PCs to connect.

---

### Post by TheFu on 2019-01-11
Don't share it with users besides yourself. By "share" I assume you mean CIFS/Samba?

RAID has nothing to do with this question, BTW.

---

### Post by Purple_Unicorn on 2019-01-11
I way trying to describe my situation. I HAVE to share that folder because that folder is made of our shared files on our local network in my business area. Its the /mnt/raid mount that Im sharing. Only that folder is seen on the Windows network when they access the Linux PC. I want to put the password on it so as Admin I can manually choose which computers are going to access that shared folder.

Samba has already been activated. Thats why they can see the folder in the first place cause I entered my business workgroup with it.

---

