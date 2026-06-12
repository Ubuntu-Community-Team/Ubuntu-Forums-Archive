---
title: "correct permission setting for magento install"
date: 2017-12-16
forum: General Help
---

### Post by tonysar on 2017-12-16
Hello. 
Took me while to get up and running , had to learn all this server things in 2 days .so stick with me . I need to install magento 2 , im running vps ubuntu server with apache2. so far everything now working correctly . in order to setup magento correctly , i had to create a supper user and added user to www-data apache group. took ownership of files and www-data is file folder group. 
one thing that i noticed, is that www-data group dose not have permission to write to files , own has read write execute . group only has read execute. this seems to me will cause problems with magento install at one point  specially when writing to and creating .htaccess. 
I like to know which group should i add www-data to so this group can also write to the files ?
Thanks

---

