---
title: "Samba - how do I share folders the REALLY easy way?"
date: 2006-07-07
forum: General Help
---

### Post by CodyJarrett on 2006-07-07
Hi,

I've tried countless smb.conf-setups and I've read many threads and guides, but I've yet to come up with a solution...

I just want to share folders between two Ubuntu Dapper machines connected to the same router.

I don't want any logins or other security settings - My router has a built-in firewall.

And I want to be able to browse the shares with Nautilus.

I really really appreciate any help with this. :confused: :confused: :confused:

---

### Post by stimpsonjcat on 2006-07-07
you only need samba if you want to share folders with windows machines. if both your computers run ubuntu you can use nfs.
click System >> Administration >> Shared Folders >> Add >> Share with nfs

---

### Post by CodyJarrett on 2006-07-07
> **stimpsonjcat said:**
> you only need samba if you want to share folders with windows machines. if both your computers run ubuntu you can use nfs.
click System >> Administration >> Shared Folders >> Add >> Share with nfs

thanks, but there's no option to share with NFS. Maybe I've messed something up?

---

### Post by scxtt on 2006-07-07
you have to install NFS packages ...

nfs-common
nfs-kernel-server
[ maybe portmap ]

and i've got samba working w/o it asking me for a p/w every time ... i think all i did was "$:> smbpasswd" one time ... now all i do is enter "smb://192.168.1.101/xubuntu_share" anytime i want to use the samba share (set the share up in xubuntu of course) ...

---

### Post by Herman on 2006-07-07
The REALLY easy way? Secure too? Between Ubuntu computers sharing a router? 
What the others have already suggested will probably be alright, but here's a Web-page about SSH Networking if you would like to see it. SHH Will take ten or fifteen minutes to set up the first time though. You will need to log in each time you want to set up the connection again though. 
If you are interested in taking a look at SSH, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p11.htm").

---

### Post by CodyJarrett on 2006-07-07
> **scxtt said:**
> you have to install NFS packages ...

nfs-common
nfs-kernel-server
[ maybe portmap ]

and i've got samba working w/o it asking me for a p/w every time ... i think all i did was "$:> smbpasswd" one time ... now all i do is enter "smb://192.168.1.101/xubuntu_share" anytime i want to use the samba share (set the share up in xubuntu of course) ...

thanks, that made NFS show up as an option. 
But how do I browse the network now. The NFS shares do not show up when I browse "Network Places" in Nautilus, and that is ultimately what I would like to do on both machines.

thanks for your help!

---

### Post by CodyJarrett on 2006-07-07
> **Herman said:**
> The REALLY easy way? Secure too? [*Click Here*]("http://users.bigpond.net.au/hermanzone/p11.htm").

no, not secure - just as easy as possible. Like I wrote:

"I don't want any logins or other security settings".

I just want to add shared folders and immediately be able to browse them in Nautilus (or another app if that is not possible).

---

### Post by scxtt on 2006-07-07
> **CodyJarrett said:**
> thanks, that made NFS show up as an option. 
But how do I browse the network now. The NFS shares do not show up when I browse "Network Places" in Nautilus, and that is ultimately what I would like to do on both machines.

thanks for your help!NFS doesn't have a "browse the network" option - it's samba that does that [i.e. "workgroup"] ... if you want to access an NFS share you'd have to specify the IP of the box you're getting the share from ... so if you're sharing a folder on 192.168.1.100 (lets say your home folder) - you would do this on the box you want to use to connect to that share:
[indent]mount 192.168.1.100:/home/CodyJarrett /media/nfs_mount[/indent]of course this is just an example, some tweaking is probably in order (i.e. an /etc/fstab entry if you want it done on boot) ...

it may seem difficult or overwhelming, but it's not ...

---

### Post by nix4me on 2006-07-07
Use the howto on the wiki for nfs.

All you do is set the share, and then mount the share on the client side.  Its really easy.

Example:
Right click a folder on server side and select share with NFS (lets call it photos).
on the client side:
mount ipaddress:/home/username/photos /mnt/photos

Thats it.  Of course the dir /mnt/photos must exist.

the wiki entry is here:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

nix4me

---

### Post by nashjc on 2006-07-07
See my posts #4 and #5 in "Samba net(not)working" under Networking for manual setup. 

I've been finding "Shared folders" not quite working. Seems not to activate samba. However, I may have got machine in unstable state.

JN (nashjc)

---

### Post by rso on 2006-07-10
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

really easy and it works for me (even though without the DNS)

---

