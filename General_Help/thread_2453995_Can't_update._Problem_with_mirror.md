---
title: "Can't update. Problem with mirror?"
date: 2020-11-20
forum: General Help
---

### Post by freedombacon on 2020-11-20
I haven't been able to update Ubuntu for a few weeks. There was some problems with my ISP, but they fixed it. I thought this had something to do with IPv6 so I disabled it. What the heck is going on here?

```
user@hostname:/etc$ sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1    
net.ipv6.conf.all.disable_ipv6 = 1
user@hostname:/etc$ sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6 = 1
user@hostname:/etc$ sudo sysctl -w net.ipv6.conf.lo.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6 = 1
user@hostname:/etc$ sudo apt-get -o Acquire::ForceIPv4=true update
Err:1 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu focal InRelease                                              
  Could not connect to ppa.launchpad.net:80 (91.189.95.83), connection timed out
Err:2 http://archive.ubuntu.com/ubuntu focal InRelease                                                                         
  Could not connect to archive.ubuntu.com:80 (91.189.88.142), connection timed out Could not connect to archive.ubuntu.com:80 (91.189.88.152), connection timed out
Err:3 http://security.ubuntu.com/ubuntu focal-security InRelease                                                               
  Could not connect to security.ubuntu.com:80 (91.189.91.38), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.142), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.152), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.39), connection timed out
Err:4 http://us.archive.ubuntu.com/ubuntu focal InRelease                                               
  Could not connect to kazooie.canonical.com:80 (91.189.91.39), connection timed out Could not connect to banjo.canonical.com:80 (91.189.91.38), connection timed out Unable to connect to us.archive.ubuntu.com:http:
Err:5 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease
  Unable to connect to us.archive.ubuntu.com:http:
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal/InRelease  Could not connect to archive.ubuntu.com:80 (91.189.88.142), connection timed out Could not connect to archive.ubuntu.com:80 (91.189.88.152), connection timed out
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/focal/InRelease  Could not connect to kazooie.canonical.com:80 (91.189.91.39), connection timed out Could not connect to banjo.canonical.com:80 (91.189.91.38), connection timed out Unable to connect to us.archive.ubuntu.com:http:
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease  Unable to connect to us.archive.ubuntu.com:http:
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease  Could not connect to security.ubuntu.com:80 (91.189.91.38), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.142), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.152), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.39), connection timed out
W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/focal/InRelease  Could not connect to ppa.launchpad.net:80 (91.189.95.83), connection timed out
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by CelticWarrior on 2020-11-20
Are you using a VPN?

---

### Post by freedombacon on 2020-11-20
No VPN.

---

### Post by freedombacon on 2020-11-22
It turns out the problem was VPN related. traceroute and the VPN's test page didn't show it in use, so it took me awhile to figure out only apt used it. The solution was to have that VPN client not pull routes from the server.

---

### Post by ActionParsnip on 2020-11-22
Please mark as solved if the issue is resolved or provide additional information

---

