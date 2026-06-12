---
title: "Cannot login to the desktop Ubuntu 18.04"
date: 2020-04-17
forum: General Help
---

### Post by gwubu on 2020-04-17
Hi there, 
I enter my user/pass to login to my desktop, once i press enter nothing happens and it resets to the login screen again.  I hit Ctrl/Alt/F3 and proceeded to update and received numerous messages.


```
Ign: 1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit: 2 http://dl.google.com/linux/chrome/deb stable Release
Hit: 3 http://deb.nodesource.com/node_12.x bionic InRelease
Hit: 4 http://ca.archive.ubuntu.com/ubuntu bionic InRelease
Err: 5 http://dl.google.com/linux/chrome/deb stable Release.gpg
    At least one invalid signature was encountered.
Err: 3 http://deb.nodesource.com/node_12.x bionic InRelease
    Splitting up /var/lib/apt/lists/deb.nodesource.com_node%5f12.x_dits_bionic_InRelease into data and signature failed
Err: 4 http://ca.archive.ubuntu.com/ubuntu bionic InRelease
    Splitting up /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_bionic_InRelease into data and signature failed
Hit: 6 http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu bionic InRelease
Err: 6  http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu bionic InRelease
    Splitting up  /var/lib/apt/lists/ppa.launchpad.net_mscore-ubuntu_mscore-stable_ubuntu_dists_bionic_InRelease  into data signature failed
Get: 7 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kb]
Err: 7 http://security.ubuntu.com/ubuntu bionic-security InRelease
   Error writing to output file - write (28: No space left on device) [IP: xx.xxx.88.142.xx]
Get: 8  http://ca.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kb]
Err: 8 http://ca.archive.ubuntu.com/ubuntu bionic-updates InRelease
    Error writing to output file - write (28: No space left on device) [IP: xx.xxx.91.39.xx]
Hit: 9 http://brave-browser-apt-release.s3.brave.com bionic InRelease
Err: 9 http://brave-browser-apt-release.s3.brave.com bionic InRelease
    Splitting up  /var/lib/apt/lists/brave-browser-apt-release.s3.brave.com bionic InRelease  into data signature failed
Get: 10 http://ca.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6kb]
Err: 10 http://ca.archive.ubuntu.com/ubuntu bionic-backports InRelease
    Error writing to output file - write (28: No space left on device) [IP: xx.xxx.91.39.xx]
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/chrome/deb stable Release: At least one invalis signature was encountered.
W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used. GPG error: http://deb.nodesource.com/node_12.x bionic InRelease: Splitting up /var/lib/apt/lists/deb.nodesource.com_node%5f12.x_dits_bionic_InRelease into data and signature failed
W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used. GPG error:  http://ca.archive.ubuntu.com/ubuntu bionic InRelease:  Splitting up /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_bionic_InRelease into data and signature failed.
W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu bionic InRelease:  Splitting up  /var/lib/apt/lists/ppa.launchpad.net_mscore-ubuntu_mscore-stable_ubuntu_dists_bionic_InRelease  into data signature failed.
W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used. GPG error: http://brave-browser-apt-release.s3.brave.com bionic InRelease: Splitting up  /var/lib/apt/lists/brave-browser-apt-release.s3.brave.com bionic InRelease  into data signature failed.
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/bionic InRelease  Splitting up  /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_bionic_InRelease  into data and signature failed.
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease  Error writing to output file - write (28: No space left on device) [IP: xx.xxx.91.39.xx]
W: Failed to fetch  http://ca.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease   Error writing to output file - write (28: No space left on device) [IP:  xx.xxx.91.39.xx]
W: Failed to fetch  http://ca.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease   Error writing to output file - write (28: No space left on device) [IP:  xx.xxx.91.39.xx]
W: Failed to fetch  http://brave-browser-apt-release.s3.brave.com/dists/bionic/InRelease  Splitting up  /var/lib/apt/lists/brave-browser-apt-release.s3.brave.com/dists/bionic/InRelease  into data signature failed.
W: Failed to fetch  http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu/dists/bionic/InRelease  Splitting up  /var/lib/apt/lists/ppa.launchpad.net_mscore-ubuntu_mscore-stable_ubuntu_dists_bionic_InRelease  into data signature failed.
W: Failed to fetch  http://deb.nodesource.com/node_12.x bionic InRelease  Splitting up /var/lib/apt/lists/deb.nodesource.com_node%5f12.x_dits_bionic_InRelease into data and signature failed.
W: Failed to fetch  http://dl.google.com/linux/chrome/deb stable Release.gpg  At least one invalid signature was encountered.
W: Some index files failed to download. They have been ignored, or older ones used instead.
```

---

### Post by DuckHook on 2020-04-17
Welcome to the forums, gwubu

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by gwubu on 2020-04-17
Hi DuckHook, thanks for the welcome :) I pasted the reply code to the Adv. Is it presented properly? Thank you.

---

### Post by ActionParsnip on 2020-04-18
Error writing to output file - write (28: No space left on device) [IP: xx.xxx.88.142.xx]

If you run:

df -h

What is the output please? If your partition is full then clear space. Running:

sudo apt-get clean 
sudo apt-get --purge autoremove

This will help some

---

### Post by DuckHook on 2020-04-18
> **gwubu said:**
> Hi DuckHook, thanks for the welcome :) I pasted the reply code to the Adv. Is it presented properly? Thank you.
I had already fixed your original post so no need to repost your info. But thank you for paying attention to it.

---

