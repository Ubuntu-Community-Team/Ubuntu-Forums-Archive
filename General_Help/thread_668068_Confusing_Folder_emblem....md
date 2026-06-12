---
title: "Confusing Folder emblem..."
date: 2008-01-15
forum: General Help
---

### Post by rajames429 on 2008-01-15
I have two identical laptops running Gutsy 7.10 

I had previously installed the Intel Compilers for C++ and Fortran v 9.1.xxx. 

I recent,y installed the Intel Compilers for C++ and Fortran v 10.1.008. They reside in /opt/intel/cc and /opt/intel/fc, respectively. 

Everytihng runs fine. 

One thing seems wrong, however. When I browse to the /opt/intel/cc directory I see two folders: 
/opt/intel/cc/9.1.047 and /opt/intel/cc/10.1.008 (on both laptops). 

However, on ONLY ONE of the laptops, the 10.1.008 folder has a lock emblem on it. None of the sub-folders has a lock emblem on them. 

I have chowned the folder with 'sudo chown 775 -R /opt/intel' on both machines. 
I have chowned the folder with 'sudo chown 775 -R /opt/intel/cc' on both machines. 
I have chowned the folder with 'sudo chown 775 -R /opt/intel/cc/10.1.008' on both machines. 

I have open nautilus with 'sudo nautilus' and verified that the permissions seem the same. 

I have checked that my User and Groups are the same on both laptops. (ie. My username is a member of the root group). 

The lock emblem remains. 

Does anyone know why this emblem is on this folder? Can you help me fix this?

---

### Post by rajames429 on 2008-01-15
Well, I guess I should have tried restarting X with Ctrl+Alt+Backspace before I posted this question. 

Restarting X solved my problem. The lock emblem is gone. Thanks for the help, anyway.

---

