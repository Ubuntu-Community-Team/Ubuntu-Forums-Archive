---
title: "command ls -al stuck ?!"
date: 2007-08-23
forum: General Help
---

### Post by glupi on 2007-08-23
Hi all,

I have very strange problem. I am connected to my ubuntu feisty server via ssh.
when i execute 'ls' or 'cd' comamnd everything works.
When I try 'ls -al' or 'top' or 'ps -ef' i receive one or 2 lines output and just blinking cursor. No prompt any more. And nothing works any more. Cntrl-C does not help. but the strange thing is that the web server is working and the web page is ok.

test@gsncli:~$ cd /
test@gsncli:/$ ls
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
test@gsncli:/$ ls -al
total 84
drwxr-xr-x 21 root   root    4096 2007-06-26 14:28 .
[COLOR="Red"]end here i receive the blikning cursor and thats it :([/COLOR]

Many other comamnds does not work - vi,more,env.. etc.

Please help!

---

### Post by glupi on 2007-08-23
It is me again.

The problem was in our IP network. New equipment limiting the packet size to 1024B :mad:

Thanks

---

