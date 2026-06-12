---
title: "Folder Sharing is deemed."
date: 2018-02-15
forum: General Help
---

### Post by Joao Lacerda on 2018-02-15
Hi Friends,

I need some help here, the foder sharing option is deemed.
On Ubuntu 16.04
[ATTACH=CONFIG]278555[/ATTACH]

Thank you for your time.

---

### Post by TheFu on 2018-02-15
Not all directories can be shared.  File permissions matter, which is what I suspect the issue here is. Don't use a GUI for this. They don't usually share with the best options, best performance or best integration with everything else on the machine.

Manually configure whatever sharing you need - if that is NFS, SFTP, or something else, it is pretty easy. There are how-tos. 

SFTP - it included when you install openssh-server. Every userid gets access via sftp. Every networked OS has a great sftp client. iOS, Android, Windows, OSX, whatever ... they all have great SFTP clients. Sftp is considered secure enough for use over the internet with ssh-keys for authentication.

NFS - useful for Unix-based OSes.  Not very useful for Windows or smartphones. This is the most efficient system-to-system network file system. Normal Unix permissions are honored.

Samba - really only useful for Windows on the same network.  

It is fine to setup multiple methods for the same storage. 

Which of these do you want?  Or is it some other protocol you need?

---

### Post by deadflowr on 2018-02-15
It actually looks like you're missing the checkbox next to the "Share this folder"
Which you need to check in order for it to be shareable.

Since you're using a non-normal theme, if you reset it to one of the default themes, like Ambiance or Radiance, does it show a checkbox again?

---

### Post by Joao Lacerda on 2018-02-16
Thanks for your quick response. 
I will try to configure an NTF connection.

---

### Post by Morbius1 on 2018-02-16
Never seen that before. My first instinct would be to reinstall nautilus-share:
```
sudo apt-get install --reinstall nautilus-share
```

If the check boxes are still missing create a usershare manually to see if something is wrong with the backend:
```
net usershare add Downloads $HOME/Downloads "" Everyone:F guest_ok=y
```
If it just comes back to the prompt it will have created the share. To verify run this command to see the share definition:
```
net usershare info --long
```
[COLOR=#0000cd]*Note: nautilus-share automatically changes Linux permissions on the shared folder to accommodate a write by a guest user which I did not include in my manual usershare command so you will have to do that yourself.*[/COLOR]

The comment about using a non-normal theme sorta makes sense but it's not apparent - to me - from your attachment that you are using one.

---

### Post by Joao Lacerda on 2018-02-16
Thank you!

I tried this:

sudo apt-get remove nautilus-share
======================================

sudo apt-get remove --auto-remove nautilus-share
=================================================

sudo apt-get pu rge --auto-remove nautilus-share
====================================


and I installed it again,

sudo apt- get update
sudo apt-get install nautilus-share

But it's still not working. :-(
All sharing options is deemed.

---

### Post by Joao Lacerda on 2018-02-16
Thank you all for your time.


I messed up with samba configurations years ago,
and that was the reason why sharing options was deemed.


That was for me the easy solution:


sudo apt-get remove --purge samba
sudo apt-get install samba


xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


sudo apt-get remove --purge smbclient lireinstalledbsmbclient
sudo apt-get install smbclient libsmbclient


xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


and I reinstalled samba.


--------------------------------
But I don't knew that the sharing folders uses Samba.
I want to share folders between ubuntu computers.


can someone point me to the right direction?


thank you in advance

---

### Post by Morbius1 on 2018-02-16
> But I don't knew that the sharing folders uses Samba.
I want to share folders between ubuntu computers.
Samba is the default file sharing mechanism in Ubuntu. If you think about it it's pretty much the default in all Linux desktop systems since parts of it are in the Linux kernel itself and all of them have libsmbclient by default.

Anyhoo ... TheFu gave you a list of alternatives and even mentioned the package you need to install for one of them ( SFTP ).

---

