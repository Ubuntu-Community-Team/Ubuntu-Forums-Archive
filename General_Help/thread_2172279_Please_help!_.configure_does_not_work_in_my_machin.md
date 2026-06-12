---
title: "Please help! ./configure does not work in my machine."
date: 2013-09-04
forum: General Help
---

### Post by georgedao123 on 2013-09-04
I am using Ubuntu 13.04. Today I got a .TAR.GZ package. I extracted it using tar -xvf fileName.tar.gz

The archive is extracted. However, I could not install it with ./configure after navigating to the folder with cd. It said: No such file or folder.

Please help me out. Thank you so much for your help.

---

### Post by albandy on 2013-09-04
Usually you have to do:

./configure
make 
sudo make install

But if you post a link to the application I can try to compile and install it to know what is happening.

---

### Post by CatKiller on 2013-09-04
./configure means to run the script called, "configure," that's in the current directory. You don't necessarily have a script called configure in that directory. Certainly there's no reason to assume that every tarball should contain one.

---

### Post by Impavidus on 2013-09-04
Usually you have to look for a file called readme or install. That will give you more detailed instructions. Not every package can be installed in the same way.

---

