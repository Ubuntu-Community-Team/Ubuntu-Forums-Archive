---
title: "sudo-apt-get update error - : Read error - read (5: Input/output error)"
date: 2017-11-30
forum: General Help
---

### Post by scollar on 2017-11-30
Hello Forum looking for help with this.

Sudo apt-get update returns:
```
sean@sean-Satellite-L645D:~$ sudo apt-get update
[sudo] password for sean:     
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu xenial-security InRelease                       
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease                              
Hit:4 http://packages.elementary.io/appcenter xenial InRelease                          
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                              
Hit:6 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease                      
Ign:7 http://ppa.launchpad.net/wii.sceners.linux/wiithon-1.1/ubuntu karmic InRelease
Hit:8 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease     
Hit:9 http://ppa.launchpad.net/elementary-os/stable/ubuntu xenial InRelease  
Hit:10 http://ppa.launchpad.net/elementary-os/os-patches/ubuntu xenial InRelease
Hit:12 http://ppa.launchpad.net/plexapp/plexht/ubuntu xenial InRelease        
Hit:13 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease         
Hit:14 http://ppa.launchpad.net/wii.sceners.linux/wiithon-1.1/ubuntu karmic Release
Reading package lists... Error!                     
W: http://ppa.launchpad.net/wii.sceners.linux/wiithon-1.1/ubuntu/dists/karmic/Release.gpg: Signature by key 39BEE4BBB63E15E56314B93428577FE31F882273 uses weak digest algorithm (SHA1)
E: Read error - read (5: Input/output error)
W: You may want to run apt-get update to correct these problems
E: The package cache file is corrupted
sean@sean-Satellite-L645D:~$
``` 

Any help to help me understand and fix this greatly apreciated

---

### Post by jaweewo on 2017-11-30
I think Your lists are corrupted, you should remove them and refresh your package lists:
 sudo rm -r /var/lib/apt/lists/
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update

Hope it helps  ^^

---

### Post by scollar on 2017-11-30
Same results ..... Any other ideas?

---

### Post by Impavidus on 2017-11-30
That wii.sceners.linux/wiithon-1.1 PPA hasn't been updated for 383 weeks. It seems to be made for Ubuntu 9.10. Maybe better to get rid of that. Whether that's the cause of your problem? I don't know. It may be deeper. Better run a filesystem check and a health check for your hard drive.

---

### Post by Yellow Pasque on 2017-11-30
Yeah, get rid of any line mentioning the ancient PPA, clean the cache, and try again

```
sudo apt-get clean
sudo apt-get update
```

---

