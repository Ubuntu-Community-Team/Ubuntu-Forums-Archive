---
title: "Dropbox wants sto install, but stalls"
date: 2014-02-12
forum: General Help
---

### Post by cecilieaux on 2014-02-12
I tried to install cloud application Dropbox from the .deb on the web but Ubuntu 12.04 LTS told me I already had a newer version. so then I try to start dropbox from the Unity dash and it eventually starts up but it wants to download and install dropbox. It downloads, it unpacks, then it stall saying there's a dependency missing: nautilus-dropbox. But the Software Centre says I have it.

Aaargh!

Help ... :(

Thanks in advance

Cecilieaux

---

### Post by cecilieaux on 2014-02-14
Eureka! Found the solution. Don't pay attention to any of the solutions out there. For 12.04 LTS

1. Open Synaptic Package Manager (if you don't have it, download it, well worth it and miles above the "software center").

2. Type "dropbox" in the quick filter. If you see a dropbox 1.60 or 1.61 mark it for complete removal. Then apply the change.

3. Assuming 2, or no dropbox, look for nautilus-dropbox 0.7.1 and install that.

4. A box will appear telling you to Start Drop box, do so by clicking Start, then Next.

5. The box will now ask you to retart Nautilus,  do so by clicking Restart.

6. File folders on the desktop will disappear.

7. Wait a bit. After a prudential time, log off.

8. Log back on, it should be working.

---

