---
title: "Update troubles"
date: 2008-02-11
forum: General Help
---

### Post by Random Numbers on 2008-02-11
I tried to install updates wit Update manager and got this:
[INDENT]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.51_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.51_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)[/INDENT]
Since I can get to this forum, I don't think my connection to the intertubes is bad.  Any idea what is wrong?

---

### Post by Ek0nomik on 2008-02-11
> **Random Numbers said:**
> I tried to install updates wit Update manager and got this:
[INDENT]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.51_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.51_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)[/INDENT]
Since I can get to this forum, I don't think my connection to the intertubes is bad.  Any idea what is wrong?

From what I can find, it looks like it may be related to anon-proxy.

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/185430](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/185430)

You can see if you have it installed by running this:

```
sudo aptitude search anon
```

---

### Post by Random Numbers on 2008-02-11
that's it!  Thanks

---

### Post by Mongo5000 on 2008-02-11
Same issue.

I tried the anon code above and this is what it gave me back

```
p   anon-proxy                      - Proxy to surf the web anonymously
```

So it looks like I do have it on a fresh install, I just don't know how to get rid of it.

Suggestions?

EDIT: Maybe not.  Just loaded Synaptic and it says anon-proxy isn't installed.

---

### Post by Mongo5000 on 2008-02-11
I just tried sudo apt-get update and this is what is doing

stephen@gutsy:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_CA           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_CA       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_CA     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release.gpg                             
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
99% [Connecting to ca.archive.ubuntu.com (129.97.134.71)]

Seems to just be timing out?

---

### Post by Mongo5000 on 2008-02-12
Seems to be fine now.  Guessing its just ca.archive.ubuntu.com:80 thats having issues.

---

### Post by Ek0nomik on 2008-02-13
> **Mongo5000 said:**
> Seems to be fine now.  Guessing its just ca.archive.ubuntu.com:80 thats having issues.

Indeed.  Sometimes a server has a hiccup.

Anyways, are you still have the same error as the original poster?

---

### Post by Mongo5000 on 2008-02-14
It seems much better now, but its hit and miss.  

No biggie for me really as long as I know it will come back :)

---

