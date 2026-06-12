---
title: "Can't install additional drivers"
date: 2017-09-03
forum: General Help
---

### Post by nigro.orlando on 2017-09-03
Hi!
I just installed ubuntu 17.04 and I'm having some issues:
 
- First when i go to additional drivers and choose the proprietary one, nothing happens. It gets me back to the nouveau one.

- Then, when I tried to install vlc I got this message: 

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-plugin-base (= 2.2.4-14ubuntu2.2) but it is not going to be installed
       Depends: vlc-plugin-qt (= 2.2.4-14ubuntu2.2) but it is not going to be installed
       Depends: vlc-plugin-video-output (= 2.2.4-14ubuntu2.2) but it is not going to be installed
       Recommends: vlc-plugin-skins2 (= 2.2.4-14ubuntu2.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Thank you in advance for your help.

---

### Post by nigro.orlando on 2017-09-03
ok, it may depend on the access to repositories. If do apt-get update I get this:


```
Err:1 http://se.archive.ubuntu.com/ubuntu zesty InRelease
  Could not resolve 'se.archive.ubuntu.com'
Err:2 http://se.archive.ubuntu.com/ubuntu zesty-updates InRelease
  Could not resolve 'se.archive.ubuntu.com'
Err:3 http://se.archive.ubuntu.com/ubuntu zesty-backports InRelease
  Could not resolve 'se.archive.ubuntu.com'
Get:4 http://security.ubuntu.com/ubuntu zesty-security InRelease [89,2 kB]
Fetched 89,2 kB in 0s (404 kB/s)                      
Reading package lists... Done
W: Failed to fetch http://se.archive.ubuntu.com/ubuntu/dists/zesty/InRelease  Could not resolve 'se.archive.ubuntu.com'
W: Failed to fetch http://se.archive.ubuntu.com/ubuntu/dists/zesty-updates/InRelease  Could not resolve 'se.archive.ubuntu.com'
W: Failed to fetch http://se.archive.ubuntu.com/ubuntu/dists/zesty-backports/InRelease  Could not resolve 'se.archive.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by nigro.orlando on 2017-09-03
Ok, no real issue here, sorry for the unnecessary post, It was a somehow a matter of connectivity. 

It took a couple of hour for establish a connection with the servers, maybe due to the recent installation of the system

---

