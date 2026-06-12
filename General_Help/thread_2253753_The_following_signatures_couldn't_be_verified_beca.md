---
title: "The following signatures couldn't be verified because the public key is not available"
date: 2014-11-22
forum: General Help
---

### Post by michael235 on 2014-11-22
Im getting an error with software updater:
Failed to download repository information

Check your Internet connection.
my internet connection is working how else would i be able to post this
log is

W:GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DE32F3C29122E0C2, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DE32F3C29122E0C2, W:Failed to fetch [http://linux.dropbox.com/ubuntu/dists/utopic/main/binary-amd64/Packages](http://linux.dropbox.com/ubuntu/dists/utopic/main/binary-amd64/Packages)  Bad header line
, W:Failed to fetch [http://linux.dropbox.com/ubuntu/dists/utopic/main/binary-i386/Packages](http://linux.dropbox.com/ubuntu/dists/utopic/main/binary-i386/Packages)  0  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by flaymond on 2014-11-22
Download Synaptic Package Manager -

```
sudo apt-get install synaptic
```

open it -

```
sudo synaptic
```

go to settings, repositories , then check the repository that you had...and make sure it was right...


* I got the similar problem today, and i suggest you to take others opinion for more detailed help. :)

---

### Post by pqwoerituytrueiwoq on 2014-11-22
[**[COLOR=#000000]@InterProg[/COLOR]**]("http://ubuntuforums.org/member.php?u=1952864") you can get there by open software sources ([FONT=courier new]software-properties-gtk[/FONT])

i think op is/was having a odd network issues, maybe dns related

---

