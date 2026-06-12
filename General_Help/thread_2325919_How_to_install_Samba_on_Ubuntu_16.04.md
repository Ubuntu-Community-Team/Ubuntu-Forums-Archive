---
title: "How to install Samba on Ubuntu 16.04"
date: 2016-05-26
forum: General Help
---

### Post by ckrles on 2016-05-26
How can I install samba on Ubuntu 16.04. I used to install it on 14.04 by going to software center and searching it. I can't find it right now.

Any help?

Thanks.

---

### Post by deadflowr on 2016-05-26
The new software center lacks, a lot.
If you mean the samba that used to be in there that had a launcher icon like:
[ATTACH=CONFIG]269304[/ATTACH]
If so the package for it is system-config-samba.
So in a terminal run
```
sudo apt install system-config-samba
```
That should install it. A long with all the needed other samba packages.

If that's not what you mean, post more about what you mean.

---

### Post by Linuxisfast on 2016-05-26
Its as simple as right click on folder and enable local share, it will ask you permission to install Samba. After that sudo smbpasswd -a user and you are all set after reboot. Still the easiest distro to do Samba with.

---

### Post by Morbius1 on 2016-05-27
The reason you are getting two different answers is because of an unfortunate coincidence.

There is a package named "samba" that contains the stuff required to set up a samba server. In the software centre there is an application called "Samba" which is the package "system-config-samba" which is used to configure that samba server.

Ever the optimist I believe system-config-samba is not in the Software Centre because the package isn't configured correctly as indicated by many bug reports such as these:

[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1490216](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1490216)
[https://bugs.launchpad.net/ubuntu/+bug/1477714](https://bugs.launchpad.net/ubuntu/+bug/1477714)
[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1453223](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1453223)
[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1450962](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1450962)
[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1421194](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1421194)

And even if you resolve the issue yourself you need to be careful with how you use it because of this:
[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1346134](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1346134)

The system-config-samba package needs to be updated, the packaging engineer needs to set the dependencies and configurations correctly, or the package needs to be removed entirely from the repositories ... in my opinion ....

---

### Post by ckrles on 2016-05-29
Sorry. i have been away for a couple of days. I will try your suggestions. Thanks.

---

### Post by ckrles on 2016-06-01
> **deadflowr said:**
> The new software center lacks, a lot.
If you mean the samba that used to be in there that had a launcher icon like:
[ATTACH=CONFIG]269304[/ATTACH]
If so the package for it is system-config-samba.
So in a terminal run
```
sudo apt install system-config-samba
```
That should install it. A long with all the needed other samba packages.

If that's not what you mean, post more about what you mean.

> **Morbius1 said:**
> The reason you are getting two different answers is because of an unfortunate coincidence.

There is a package named "samba" that contains the stuff required to set up a samba server. In the software centre there is an application called "Samba" which is the package "system-config-samba" which is used to configure that samba server.

Ever the optimist I believe system-config-samba is not in the Software Centre because the package isn't configured correctly as indicated by many bug reports such as these:

[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1490216](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1490216)
[https://bugs.launchpad.net/ubuntu/+bug/1477714](https://bugs.launchpad.net/ubuntu/+bug/1477714)
[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1453223](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1453223)
[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1450962](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1450962)
[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1421194](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1421194)

And even if you resolve the issue yourself you need to be careful with how you use it because of this:
[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1346134](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1346134)

The system-config-samba package needs to be updated, the packaging engineer needs to set the dependencies and configurations correctly, or the package needs to be removed entirely from the repositories ... in my opinion ....



I installed it according to deadflowr instructions, but when I run it it prompts to type in my password and nothing happens.
Besides, when I set up the permissions on a specified folder, they are reset to default and it doesn't allow me to connect.

Any ideas?

Thanks.

---

### Post by Morbius1 on 2016-06-01
>  I installed it according to deadflowr instructions, but when I run it it prompts to type in my password and nothing happens.
Now you know why it's not in the Software Centre and why I listed all those bug reports.

Run the following command in a terminal:
```
gksu system-config-samba
```
If you get a bunch of python errors and finally something that looks like this:
> SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory
Create the missing file so it's happy:
```
sudo touch /etc/libuser.conf
```

---

