---
title: "Can I do clean installings of Ubuntu?"
date: 2008-05-27
forum: General Help
---

### Post by jras20 on 2008-05-27
Hopefully this wont happen for a while, but incase my laptop hard drive crashes, can I do a clean install on Ubuntu, and not half to install windows?  I have Ubuntu 8.04 installed with Vista right now.  Ubuntu is my default boot O/S.
Thanks.

---

### Post by forestpixie on 2008-05-27
Yea - just install on the same partition as it already is and it'll do that for you.

---

### Post by warp99 on 2008-05-27
> **jras20 said:**
> Hopefully this wont happen for a while, but incase my laptop hard drive crashes, can I do a clean install on Ubuntu, and not half to install windows?  I have Ubuntu 8.04 installed with Vista right now.  Ubuntu is my default boot O/S.
Thanks.

Sure you can. Just re-install to the Ubuntu partition during setup and all is well. You can also re-install Windows if that crashes instead, but a little more work is involved:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28reinstall%29%7C%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28reinstall%29%7C%28windows%29)

Now if you want to make a reinstall of Ubuntu very painless just do the following:

Before you have a crash backup your home directory using the following command:
```
tar -cjvpf myhomediretory.bz2 /home 
```
then save all of your installed package settings:
```
dpkg --get-selections > installed_pkgs.txt
```
Now if you have to reinstall you can just restore you home directory:
```
sudo tar -xvf myhomedirectory.bz2 -C /
```
then restore your packages:
```
 sudo dpkg --set-selections < installed_pkgs.txt
```
and run a  'sudo apt-get dselect-upgrade' to install all of your packages from your previous setup.

---

