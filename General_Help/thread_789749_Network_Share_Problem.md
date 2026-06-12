---
title: "Network Share Problem"
date: 2008-05-10
forum: General Help
---

### Post by xxrealmsxx on 2008-05-10
I have tried several ways to get my network share working on my Xubuntu installation but its not working.

My latest attempt was to use pyneighborhood to get the network shares mounted.

When I run pyneighborhood as a regular user it will not mount the folder and claims that I need log in information (the server is set to anonymous).

When I use sudo everything works fine and I can copy files over and write to the network share, however if I try to copy some of my folders it gives me a permission error. 

The strange this is that all of the permissions are the same on every folder on my server.

The terminal output when I do all this is as follows:

jamie@jamie-laptop:~$ sudo pyNeighborhood
Current name: SERVER
Dictionary: {'ip': u'192.168.1.128', 'display': u'SERVER', 'netbios': u'SERVER'}
Scanning host at first
Trying to start the pulse thread
Starting the pulse thread
192.168.1.128
Scanning share 192.168.1.128 anonymously
smbclient -N -L 192.168.1.128
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]
success
Quitting the pulse thread
Stopped the pulse thread succesfully
IP:  192.168.1.128
192.168.1.128
Input mount point:  /home/jamie/SERVER/share
Setting mount command to SMB
smbmount //192.168.1.128/share /home/jamie/SERVER/share -o guest
Mounting //192.168.1.128/share ...
Warning: mapping 'guest' to 'guest,sec=none'
Mounted successfully!
Mount point:  
Mount directory:  /home/jamie
No such mountpoint

I would appreciate any help I can get, i'm quite happy with Xubuntu except for this minor headache.

---

### Post by xxrealmsxx on 2008-05-10
I went ahead and did Chmod 777 on the entire folder and its subfolders and now everything works.

---

