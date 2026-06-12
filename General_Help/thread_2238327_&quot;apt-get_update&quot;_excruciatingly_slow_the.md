---
title: "&quot;apt-get update&quot; excruciatingly slow then doesn't work"
date: 2014-08-07
forum: General Help
---

### Post by JazzPotato on 2014-08-07
Hi there,
Recently, around about since 14.04.1 came out, my apt-get update has not been very compliant when trying to update my repos.
When I issue the command, the process hangs on :
```
 0% [Connecting to 128.199.248.144 (128.199.248.144)]
```
for a while, and then takes an incredibly long time to do it's thing. However, when it finally finishes, it complains with things like:

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Unable to connect to 128.199.248.144:80:


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Unable to connect to 128.199.248.144:80:


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Unable to connect to 128.199.248.144:80:


W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Here is what my terminal emulator looks like when the command has finished:

```

Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://extras.ubuntu.com trusty InRelease 
Err http://archive.ubuntu.com trusty-updates InRelease                         
  
Err http://archive.ubuntu.com trusty-backports InRelease                       
  
Err http://archive.ubuntu.com trusty-security InRelease                        
  
Err http://archive.ubuntu.com trusty Release.gpg                               
  Unable to connect to 128.199.248.144:80:
Err http://archive.ubuntu.com trusty-updates Release.gpg
  Unable to connect to 128.199.248.144:80:
Err http://archive.ubuntu.com trusty-backports Release.gpg
  Unable to connect to 128.199.248.144:80:
Err http://archive.ubuntu.com trusty-security Release.gpg
  Unable to connect to 128.199.248.144:80:
Err http://extras.ubuntu.com trusty Release.gpg      
  Could not connect to 128.199.248.144:80 (128.199.248.144), connection timed out
Reading package lists... Done                        
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Unable to connect to 128.199.248.144:80:


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not connect to 128.199.248.144:80 (128.199.248.144), connection timed out


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Unable to connect to 128.199.248.144:80:


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Unable to connect to 128.199.248.144:80:


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Unable to connect to 128.199.248.144:80:


W: Some index files failed to download. They have been ignored, or old ones used instead.

```


This happens on the multiple LANs I have tried it from. My ubuntu server, which is behind the same switch, router and is in the same office, apt-get updates swiftly and perfectly. I sort of remember there being a dpkg command that refreshes apt-get's brain, but I need help here.
What could the problem be?

Thanks,
Gary

---

### Post by ian-weisser on 2014-08-07
> **JazzPotato said:**
> ```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Unable to connect to 128.199.248.144:80:
```

128.xxx.xxx.xxx is not the normal IP for archive.ubuntu.com

```
$ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.92.201) 56(84) bytes of data.
64 bytes from urayuli.canonical.com (91.189.92.201): icmp_seq=1 ttl=49 time=103 ms
```

Did you set up a proxy or otherwise muck with your networking?
Or does your LAN require a proxy that you are not using?
Or have you (or your LAN administrators) been experimenting with nameservers?

---

### Post by JazzPotato on 2014-08-07
I think it has something to do with me trying to use a proxy.
However, the proxy is not in use now.
I set the proxy through the gui, Network > Network Proxy
How do I fix it?

---

### Post by mJayk on 2014-08-07
> **JazzPotato said:**
> I think it has something to do with me trying to use a proxy.
However, the proxy is not in use now.
I set the proxy through the gui, Network > Network Proxy
How do I fix it?


We fixed this problem in the #ubuntu irc, turned out to be an extra DNS entry.

---

### Post by JazzPotato on 2014-08-07
Cheers mJark, you deserved that cookie! :-)

---

