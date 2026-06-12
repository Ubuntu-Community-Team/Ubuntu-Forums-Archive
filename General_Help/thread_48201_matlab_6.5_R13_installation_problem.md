---
title: "matlab 6.5 R13 installation problem"
date: 2005-07-11
forum: General Help
---

### Post by windmaple on 2005-07-11
I am trying to install matlab 6.5 on my lappy.I copied all the files in the disk into /home/windmaple/temp and then followed the instructions. But I came up with the following error.

root@ubuntu:/home/windmaple/temp #./install* &
[1] 8399
root@ubuntu:/home/windmaple/temp # 
/home/windmaple/temp/update/install/mapname.sh: line 1: TabGroup: command 
not found
cp: missing desination file
Try 'cp --help' for more infomation
./install :line 1251:.:/home/windmaple/temp/update/install/: is a directory

Is there anything I could do about that? 
Thanks a lot!

---

### Post by professor_chaos on 2005-07-11
I'm not sure about 6.5, but I recieved an error when attempting to execute the install like you are for matlab 7. 

instead of     ./install
try                 sh ./install

also, incase you weren't aware... you can install with root privaleges without logging in as root. To do this login as normal user and try...   sudo sh ./install

Hope you are sucessful!

---

