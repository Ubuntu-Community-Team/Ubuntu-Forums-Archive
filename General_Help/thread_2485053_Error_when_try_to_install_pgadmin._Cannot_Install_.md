---
title: "Error when try to install pgadmin. Cannot Install the public key for the repository."
date: 2023-03-18
forum: General Help
---

### Post by antonio-cpr on 2023-03-18
Hi 
I'm using Lubuntu but when i type lsb_release -a I get:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy

So, I'm trying to install pgadmin following the instructions of the official website. But when I paste the first command I get the error bellow:
```
sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/packages-pgadmin-org.gpg] https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'
Hit:1 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                                                     
Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease                                                                                               
Hit:3 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                                                     
Hit:4 https://download.sublimetext.com apt/stable/ InRelease                                                       
Hit:5 http://archive.ubuntu.com/ubuntu jammy-backports InRelease                                                   
Hit:6 http://apt.postgresql.org/pub/repos/apt jammy-pgdg InRelease               
Get:7 https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/jammy pgadmin4 InRelease [4,217 B]
Err:7 https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/jammy pgadmin4 InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8881B2A8210976F2
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://apt.postgresql.org/pub/repos/apt jammy-pgdg InRelease' doesn't support architecture 'i386'
W: GPG error: https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/jammy pgadmin4 InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8881B2A8210976F2
E: The repository 'https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/jammy pgadmin4 InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

Whats happening here and how can I fix this?

Source: [https://www.pgadmin.org/download/pgadmin-4-apt/](https://www.pgadmin.org/download/pgadmin-4-apt/)

---

### Post by Holger_Gehrke on 2023-03-18
That's not the first command. You overlooked the actual first command which uses curl and gpg to download and install the key that apt is complaining about ...

Holger

---

