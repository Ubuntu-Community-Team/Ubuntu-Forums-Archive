---
title: "update error"
date: 2013-10-26
forum: General Help
---

### Post by chebbisana on 2013-10-26
I got these errors when trying to update! can you help me please

(P.S: i've got this error before: "the package lists or status file could not be parsed or opened" 
i've tried this code: 

[FONT=Ubuntu Mono][COLOR=#000000]sudo rm /var/lib/apt/lists/* -vf
[/COLOR][/FONT]sudo apt-get clean
sudo apt-get update

but i still get these errors with updating:



Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease)  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease)  


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease)  


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/InRelease](http://extras.ubuntu.com/ubuntu/dists/precise/InRelease)  


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Could not resolve 'security.ubuntu.com'


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not resolve 'extras.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by chebbisana on 2013-10-26
it seeems that i have a problem with internet connection (i've tried to ping google DNS but it doesn't work: "connect: Network is unreachable" ) how can i fix it?

---

### Post by Iowan on 2013-10-26
I presume the update isn't the only thing that doesn't work...
Did you ping google DNS by IP address?
Can you ping your router?
What is in your routing table (route -n)?

---

### Post by chebbisana on 2013-10-26
i've tried to ping google DNS with: ping -c3 8.8.8.8 

here is my routing table:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.10   0.0.0.0         UG    100     0        0 eth0
169.254.0.0    0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

i've tried:   ping -c3 192.168.1.10  
it posts up destination host unreachable ...

---

