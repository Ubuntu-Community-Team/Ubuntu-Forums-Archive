---
title: "Samba File sharing a My Book - cannot edit files"
date: 2018-07-07
forum: General Help
---

### Post by robert71 on 2018-07-07
Hi guys ,  
 Im having some trouble editing a share i created. i cannot edit any files / folders from my windows machine or from 
Linux box to which My Book is directly connected 
 
Please help here is my smb.conf: ( normal / default + my entry below) 
   
[pi]    
path=/media/pi/My Book    
only guest = no    
browseable = yes    
writeable = yes    
create mask = 0777    
director mask = 0777 
   
public = no  then i used sudo smdpasswd pi 

connected too the share from windows using credentials  
u: pi 
P: xxxx 
 
cannot edit files locally or through share plz 


kind regards

---

