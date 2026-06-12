---
title: "Having really hard time mounting NFS shares in Windows 2022"
date: 2023-08-24
forum: General Help
---

### Post by furydev on 2023-08-24
Hi All, 

I've got a Ubuntu server AD Joined - viewing several SAMBA Shares all working. 

The Ubuntu server delivers an NFS Share for some engineering functions and files. 

Despite adding the NFS Client to windows I cannot mount the share to a drive letter. I have tried mount -o and PowerShell tells me its ambiguous. I cannot believe I am the first person to do this, everything seems to be failing. 

Any ideas on Syntax etc? What works what doesn't ? 

Thanks in advance!

---

### Post by SeijiSensei on 2023-08-24
Name resolution problem perhaps? What if you use \\ip.addr.of.server\share instead of its hostname?

Would it be easier to install Samba on the Ubuntu box and use CIFS for everything?

---

### Post by yancek on 2023-08-24
The method and steps suggested at the site at the link below state that it is the way to do it.  Not sure if this is what you have done and I have never used nfs with windows so can't be of any more assisteance.

[https://blog.netwrix.com/2022/11/18/mounting-nfs-client-windows/](https://blog.netwrix.com/2022/11/18/mounting-nfs-client-windows/)

---

### Post by MAFoElffen on 2023-08-24
This is not really an Ubuntu or Linux question, but since I also do Windows Desktop and Server support...

The Windows OS method:
> 
*"To mount an NFS share using the built-in Windows 10 NFS client, open the File Explorer and click on This PC. Then, click on the Computer tab and select Map Network Drive. In the Folder field, enter the path to the NFS share. For example, if the NFS share is at /mnt/nfs, you would enter \\server\mnt\nfs."*

But you were hinting at doing it with PowerShel so, either following the format of these two examples:
```

mount.exe 10.0.0.7:/nfs_share Z:\
# or
 New-PSDrive -Name Z -PSProvider FileSystem -Root "\\10.0.0.7\export\nfs_share -Persist

```
Two differing perspectives on that. First- Since you are joined to AD and AD requires DNS... Then you can interchange/substitute the DNS name or IP, without any issues. 

Next, since it is AD Domain, I am assuming that the required NFS services are installed, running, and working correctly. Right?

Windows OS does not support NFS as well as SMB. They tend to fall back to the dark ages with that, as SMB is their own native protocol, and their mentality is that "Windows OS" exists in a vacuum with no one else existing outside of that. Only lately has that started to change. That is why "my niche" (successfully) was needed to get everything to work and play nice together, as one seamless environment. That large grey area between the black & white is where the real work is. As it should be.

---

### Post by furydev on 2023-08-25
Hi - All AD Joined - the shares are available to the mixed RHEL and Debian based distoo machines on the same network and that is working fine.

Access via IP or FQDN not working in Windows 2022.. 

And yes, open source hybrid environments are my niche too - down to KVM/QEMU mixed HyperV etc ... 

I cannot understand why this isn't working - admittedly a while since I've done it - but .....

---

