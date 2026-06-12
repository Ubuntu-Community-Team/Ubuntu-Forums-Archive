---
title: "smbfs not working"
date: 2007-10-27
forum: General Help
---

### Post by spawnlcd on 2007-10-27
Hi Everyone, 

I have upgraded from Ubuntu Server 6.0.6.1, to 7.10, and I all of a sudden I started having problems with my smbfs mounts not loading. Here is what I did, I placed the mounting points for the smbfs on the /etc/fstab, as so:

#NAS Shared Folders

//192.168.1.xx/xx_share /NAS/xx_share smbfs auto,username=,password=

//192.168.1.xx/xx_client /NAS/xx_client smbfs auto,username=,password=

//192.168.1.xx/xx_server /NAS/xx_server smbfs auto,username=,password=

//192.168.1.xx/xx_share /NAS/xx_share smbfs auto,username=,password=

//192.168.1.xx/xx1 /NAS/xx1 smbfs auto,username=,password=

and when I issued a "mount -a", the mounts loaded, and I saw them on the "mount" output. However, as soon as I reboot the server, the mounts no longer loads. I tried issuing the "mount -a" command again, but I only get this:

Could not resolve mount point /NAS/xx
Could not resolve mount point /NAS/xx_client
Could not resolve mount point /NAS/xx_server
Could not resolve mount point /NAS/media_share
Could not resolve mount point /NAS/xx1

Another thing I am noticing is when I issue a "ls /NAS/<Any of the mounts I created>" it locks up. 


The strange part is that I have another another Ubuntu server runnning 7.10 that is running the same smbfs configuration with no problems. Any ideas or direction would be great.

Thanks,

Rafael

---

### Post by mahousaru on 2007-10-27
try substituting smbfs for cifs

---

### Post by petervn1 on 2007-10-27
I was having the same issues. After upgrading to Gutsy Gibbon my windows mounts were no longer showing up. I poked around a little a bit, and then tried to mount the windows to a different directory, and it worked! So apparently, it was not the smbfs to blame, but the mount point itself. Here is what I did to get my windows shares back after upgrading to Gutsy Gibbon. 

/etc/fstab (no changes are needed)

//192.168.1.2/<share> /mnt/win/WinDrive smbfs ro,nouser,username=<uname>,password=<pswd>,uid=<username>,gid=<groupname>,fmask=770,dmask=770 0 0

- Un-mount the /mnt/win/WinDrive using the following command (repeat it for each mount point to a windows share):

$ sudo umount /mnt/win/WinDrive

- Then, just to avoid any surprises, recreat the directory:

$ sudo rmdir /mnt/win/WinDrive 

(you may get an error 'device is busy'. If you are getting it then it is most likely that  following steps would not work).

$ sudo mkdir /mnt/win/WinDrive

- Finally, mount them back:

$ sudo mount -a

At this point you should be able to see your windows shares

---

### Post by spawnlcd on 2007-10-27
Thanks for the solution petervn1. It works now!!! :)


However, the problem comes back when I reboot the server. But, you solution seems to resolve the issue. Is this a bug?

Rafael

---

