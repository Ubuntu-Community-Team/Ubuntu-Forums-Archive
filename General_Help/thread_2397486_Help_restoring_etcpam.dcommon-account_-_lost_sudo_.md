---
title: "Help restoring /etc/pam.d/common-account - lost sudo access"
date: 2018-07-30
forum: General Help
---

### Post by bballs91 on 2018-07-30
Hi All,

So I was trying to be able to authenticate with my newly create AD Domain against my Ubutnu Server and its samba shares. 

In the process I was fiddling with the /etc/pam.d/common-* files and was accidentally moved one instead of copying it.

So now I dont have a common-account and cannot access sudo to create a new one, or copy the old one back, or even change the permissions of the folder to create one with another account.

Is there anyway to restore this wihtout sudo rights?

FYI This is running on a VMWare ESXi Host. Ubuntu 16.04. 

Thanks!

EDIT:

So i found a bash script owned by my normal user which is run as root daily around 7:40. Here I was able to add a line ```
cp /etc/pam.d/common-account.pam-old /etc/pam.d/common-account
``` hopefully this works tomorrow morning :)

---

### Post by bballs91 on 2018-07-31
So my above idea, with adding a line to a bash script that runs as root did not work. This obviously could not be run as root, because root could generally not be used.

Sooo in case anyone comes across this thread and wants to know how I fixed it. I did the following:

1) Create a new VM in ESXi with Advanced settings and give it the HDD of the machine thats not working, but nothign else.
2) Boot from an .iso from your PC, preferably an Ubuntu Live CD.
3) Mount and chroot into your old partition
4) recreate the /etc/pam.d/common-account file, or whatever happens to be missing
5) exit and reboot!

Now initially I thoguht that would be it.. But ESXi then wouldnt start the VM, complaining about mismatched Instance IDs or something of the like. So therefore, I had to do the following:

6) SSH into the ESXi Host Server
7) Open the .vmdk file in vim and adjust the parent CID between [Name of virtual HDD].vmdk and [Name of virutal HDD]_000001.vmdk so they are linked together again. 
8) Then ESXi would boot my machine - however it still was not done. It hung at boot and said I needed to manually run fsck. So:
9) fsck /dev/sda1 -y 

10) Finallllyyy boot and regained sudo access!

---

