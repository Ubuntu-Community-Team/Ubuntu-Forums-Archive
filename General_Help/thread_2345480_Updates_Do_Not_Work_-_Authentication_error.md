---
title: "Updates Do Not Work - Authentication error"
date: 2016-12-04
forum: General Help
---

### Post by PEM59 on 2016-12-04
I Have Ubuntu 16.04.
About 3 weeks ago the updates started not working.

I go through the automatic updates and it says 
"Requires installation of untrusted packages"
"This requires installing packages from unauthenticated sources."

Did my authentication get messed up?
Did my key files get corrupted?

---

### Post by howefield on 2016-12-04
Post the output from running these two terminal commands..

```
sudo apt update
```
```
sudo apt upgrade
```

---

### Post by QIII on 2016-12-04
Hello!

Could you attempt to perform the updates in the terminal and post back the results?  This will help immensely in understanding what is going on.

Please surround your output in code tags, which you may do in one of three ways:

1.  Click the # button above the text input box.  Place your cursor between the code tags and type or copy your text.

2.  Type or copy your text, highlight it and then click the # button above the text input box.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by PEM59 on 2016-12-04
Sudo apt Update

```

Ubuntu:~$ sudo apt update
[sudo] password for xxxx: 
Get:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Err:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease  
  At least one invalid signature was encountered.
Err:2 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease
  At least one invalid signature was encountered.
Err:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
  At least one invalid signature was encountered.
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com/ubuntu xenial InRelease: At least one invalid signature was encountered.
E: The repository 'http://us.archive.ubuntu.com/ubuntu xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://us.archive.ubuntu.com/ubuntu xenial-security InRelease: At least one invalid signature was encountered.
E: The repository 'http://us.archive.ubuntu.com/ubuntu xenial-security InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease: At least one invalid signature was encountered.
E: The repository 'http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Ubuntu:~$ 

```

sudo apt upgrade

```


Ubuntu:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  account-plugin-identica account-plugin-twitter gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-networkmanager-1.0 libcdaudio1 libenca0
  libfaac0 libslv2-9 linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic
  linux-image-4.4.0-34-generic linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic
  linux-image-extra-4.4.0-34-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libsnapd-glib1 linux-headers-4.4.0-51 linux-headers-4.4.0-51-generic linux-image-4.4.0-51-generic
  linux-image-extra-4.4.0-51-generic snapd-login-service
The following packages will be upgraded:
  gnome-software gnome-software-common linux-generic linux-headers-generic linux-image-generic
  ubuntu-software
6 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 69.4 MB of archives.
After this operation, 238 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  ubuntu-software gnome-software gnome-software-common libsnapd-glib1 linux-image-4.4.0-51-generic
  linux-image-extra-4.4.0-51-generic linux-generic linux-image-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-generic snapd-login-service
Install these packages without verification? [y/N] 

```

Note - If I run it from this point without verification, it will complete the update.

---

### Post by howefield on 2016-12-05
Try changing the mirror to the main server, you can do this from the Software & Updates application.

Are you using a proxy server by any chance ?

---

### Post by PEM59 on 2016-12-05
I tried changing the server in the updates app. 
It did not make a difference.
I am not using a proxy server.

---

