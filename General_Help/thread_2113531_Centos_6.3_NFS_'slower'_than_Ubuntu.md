---
title: "Centos 6.3 NFS 'slower' than Ubuntu"
date: 2013-02-07
forum: General Help
---

### Post by sdpagent on 2013-02-07
I tried using centOS 6 instead of ubuntu for my nfs media server (Tired of the server stating that it wants to reboot due to automatic security updates every other day). I believe I had set it up the same with the same /etc/exports file and same drive being shared, but noticed that it was noticeably 'slower' than when it was a Ubuntu machine. 
 - Much slower to be mounted
 - would 'time out'
 - generally slower to access/brose the folders.

I am not referring to file transfers themselves.

I thought perhaps I was just being 'nutty' and just installed ubuntu back on the machine again and it is much smoother again (Very noticeable). Has anyone noticed this or have any ideas what is causing this? I am sharing a 3TB drive which has about 2.5TB of media on the folder being shared.

---

### Post by SeijiSensei on 2013-02-07
Let's see /etc/exports on the server.  Try using async in the options list.

---

