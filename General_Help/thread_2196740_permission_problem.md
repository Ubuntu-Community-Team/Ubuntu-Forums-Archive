---
title: "permission problem"
date: 2013-12-31
forum: General Help
---

### Post by myron2 on 2013-12-31
Hi there 

i have bit issues here, but samba installation is successfull i can create user and authonticate but the problem is after mapping the folder and test to create a folder it says "you dont have permission" is there any missing in my conf? but i tried to change permission directly to the share folder >> chmod -R 777 it works.im bit confuse, is there anyway in samba conf to chage the permission without using chmod -r 777 ?


[test_folder]
        comments =  test folder
        writeable = yes
        path = /home/test_folder
        valid users = chucknorris
        browseable = yes
        public = no
        read only = no

any help?

---

### Post by oldos2er on 2013-12-31
Moved to General Help.

---

