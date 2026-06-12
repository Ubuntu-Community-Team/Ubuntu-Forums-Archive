---
title: "Updating in synpatic manager error"
date: 2015-07-03
forum: General Help
---

### Post by UncleMonty on 2015-07-03
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 13B00F1FD2C19886

W: Failed to fetch [http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by mikewhatever on 2015-07-03
Looks like something is wrong with the repository. You may want to try asking at [https://community.spotify.com/](https://community.spotify.com/).

---

### Post by oldos2er on 2015-07-03
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 13B00F1FD2C19886

sudo apt-get update
```

---

