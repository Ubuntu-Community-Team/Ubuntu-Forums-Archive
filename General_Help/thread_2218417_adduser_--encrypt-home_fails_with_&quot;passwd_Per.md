---
title: "adduser --encrypt-home fails with &quot;passwd: Permission denied&quot;"
date: 2014-04-20
forum: General Help
---

### Post by christian19 on 2014-04-20
Hi all,

I have searched around for my problem and I've still no idea what's wrong. I decided to sign up here and I hope that someone has an idea!

I have setted up a new PC with Kubuntu 14.04. When I try to add a user with encrypted home I get this:

```

ins@espp920ku:~$ sudo -i
[sudo] password for ins: 

root@espp920ku:~# adduser --encrypt-home --debug osterhase
Adding user `osterhase' ...
Selecting UID from range 1000 to 29999 ...
Selecting GID from range 1000 to 29999 ...
Adding new group `osterhase' (1001) ...
/usr/sbin/groupadd -g 1001 osterhase
Adding new user `osterhase' (1001) with group `osterhase' ...
/usr/sbin/useradd -d /home/osterhase -g osterhase -s /bin/bash -u 1001 osterhase
Creating home directory `/home/osterhase' ...
Setting up encryption ...
/usr/bin/ecryptfs-setup-private -b -u osterhase

************************************************************************
YOU SHOULD RECORD YOUR MOUNT PASSPHRASE AND STORE IT IN A SAFE LOCATION.
  ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
THIS WILL BE REQUIRED IF YOU NEED TO RECOVER YOUR DATA AT A LATER TIME.
************************************************************************


Done configuring.

Copying files from `/etc/skel' ...
/bin/umount /home/osterhase
Enter new UNIX password: 
Retype new UNIX password: 
passwd: Permission denied
passwd: password unchanged
Try again? [y/N] n
/usr/bin/chfn osterhase
Changing the user information for osterhase
Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [Y/n] y
root@espp920ku:~#

```

The adduser script is asking for a new password. I can enter everything but I always get Permission denied.

I had modified system wide umask settings (UMASK 027 in /etc/login.defs) and adduser DIR_MODE (DIR_MODE=0750 in /etc/adduser.conf) but setted back to default for troubleshooting with no effect. Default: UMASK 022, DIR_MODE=0755

On my Laptop with Kubuntu 13.10 all works fine!

Any ideas?

Best regards
Christian

---

### Post by martin110 on 2014-06-18
I had the exactly same problem. It seems that the access rights of /home/.ecryptfs are wrong.

What resolved the problem for me: As root do rm -rf /home/.ecryptfs, then again adduser --encrypt-home ...
But I guess that there must be a simpler solution, possibly a chmod 755 /home/.ecryptfs should do the trick.

- Martin

---

