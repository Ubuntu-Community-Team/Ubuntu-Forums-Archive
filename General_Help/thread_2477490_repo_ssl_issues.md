---
title: "repo ssl issues"
date: 2022-07-26
forum: General Help
---

### Post by bazzybtec on 2022-07-26
there seems to be an issue with the ubuntu repositories.

I have tested these urls in a browser and they don't work using https only http.

i have tested this on my work machines and local machines. can i confirm if others are experiencing this and are the devs aware of it?


```
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jammy InRelease
Ign:2 [https://security.ubuntu.com/ubuntu](https://security.ubuntu.com/ubuntu) jammy-security InRelease                                        
Ign:3 [https://security.ubuntu.com/ubuntu](https://security.ubuntu.com/ubuntu) jammy-backports InRelease                                       
Ign:4 [https://archive.ubuntu.com/ubuntu](https://archive.ubuntu.com/ubuntu) jammy InRelease  
Ign:5 [https://archive.ubuntu.com/ubuntu](https://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:2 [https://security.ubuntu.com/ubuntu](https://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:3 [https://security.ubuntu.com/ubuntu](https://security.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:4 [https://archive.ubuntu.com/ubuntu](https://archive.ubuntu.com/ubuntu) jammy InRelease
Ign:5 [https://archive.ubuntu.com/ubuntu](https://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:2 [https://security.ubuntu.com/ubuntu](https://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:3 [https://security.ubuntu.com/ubuntu](https://security.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:4 [https://archive.ubuntu.com/ubuntu](https://archive.ubuntu.com/ubuntu) jammy InRelease
Ign:5 [https://archive.ubuntu.com/ubuntu](https://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Err:2 [https://security.ubuntu.com/ubuntu](https://security.ubuntu.com/ubuntu) jammy-security InRelease
  Cannot initiate the connection to security.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Could not connect to security.ubuntu.com:443 (185.125.190.36). - connect (111: Connection refused) Could not connect to security.ubuntu.com:443 (91.189.91.39). - connect (111: Connection refused) Cannot initiate the connection to security.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to security.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable) Could not connect to security.ubuntu.com:443 (185.125.190.39). - connect (111: Connection refused) Could not connect to security.ubuntu.com:443 (91.189.91.38). - connect (111: Connection refused) Cannot initiate the connection to security.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable)
Err:3 [https://security.ubuntu.com/ubuntu](https://security.ubuntu.com/ubuntu) jammy-backports InRelease
  Cannot initiate the connection to security.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Cannot initiate the connection to security.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to security.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable) Cannot initiate the connection to security.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable)
Err:4 [https://archive.ubuntu.com/ubuntu](https://archive.ubuntu.com/ubuntu) jammy InRelease
  Could not connect to archive.ubuntu.com:443 (91.189.91.38). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (185.125.190.39). - connect (111: Connection refused) Could not connect to archive.ubuntu.com:443 (91.189.91.39). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (185.125.190.36). - connect (111: Connection refused)
Err:5 [https://archive.ubuntu.com/ubuntu](https://archive.ubuntu.com/ubuntu) jammy-updates InRelease
  Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable)
Reading package lists... Done
W: Failed to fetch [https://archive.ubuntu.com/ubuntu/dists/jammy/InRelease](https://archive.ubuntu.com/ubuntu/dists/jammy/InRelease)  Could not connect to archive.ubuntu.com:443 (91.189.91.38). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (185.125.190.39). - connect (111: Connection refused) Could not connect to archive.ubuntu.com:443 (91.189.91.39). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (185.125.190.36). - connect (111: Connection refused)
W: Failed to fetch [https://archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](https://archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease)  Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable)
W: Failed to fetch [https://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease](https://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease)  Cannot initiate the connection to security.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Could not connect to security.ubuntu.com:443 (185.125.190.36). - connect (111: Connection refused) Could not connect to security.ubuntu.com:443 (91.189.91.39). - connect (111: Connection refused) Cannot initiate the connection to security.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to security.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable) Could not connect to security.ubuntu.com:443 (185.125.190.39). - connect (111: Connection refused) Could not connect to security.ubuntu.com:443 (91.189.91.38). - connect (111: Connection refused) Cannot initiate the connection to security.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable)
W: Failed to fetch [https://security.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](https://security.ubuntu.com/ubuntu/dists/jammy-backports/InRelease)  Cannot initiate the connection to security.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Cannot initiate the connection to security.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to security.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable) Cannot initiate the connection to security.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable)
W: Some index files failed to download. They have been ignored, or old ones used instead.
root@bcoleman-X570:/etc/apt# vim sources.list
```

---

### Post by howefield on 2022-07-27
Thread moved to the "General Help" forum.

---

### Post by &amp;KyT$0P# on 2022-07-27
I can confirm that archive.ubuntu.com is not accessible over https.

Why do you need to access the repos over https?

---

