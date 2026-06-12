---
title: "Help installing kloxo panel??"
date: 2013-06-14
forum: General Help
---

### Post by caleb12134 on 2013-06-14
Hey guys :D :D! When i try to install kloxo panel it  just gives me stuff like this.

caleb1@ubuntu:~$ wget [http://download.lxlabs.com/download/kloxo/production/kloxo-install-master.sh](http://download.lxlabs.com/download/kloxo/production/kloxo-install-master.sh)
--2013-06-14 08:47:00--  [http://download.lxlabs.com/download/kloxo/production/kloxo-install-master.sh](http://download.lxlabs.com/download/kloxo/production/kloxo-install-master.sh)
Resolving download.lxlabs.com (download.lxlabs.com)... 66.197.145.24
Connecting to download.lxlabs.com (download.lxlabs.com)|66.197.145.24|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-06-14 08:47:05 ERROR 404: Not Found.


caleb1@ubuntu:~$ su - root
Password: 
su: Authentication failure
caleb1@ubuntu:~$ sudo -i
[sudo] password for caleb1: 
root@ubuntu:~# wget [http://download.lxcenter.org/download/kloxo/production/kloxo-installer.sh](http://download.lxcenter.org/download/kloxo/production/kloxo-installer.sh)
--2013-06-14 08:47:49--  [http://download.lxcenter.org/download/kloxo/production/kloxo-installer.sh](http://download.lxcenter.org/download/kloxo/production/kloxo-installer.sh)
Resolving download.lxcenter.org (download.lxcenter.org)... 66.197.145.24
Connecting to download.lxcenter.org (download.lxcenter.org)|66.197.145.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6234 (6.1K) [application/octet-stream]
Saving to: `kloxo-installer.sh.1'


100%[======================================>] 6,234       --.-K/s   in 0.03s   


2013-06-14 08:47:49 (225 KB/s) - `kloxo-installer.sh.1' saved [6234/6234]


root@ubuntu:~# ./kloxo-installer.sh.1
-bash: ./kloxo-installer.sh.1: Permission denied
root@ubuntu:~# chmod 777 /kloxo-installer.sh.1
chmod: cannot access `/kloxo-installer.sh.1': No such file or directory
root@ubuntu:~# '/home/caleb1/Desktop/kloxo-installer.sh' 
/home/caleb1/Desktop/kloxo-installer.sh: 26: [: 0: unexpected operator
/home/caleb1/Desktop/kloxo-installer.sh: 55: [: ==: unexpected operator
/home/caleb1/Desktop/kloxo-installer.sh: 82: /home/caleb1/Desktop/kloxo-installer.sh: function: not found
/home/caleb1/Desktop/kloxo-installer.sh: 83: local: not in a function
root@ubuntu:~#  sh ./kloxo-installer.sh --type=master
./kloxo-installer.sh: 26: [: 1: unexpected operator
./kloxo-installer.sh: 55: [: master: unexpected operator
./kloxo-installer.sh: 82: ./kloxo-installer.sh: function: not found
./kloxo-installer.sh: 83: local: not in a function
root@ubuntu:~# sh ./kloxo-installer.sh --type=master
./kloxo-installer.sh: 26: [: 1: unexpected operator
./kloxo-installer.sh: 55: [: master: unexpected operator
./kloxo-installer.sh: 82: ./kloxo-installer.sh: function: not found
./kloxo-installer.sh: 83: local: not in a function
root@ubuntu:~# sh ./kloxo-installer.sh
./kloxo-installer.sh: 26: [: 0: unexpected operator
./kloxo-installer.sh: 55: [: ==: unexpected operator
./kloxo-installer.sh: 82: ./kloxo-installer.sh: function: not found
./kloxo-installer.sh: 83: local: not in a function
root@ubuntu:~#  sh ./kloxo-installer.sh --type=<master/slave> --db-rootpassword=PASSWORD
-bash: master/slave: No such file or directory
root@ubuntu:~#  sh ./kloxo-installer.sh --type=<master> --db-rootpassword=PASSWORD
-bash: master: No such file or directory
root@ubuntu:~#

---

### Post by zombifier25 on 2013-06-14
The downloaded file is kloxo-installer.sh.1, but you're trying to run kloxo-installer.sh.
That;s all I got. Try again and post the results.

---

