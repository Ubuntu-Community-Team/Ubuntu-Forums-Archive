---
title: "New to linux, can't get file sharing to work"
date: 2017-05-07
forum: General Help
---

### Post by vorbis1024 on 2017-05-07
Hi there, 
i've just installed ubuntu for the first time, seems good but at this point i can't connect to my NAS on my home network. Its very frustrating, i've followed a number of guides such as this one here 

[http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/)

but still no luck. the NAS is sharing over CIFS and NFS. no shares come up in the file explorer and after following the guide above i can see the CIFS share but upon clicking it i just get 'unable to access location' 'mount: only root can mount'
I've tried using the NAS's name and its static IP

any  help is greatly appreciated.

---

### Post by HermanAB on 2017-05-07
Howdy,

Network file systems can be frustrating to get to work.  The trick is to test from the bottom up and to use very simple test utilties that will answer a simple question such as: Does the network routing work?  Does the server respond?  Is the username and password correct? and so on.  

Obviously (or not so obviously if you look at the multitude of lamentations on these fora), if the underlying network has a configuration problem, then the upper protocols will not work at all and you are wasting your time debugging the wrong thing.

You can get some idea of where the problems are with the ping and telnet utilities:

Do you have a DNS or Hosts file setup, or do you use hard coded IP addresses?
$ sudo ping servername
$ sudo ping serveripaddress

Does the server respond on the SMB port 445?
$ telnet serveripaddress 445

If you can get this far, only then can you start to check the SMB protocol using the smbclient program.

Only if smbclient works, should you try to mount the share using a GUI, otherwise you are just wasting your time.

Hope that helps!

---

### Post by Morbius1 on 2017-05-07
You gotta love these independent samba HowTo's. The author goes through the whole nsswitch / winbind thing presumably so he can access the server by it's host name then accesses it by ip address:
```
 //192.168.1.5/share /media/Ji-share cifs credentials=/home/handbook/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0
```
The reason you got 'unable to access location' 'mount: only root can mount' is because the line in fstab didn't work. And your bookmark was created because the mount point is under /media ( not because it connected to the server ) which made it actionable but the line in fstab omits the options required for an ordinary user to mount it.

Anyhoo, When you ran **sudo mount -a** you should have seen an error message. What was it?

---

