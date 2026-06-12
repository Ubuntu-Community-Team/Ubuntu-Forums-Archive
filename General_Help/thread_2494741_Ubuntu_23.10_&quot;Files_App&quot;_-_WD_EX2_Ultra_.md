---
title: "Ubuntu 23.10 &quot;Files App&quot; - WD EX2 Ultra NAS"
date: 2024-01-25
forum: General Help
---

### Post by exhile on 2024-01-25
Hello everyone,

I just recently reinstalled Ubuntu 23.10 on my laptop and now my WD EX2 Ultra NAS cannot be viewed by the "Files app" in Ubuntu 23.10. Prior to more reinstall of the operating system, Ubuntu 23.10 could see my EX2 Ultra using the "Files App" and I could access all the files on my NAS. I am not sure what has changed since before and after the reinstall of the O/S. I can presently SSH into my EX2 Ultra NAS via terminal changing directories and listing files. I also installed SAMBA with no change in the results as well.

If anyone here on this forum could assist with this issue, that would be greatly appreciated. I have searched the forums with keywords regarding the issue to no avail records of a similar issue.

---

### Post by TheFu on 2024-01-26
NFS or CIFS connection to the NAS?
If CIFS, verify that it supports SMB3+.  There are ways to enable old, defunct, versions, but Win10 and 11 both use SMB3+.

Of course, the NAS should support NFS and since that's the native mode for network storage in any Unix-based OS, NFS should always be preferred over other methods.

Lastly, WD devices that allow internet access to storage have a history of security failures, so I would strongly caution against allowing the internet aspects of the device to be enabled or used.  It can still be used as a NAS on your LAN, probably and if you need internet access, setup sftp on your Ubuntu system to be available over the internet using ssh-keys for authentication. Then all your data can be available from anywhere, AND be secure.

I looked at the WD page for this device and they don't mention NFS or CIFS, which is not good.  It is actually scary they don't list supported network protocols for storage on a NAS.  I'd call it crazy.

[https://support-en.wd.com/app/answers/detailweb/a_id/14890/~/my-cloud%3A-configure-nfs-service](https://support-en.wd.com/app/answers/detailweb/a_id/14890/~/my-cloud%3A-configure-nfs-service) came up with a search and it doesn't say it is not supported on your model, so perhaps it is?  NFS makes network storage appear like local storage and it is faster than other network file protocols.

---

### Post by exhile on 2024-01-27
> **TheFu said:**
> NFS or CIFS connection to the NAS?
If CIFS, verify that it supports SMB3+.  There are ways to enable old, defunct, versions, but Win10 and 11 both use SMB3+.

Of course, the NAS should support NFS and since that's the native mode for network storage in any Unix-based OS, NFS should always be preferred over other methods.

Lastly, WD devices that allow internet access to storage have a history of security failures, so I would strongly caution against allowing the internet aspects of the device to be enabled or used.  It can still be used as a NAS on your LAN, probably and if you need internet access, setup sftp on your Ubuntu system to be available over the internet using ssh-keys for authentication. Then all your data can be available from anywhere, AND be secure.

I looked at the WD page for this device and they don't mention NFS or CIFS, which is not good.  It is actually scary they don't list supported network protocols for storage on a NAS.  I'd call it crazy.

[https://support-en.wd.com/app/answers/detailweb/a_id/14890/~/my-cloud%3A-configure-nfs-service](https://support-en.wd.com/app/answers/detailweb/a_id/14890/~/my-cloud%3A-configure-nfs-service) came up with a search and it doesn't say it is not supported on your model, so perhaps it is?  NFS makes network storage appear like local storage and it is faster than other network file protocols.

Thanks @TheFu for your suggestions and overall reply. 

The MyCloud EX2 Ultra does support NFS as well as SMB3. I will continue troubleshooting the issue.

---

### Post by TheFu on 2024-01-27
Nautilus is the the real name of the "File" program.  You should be able to find the dependencies to get SMB3 working through it.

However, NFS is faster and feels like local storage, so it would be a better choice.  You'll want to use the /etc/fstab to mount it via NFS or via CIFS/SMB to control the mount options better.  When this happens, it appears as local storage and doesn't have a drive icon in any applications.  To make access quick, create a symbolic link from your HOME directory to this network storage.

For NFS, you can test the mount using 1 command after installing the nfs-common package.  There are lots of posts in these forums that show the fstab examples for NFS and for CIFS/Samba.  Using the mount command in a terminal with lots of verbose output is the quick way to see issues with mounts when there is any issue.

---

### Post by exhile on 2024-01-28
> **TheFu said:**
> Nautilus is the the real name of the "File" program.  You should be able to find the dependencies to get SMB3 working through it.

However, NFS is faster and feels like local storage, so it would be a better choice.  You'll want to use the /etc/fstab to mount it via NFS or via CIFS/SMB to control the mount options better.  When this happens, it appears as local storage and doesn't have a drive icon in any applications.  To make access quick, create a symbolic link from your HOME directory to this network storage.

For NFS, you can test the mount using 1 command after installing the nfs-common package.  There are lots of posts in these forums that show the fstab examples for NFS and for CIFS/Samba.  Using the mount command in a terminal with lots of verbose output is the quick way to see issues with mounts when there is any issue.

Wow, lots of good suggestions to resolve the issue I am experiencing. Thanks again @TheFu

---

