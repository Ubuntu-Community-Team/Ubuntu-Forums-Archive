---
title: "ProtonVPN certificate errors and installation process procedures"
date: 2023-06-11
forum: General Help
---

### Post by acew1zard on 2023-06-11
I follow the guide and I HAVE THE LATEST VERSION of Ubuntu: 
```

noach-chazzan@noach-chazzan-21A4:~/Downloads$ echo "c68a0b8dad58ab75080eed7cb989e5634fc88fca051703139c025352a6ee19ad protonvpn-stable-release_1.0.3-2_all.deb" | sha256sum --check -
protonvpn-stable-release_1.0.3-2_all.deb: OK
noach-chazzan@noach-chazzan-21A4:~/Downloads$ sudo apt-get update
Hit:1 http://archive.ubuntu.com/ubuntu lunar InRelease                  
Ign:2 https://repo.protonvpn.com/debian stable InRelease                
Hit:3 http://archive.ubuntu.com/ubuntu lunar-updates InRelease
Hit:4 http://archive.ubuntu.com/ubuntu lunar-backports InRelease
Hit:5 http://archive.ubuntu.com/ubuntu lunar-security InRelease
Ign:2 https://repo.protonvpn.com/debian stable InRelease
Ign:2 https://repo.protonvpn.com/debian stable InRelease
Err:2 https://repo.protonvpn.com/debian stable InRelease
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 104.26.5.35 443]
Reading package lists... Done
W: Failed to fetch https://repo.protonvpn.com/debian/dists/stable/InRelease  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 104.26.5.35 443]
W: Some index files failed to download. They have been ignored, or old ones used instead.
noach-chazzan@noach-chazzan-21A4:~/Downloads$ sudo apt-get install protonvpn
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package protonvpn
noach-chazzan@noach-chazzan-21A4:~/Downloads$ ls
protonvpn-stable-release_1.0.3-2_all.deb
noach-chazzan@noach-chazzan-21A4:~/Downloads$ 

```

Does any one here have protonVPN running on their computer? I get an error related to certificate error. Why?I got this error before and no one was able to help so I THINK does that mean no one uses protonVPN? I clicked the .deb file an it launched and ran/installed in the local software package manager, then I ran the terminal commands and instantly I got the above error messages. I am somewhat new to Linux and not that smart so please forgive me but this is the only truly free VPN service out there and is a very popular one so I think this is important.

---

### Post by acew1zard on 2023-06-11
```
noach-chazzan@noach-chazzan-21A4:~$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
Executing: /tmp/apt-key-gpghome.9X0W3CuMRs/gpg.1.sh --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
gpg: key 68818C72E52529D4: public key "MongoDB 4.0 Release Signing Key <packaging@mongodb.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
noach-chazzan@noach-chazzan-21A4:~$ echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse
noach-chazzan@noach-chazzan-21A4:~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu lunar InRelease                         
Ign:2 https://repo.protonvpn.com/debian stable InRelease                       
Get:3 http://archive.ubuntu.com/ubuntu lunar-updates InRelease [109 kB]        
Ign:4 https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 InRelease     
Get:5 http://archive.ubuntu.com/ubuntu lunar-backports InRelease [99.8 kB]     
Get:6 https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release [2,989 B]
Ign:2 https://repo.protonvpn.com/debian stable InRelease                       
Get:7 https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release.gpg [801 B]
Ign:7 https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release.gpg
Get:8 http://archive.ubuntu.com/ubuntu lunar-security InRelease [109 kB]
Ign:2 https://repo.protonvpn.com/debian stable InRelease
Err:2 https://repo.protonvpn.com/debian stable InRelease                       
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 104.26.4.35 443]
Reading package lists... Done                                                  
W: https://repo.mongodb.org/apt/ubuntu/dists/bionic/mongodb-org/4.0/Release.gpg: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: GPG error: https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release: The following signatures were invalid: EXPKEYSIG 68818C72E52529D4 MongoDB 4.0 Release Signing Key <packaging@mongodb.com>
E: The repository 'https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
noach-chazzan@noach-chazzan-21A4:~$ sudo apt install -y mongodb-org
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package mongodb-org

```
I also get this error when I try to install and setup up mongodb. I don't know what is going on at this point. Please any help will suffice because this is important.

---

### Post by acew1zard on 2023-06-11
```

noach-chazzan@noach-chazzan-21A4:~$ sudo nano /etc/apt/sources.list
noach-chazzan@noach-chazzan-21A4:~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu lunar InRelease                         
Ign:2 https://repo.protonvpn.com/debian stable InRelease                       
Get:3 http://archive.ubuntu.com/ubuntu lunar-updates InRelease [109 kB]        
Ign:4 https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 InRelease     
Ign:5 https://apache.bintray.com/couchdb-deb bionic InRelease                  
Get:6 https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release [2,989 B]
Get:7 https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release.gpg [801 B]
Ign:2 https://repo.protonvpn.com/debian stable InRelease                       
Ign:7 https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release.gpg
Get:8 http://archive.ubuntu.com/ubuntu lunar-backports InRelease [99.8 kB]
Ign:5 https://apache.bintray.com/couchdb-deb bionic InRelease                  
Get:9 http://archive.ubuntu.com/ubuntu lunar-security InRelease [109 kB] 
Ign:2 https://repo.protonvpn.com/debian stable InRelease
Ign:5 https://apache.bintray.com/couchdb-deb bionic InRelease                  
Err:2 https://repo.protonvpn.com/debian stable InRelease                       
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 104.26.4.35 443]
Err:5 https://apache.bintray.com/couchdb-deb bionic InRelease                  
  Certificate verification failed: The certificate is NOT trusted. The name in the certificate does not match the expected.  Could not handshake: Error in the certificate verification. [IP: 52.44.66.176 443]
Reading package lists... Done                                                  
W: https://repo.mongodb.org/apt/ubuntu/dists/bionic/mongodb-org/4.0/Release.gpg: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: GPG error: https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release: The following signatures were invalid: EXPKEYSIG 68818C72E52529D4 MongoDB 4.0 Release Signing Key <packaging@mongodb.com>
E: The repository 'https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
noach-chazzan@noach-chazzan-21A4:~$ sudo apt install couchdb
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package couchdb is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'couchdb' has no installation candidate
noach-chazzan@noach-chazzan-21A4:~$ 



```
EVEN when I modify the sources files and do it for clouddb I Get the same error. I think ubuntu devs need to know about this so we can fix it together. How do I report a bug to the dev community.

---

