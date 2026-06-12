---
title: "persistent usb - could not open lock file"
date: 2013-11-19
forum: General Help
---

### Post by Rahabib on 2013-11-19
I have a persistent usb xubuntu set up, but I am not sure if I am doing something wrong or what.

I created a new user and added sudo (and it worked)
```
sudo adduser <username> sudo
```
I can add repositories, but I cant apt install or update.
For instance if I run "apt-get update" I can login, it runs the update then at the end it returns 
> E: Could not open lock file /var/lib/dpkg/lock - open (5: Input/output error)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I also get similar issues with deleting files.
> Unable to find or create trash directory
I also cant lock the screen (cntl+alt+delete) or from the top panel.

I have tried deleting/removing /var/lib/dpkg/lock as others have stated in other posts (sorry didnt want to necro old posts).

Do i need to just reformat the usb drive and start over?  Shouldn't a default persistent drive set up by unetbootin allow me to install applications?  I know I cant update the kernel, but I cant add anything.

Thanks for any help.

---

