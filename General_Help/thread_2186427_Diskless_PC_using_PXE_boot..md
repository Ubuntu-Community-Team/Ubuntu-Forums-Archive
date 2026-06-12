---
title: "Diskless PC using PXE boot."
date: 2013-11-07
forum: General Help
---

### Post by thanh2 on 2013-11-07
Hello,
I have tried these 2 guides on setting up a diskless PC which boots via PXE (the guide on serenux.com is more detailed):

[https://help.ubuntu.com/community/DisklessUbuntuHowto#Creating_your_NFS_installation](https://help.ubuntu.com/community/DisklessUbuntuHowto#Creating_your_NFS_installation)
[http://www.serenux.com/2011/04/howto-create-a-diskless-workstation-that-boots-from-pxe-using-ubuntu/#comments](http://www.serenux.com/2011/04/howto-create-a-diskless-workstation-that-boots-from-pxe-using-ubuntu/#comments)

When I try to boot the diskless machine, I receive this message: 

Begin: Retrying nfs mount &#8230; Begin: Running /scripts/nfs-premount &#8230; done
mount: Protocol not supported
done.


 [it keeps repeating those for a while, then:]


 Begin: Running /scripts/nfs-bottom &#8230; done.
done.
Begin: Running /scripts/init-bottom &#8230; mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn&#8217;t have requested /sbin/init
No init found. Try passing init= bootarg.


 [Drop in BusyBox]


 I tried doing the guides again from the beginning but still had this problem. Googling for a couple days but found no solutions. 

I would appreciate any help.

Regards,
Thanh.

---

### Post by jac3 on 2014-01-26
Did you ever resolve this.  I have gone down the same path and stuck at the same spot.  I saw a post where one guy said to add boot=nfs to the menu config but this didn't change anything for me.

---

### Post by thanh2 on 2014-01-27
Hi,
Yeah, the guy you mention was probably me. Actually I struggled with that for a long time and I can conclude that one should not try to solve the problem by googling around because it was really enigmatic, you will never know how and when it will be working.

The easiest method I found is that re-installing ubuntu (it's OK if you replace old ubuntu by a fresh one by choosing the option ubuntu offers). After that, customize ubuntu as you wish and follow the instruction from the beginning (link in my original post).

Hopes it helps,
Thanh.

---

### Post by jac3 on 2014-01-27
You right.  It was you!  I am almost to the point of using windows to boot ubuntu using this [http://www.howtogeek.com/162809/how-to-pxe-boot-an-ubuntu-image-from-windows-server-2008/](http://www.howtogeek.com/162809/how-to-pxe-boot-an-ubuntu-image-from-windows-server-2008/).  I really want to keep an open mind and start to get familiar with Linux but there are SOOOO many freakin builds of it, it is a bit overwhelming but I still feel for what I am trying to accomplish for my client it is the better solution.  He wants to boot over 200 diskless clients at the same time and I feel the overhead on Linux is a lot less that Windows.

So your saying re-install the client?  It was a fresh install and of the latest build from ubuntu. The only thing I did was apply updates and that was it.   You think the issue is with the client and not the configuration on the server?  

Thanks again!

---

### Post by thanh2 on 2014-01-28
Hello,
The larger the system, the more Linux is preferred over Windows. It's not your feeling or intuition, it's the truth.

To answer your question, re-install Ubuntu on the client (the to-be-diskless-machine). That must be a fresh install (Ubuntu 12.04.3 LST up to this moment), but you need not necessarily update everything in that Ubuntu to the latest. After that, follow the guide from serenux.com (link in my original post)

A few things you should take note for this is from my own experience. When PXE-booting PCs, the diskless client will consume its own hardware resources (processors, RAM), it does not consume those resources of the server. Because PXE-boot is a network-boot, the system will consume the bandwidth like crazy; thus you should use the best cables you have (gigabyte network). The most important thing is to make sure the Switches, which connect the whole system, are config'ed correctly to ensure the server receive the requests from clients (DHCP requests, ...).

Hopes you can work it out.
Thanh.

---

### Post by jac3 on 2014-01-28
Thanks man.  I did a lot more experimentation yesterday.    I used the guide I posted above getting a windows NFS server up and running hosting the PXS boot image and the results were exactly the same!  Fresh install of 12.04.3.   I ran through serenux guide and got the exact same boot error.  Then I prepared an image using remastersys and I get the same unable to mount error.  To me since I have changed the server from Linux to Windows and get the same error with two different deployment methods of Ubuntu Desktop 12.04.03 it seems like the error is in Ubuntu Desktop 12.04.  I am going to try an older version Ubuntu and see if I have the sane issues.

---

### Post by thanh2 on 2014-01-28
Hello,
make sure you have set up DHCP, TFTP and NFS correctly. Refer to this guide:
[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

That guide only guides you to PXE-boot the Ubuntu Live CD. The guide at this site:

[http://www.serenux.com/2011/04/howto-create-a-diskless-workstation-that-boots-from-pxe-using-ubuntu](http://www.serenux.com/2011/04/howto-create-a-diskless-workstation-that-boots-from-pxe-using-ubuntu)

shows you how to create YOUR OWN UBUNTU IMAGE. The 2 images are completely different. The Live CD boots Ubuntu by 'casper' thing, and you MUST set that image to read-only. The customized image looks like when you type "ls /" in the Terminal because you copy the whole Operating system from the client to the NFS server; you MUST set this image to read-write.

Do NOT use remastersys or any program to create your image. Follow the 2 guides (I put 2 links above) strictly and you will see the difference.

One more thing, you may wonder why Live CD image must be set to read-only and why customized image must be writable. It's a very long story so I won't post to confuse you. Actually it's a part of my Thesis.

Hopes it helps,
Thanh.

---

### Post by jac3 on 2014-01-28
Thanks but I downgraded to Ubuntu 10 and did both the remastersys method and serenux method and both of them booted successfully.    Something is up with 12.4 and I am not enough of a linux guy to tell you what or how to fix it.   Until that happens I am just going to use 10 for my pxe boots.

Later

---

### Post by kubassy on 2014-03-11
Hi!

I hope I can keep alive this thread, coz this guide very useful. I've tryed both method. Both of them are booted succesfuly,  but unfortunaetly the remastersys version is too slow at boot. With a useable distro, the squashfs file is min 1gb and I got only 100Mb lan for those workstation where I want to use. 

With the serenux method I got a permision problems. I don't realy understand the last step: "chmod 777 /var/tftp". 
The hole filesystem in the nfsroot folder. In the tftp only the kernel and the image (why need the kernel 777 perm?). And with this method the boot is stuck at the middle of the process with 'cant write to xy folder' When copy the filsystem files to the nfsroot I got error messages to all files, that can't keep owner and group. So all files in the nfs folder are created with nobody nogroup 700 permisions. If I run the 'chown -R 777 <nfsfolder (not tftp)> ' the os booted, but nothing works. Can't login etc, beacause of the permisions. The real UID-s are not the same wich are in the  /nfsshare/etc/passwd, which is used by the dikless os. 
Sorry for bad english. I hope it's understandable...

---

### Post by jac3 on 2014-03-11
Are you using 10 or 12.4?

I am still using 10.

In the end I used a Windows Server 2012 and setup an NFS file share and used that for the pxe boot server.    

I followed this post:  [http://www.howtogeek.com/162809/how-to-pxe-boot-an-ubuntu-image-from-windows-server-2008/](http://www.howtogeek.com/162809/how-to-pxe-boot-an-ubuntu-image-from-windows-server-2008/)

One issue I ran into was when copying the files from the main boot copy using serenux's method to the windows box the permissions were all screwed up on the windows side and I couldn't correct them using any tool I tried.

So now I have a Windows server 2012 box with DHCP and hosts the pxelinux.cfg and a linux ubuntu nfs file share hosting the files for the client.  So the clients are booting from the windows box and the cfg file is pointed to the NFS share on the ubuntu server.

The main issue is if you boot multiple clients from the nfs share using serenux all the clients are sharing the same files.  If you fire up two of them and shut one down via the shutdown command it crashes the entire share.

I built this for a client testing diskless pcs.  So I put the nfs share ubuntu box on a vm and now they boot 100s of laptops and desktops to the nfs share and just hard shut down the machines.  If they screw up and shutdown on through linux then I restore the snapshot back to when it worked and everything starts working again.

Not to elegant but they are flying through machines testing them now.

---

