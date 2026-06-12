---
title: "chmod - num lock - script problems"
date: 2004-11-30
forum: General Help
---

### Post by hasan on 2004-11-30
I have a folder on my desktop with  chmod set to: drwxr-xr-x (755) - how do i delete it?

On the keyboard i use the Num Lock "numbers alot" Ubuntu is always disabling this - how could i enable Num Lock permenantley?

Many thanks,

---

### Post by jiyuu0 on 2004-11-30
1) it could be because the folder it owned by somebody else
$ chown -R ur_user:ur_group directory_name

2) set num lock on when login to gnome
[http://kitech.com.my/ubuntu/4.10/#onnumlockgnome](http://kitech.com.my/ubuntu/4.10/#onnumlockgnome)

---

### Post by adbak on 2004-11-30
For your numlock problem....

apt-get install numlockx

It's in universe.

---

### Post by hasan on 2004-11-30
***$ chown -R ur_user:ur_group directory_name***

well i accidentally created the folder.. so how do i delete it? there is one user and thats me in the system + root

---

### Post by jiyuu0 on 2004-12-01
since you are going to delete it

$ sudo rm -fr location_of_the_folder
*becareful where you delete

---

