---
title: "Windows Host - Kubuntu on guest (VMware/Virtualbox)"
date: 2007-02-08
forum: General Help
---

### Post by stormyuk on 2007-02-08
Hi,

In my desire to run Linux and test it more but without having to dual boot I decided to try running Kubuntu as a virtual machine from within Windows XP. I just can't dump windows just yet as at the moment I am still finding I use more Windows apps than Linux. 

It all works great on both VMware and Virtualbox.

However, in VMware for the Samba shares I can readily see my Windows Host files after I changed the smb.conf to use the line:

interface = eth0 vmnet1

As per the instructions in VMware documentation.

However, I can't for the life of me get Virtualbox working, it can NEVER see my Windows Host shares. It just complains that it cant find files and it may be due to a firewall (which I don't believe it is).

I want to get VMware and Virtualbox working identically so that I can test and see which I find the best, for now VMware is wining purely because it works with Samba with one little tweak. 

All the info I read on Samba has reams and reams of config files to change which didnt seem necessary in VMware.

Also is it possible to Mount the SMB shares so they appear as drives in Linux? As for example at the moment when I tried to play an MP3 direct from the SMB share in Kubuntu Amarok thought it was a "stream" as opposed to MP3 and readily crashed.

Any help would be appreciated.

Thanks,

Mike

---

### Post by g8m on 2007-02-08
I hang shares in the linux file system with smbmount.

  smbmount //server/share /home/evil/mnt

The mnt folders contains the shared files and amarok will have no problem playing them.

---

### Post by stormyuk on 2007-02-08
Thanks, I assume that will work with VMware where my shares are working, but I still need to figure out how to get the shares working in the first place with Virtualbox.

Cheers,

Mike

---

### Post by kodoku on 2007-03-04
if you've enabled default network settings for VirtualBox, then you must be using the NAT interface, which does not allow incoming connections (meaning file sharing). 

To enable sharing, you must use the Host Networking interface, refer to this guide: [http://ubuntuforums.org/showthread.php?t=346185&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=346185&highlight=virtualbox)

---

