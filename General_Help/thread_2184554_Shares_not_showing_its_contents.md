---
title: "Shares not showing its contents"
date: 2013-10-29
forum: General Help
---

### Post by JnPson on 2013-10-29
I'm using Ubuntu 13.10 after upgrading from 13.04. 

After upgrading I can't see the contents of some shared folders in my network. I have several servers, three Ubuntu 12.04.3 and one Windows Server 2003, which is acting as DFS server (Distributed File Server). 

One of my servers, has Samba 4.0.0alpha18 installed and the two others has Samba Version 4.0.10. 
If I browse my 4.0.0alpha18 server I only see the shared folders but not the content of it. If I browse the shared folders of my two other servers I can see the content of it. 
I have a similar problem with Windows 7. Windows 7 cannot access the Samba 4.0.0alpha18 server, but my XP machines can.

But before I upgraded my Ubuntu I could access and view all shares on that server. So, what happened?

---

### Post by smuggly on 2013-11-11
The silence on this one is amazing. They have screwed it up Again. Networking is a critical function. I can't browse my windows network @ ALL? in 13.10. Something has changed drastically. I could just install winbind edit nsswitch.conf. Before & Go. Now that no longer works. So I guess we will have to wait for someone to figure out a work around. Until then it's back to LTS.

---

