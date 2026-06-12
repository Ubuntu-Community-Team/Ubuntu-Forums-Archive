---
title: "Connecting to an Ubuntu drive on a windows machine using samba"
date: 2016-08-06
forum: General Help
---

### Post by Jeffa on 2016-08-06
Hello community. 

I recently did a fresh install on a file server running ubuntu for the upgrade to 16.04. I'm having some trouble connecting to the drive on the server from my windows machine (running windows 7). The smb.conf file lists the correct workgroup. I've also added the following to the end of the smb.conf file. 


path = /media/user/Storage2
browsable = yes
guest ok = yes 
read only = no
create mask = 0755

Other than that, I haven't made many other changes to the smb.conf file. I've followed multilple how-to's for configuring samba, but still haven't been able to connect. I've also created a samba user and created a password. But every time I try and map the drive from the windows machine, it fails. Any ideas as to what I could try next? 

Thanks community!

---

