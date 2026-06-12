---
title: "Using Apt Errors Out (Clearsigned file isn't valid, got NOSPLIT)"
date: 2024-04-23
forum: General Help
---

### Post by kabirgandhiok on 2024-04-23
Hi,

I have been unable to run updates through apt. It was working fine until yesterday. I can connect to the WIFI and browse the web or anything else, but apt won't work

```

lxhome@lxhome:~$ sudo apt update && sudo apt upgrade
[sudo] password for lxhome: 
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [262 B]                                   
Err:1 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                    
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Ign:2 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease                                              
Get:3 http://in.archive.ubuntu.com/ubuntu jammy InRelease [262 B]                    
Err:3 http://in.archive.ubuntu.com/ubuntu jammy InRelease                      
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:4 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease [262 B]                              
Err:4 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease                                      
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:5 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease [262 B]
Err:5 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Hit:6 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:2 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease
Reading package lists... Done
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://security.ubuntu.com/ubuntu jammy-security InRelease' is no longer signed.
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://in.archive.ubuntu.com/ubuntu jammy InRelease' is not signed.
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
lxhome@lxhome:~$ 

```

I don't have a LAN cable so I was not able to check through a wired connection. Connecting to my phone's network through a hotspot results in the same error.

```

lxhome@lxhome:~$ less /etc/resolv.conf 
nameserver 127.0.0.53
options edns0 trust-ad
search .

```

While trying to install vim

```

lxhome@lxhome:~$ sudo apt install vim
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwpe-1.0-1 libwpebackend-fdo-1.0-1
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  vim-runtime
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim vim-runtime
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,571 kB of archives.
After this operation, 37.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://security.ubuntu.com/ubuntu jammy-security/main amd64 vim-runtime all 2:8.2.3995-1ubuntu2.16 [6,835 kB]
Err:1 http://security.ubuntu.com/ubuntu jammy-security/main amd64 vim-runtime all 2:8.2.3995-1ubuntu2.16
  File has unexpected size (262 != 6835286). Mirror sync in progress? [IP: 2620:2d:4002:1::103 80]
  Hashes of expected file:
   - SHA512:814be7174938d2f65bdc005f2af017d0916a681963b7e7205678b4416d68131de3a29e685fb1e116a42e345308413ccaf3d519c1051ec816ce8659fbec1b2479
   - SHA256:31c348b1e7e93d429be7edfc79dfbf795690edd5d4830672f4429604051d352f
   - SHA1:cdb693754bfe6da5d31c0b1335489da689dffdbc [weak]
   - MD5Sum:6759fa9e59f16bd5e1d885df3374a786 [weak]
   - Filesize:6835286 [weak]
Get:2 http://security.ubuntu.com/ubuntu jammy-security/main amd64 vim amd64 2:8.2.3995-1ubuntu2.16 [1,736 kB]
Err:2 http://security.ubuntu.com/ubuntu jammy-security/main amd64 vim amd64 2:8.2.3995-1ubuntu2.16
  File has unexpected size (262 != 1735502). Mirror sync in progress? [IP: 2620:2d:4002:1::103 80]
  Hashes of expected file:
   - SHA512:40a003e0c5b999865a01c33be12829805e227157705d9a773ba1c19328c64386933ba1666f00e0fe7bad51f7cdde49a6c786290355f39c3cdf6063403cbd5d67
   - SHA256:33bea1bfa0e9e346402fae755605fa112ed84e628c64bdac826bb62ab486eb34
   - SHA1:1ac9f4a4e41a20a40497d1967b0e96b03b2b80db [weak]
   - MD5Sum:1aac7b5fa6106b3e48cdf9db7c72cf7e [weak]
   - Filesize:1735502 [weak]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_8.2.3995-1ubuntu2.16_all.deb  File has unexpected size (262 != 6835286). Mirror sync in progress? [IP: 2620:2d:4002:1::103 80]
   Hashes of expected file:
    - SHA512:814be7174938d2f65bdc005f2af017d0916a681963b7e7205678b4416d68131de3a29e685fb1e116a42e345308413ccaf3d519c1051ec816ce8659fbec1b2479
    - SHA256:31c348b1e7e93d429be7edfc79dfbf795690edd5d4830672f4429604051d352f
    - SHA1:cdb693754bfe6da5d31c0b1335489da689dffdbc [weak]
    - MD5Sum:6759fa9e59f16bd5e1d885df3374a786 [weak]
    - Filesize:6835286 [weak]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim_8.2.3995-1ubuntu2.16_amd64.deb  File has unexpected size (262 != 1735502). Mirror sync in progress? [IP: 2620:2d:4002:1::103 80]
   Hashes of expected file:
    - SHA512:40a003e0c5b999865a01c33be12829805e227157705d9a773ba1c19328c64386933ba1666f00e0fe7bad51f7cdde49a6c786290355f39c3cdf6063403cbd5d67
    - SHA256:33bea1bfa0e9e346402fae755605fa112ed84e628c64bdac826bb62ab486eb34
    - SHA1:1ac9f4a4e41a20a40497d1967b0e96b03b2b80db [weak]
    - MD5Sum:1aac7b5fa6106b3e48cdf9db7c72cf7e [weak]
    - Filesize:1735502 [weak]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
lxhome@lxhome:~$ 

```

Any suggestions on what I can do to fix this, would be very helpful. There were some posts that suggested changing nameserver to 8.8.8.8, but I don't see how it will help because I've never edited this field earlier, and it worked fine.

Thanks!
K

---

