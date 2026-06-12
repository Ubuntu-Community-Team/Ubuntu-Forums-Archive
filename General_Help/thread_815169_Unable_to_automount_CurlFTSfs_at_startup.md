---
title: "Unable to automount CurlFTSfs at startup"
date: 2008-06-01
forum: General Help
---

### Post by jesus gumbau on 2008-06-01
Hello, 
 
I am unable to auto mount a FTP directory using CurlFTPfs introducing the following line in fstab: 
 
curlftpfs#myuser:mypass@192.168.0.1/../../../mnt/disco_externo /mnt/disco fuse auto,allow_other,rw,user,uid=1000 0 0 
 
However, when doing it manually (executing mount /mnt/disco) it works like a charm! 
 
What's wrong with that?

---

