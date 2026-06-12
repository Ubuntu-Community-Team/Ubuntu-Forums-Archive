---
title: "Install Intel Math Kernel Library (mkl) on Kubuntu"
date: 2006-08-21
forum: General Help
---

### Post by wyxsdu on 2006-08-21
I try to install mkl8.1.1 on kubuntu6.0.6 by "sudo ./install.sh:, but failed.

Mr. Arai say it can be installed by nomoral user.

Just download mkl to you own directory. unzip it.

and ./install.sh 
(1)when it say "How would you prefer to proceed? (root/sudo/ignore) [ignore]:" just "Enter"
(2)select "1 install"
(3)then define the lic
(4) then select "2. Install the software without using RPM database (root password not required)."
(5)define your directory which you want to install mkl. Note: No install mkl on the root work directory. You need install it on your own. Such as "/home/tom/mkl/8" tom is your user name.
after install you need "sudo cp -r mkl/8 /opt/intel/."

Then any people in your computer can use it.

WANG Yuanxu

---

