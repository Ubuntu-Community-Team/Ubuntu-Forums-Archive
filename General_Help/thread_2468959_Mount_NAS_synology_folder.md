---
title: "Mount NAS synology folder"
date: 2021-11-15
forum: General Help
---

### Post by uros-likar on 2021-11-15
I have a Synology NAS with some shared folders on it. Those folders use samba share I think, so windows can see them on the network. I can reach those folders using samba but I'd like to mount them via SSH. I google it how to do it and I read that you need to enable NFS rule. I found that NFS settings but I don't understand what to do with it. 

1. First of all you have hostname or IP, What I need to insert there? I tried to insert NAS IP. 
2. Then you have Privilege which is clear. 
3. After that you have "Squash" with options: no mapping, Map root as admin, Map root guest, Map all users to admin, Map all users to guest. What exactly is this and what I need to choose??
4. Last drop down option is Security with options: AUTH_SYS, Kerberos authentication, Kerberos Integrity, Kerberos privacy. Probably I leave the first option?

I though that permissions are defined to NAS user and I insert some kind of username and password like on windows. After all those options are set correctly, how do I connect to it and permanently mount it to a folder? 


[IMG]https://i.postimg.cc/qqWq2CgM/Screenshot-20211115-200735.png[/IMG]

Thank you for any info.

---

### Post by TheFu on 2021-11-15
I think there is some confusion.

NFS is a network storage protocol.

CIFS/Samba are network storage protocols.

ssh is NOT a storage protocol.  Ssh is a secure terminal connection.  You can run any TCP protocol through an ssh tunnel, if you like and there is an sshfs network storage protocol, but it is very slow and probably best used only over the internet, where CIFS and NFS shouldn't be used.

NFS has a server-side with settings (the Synology) and a client-side with settings, typically the /etc/fstab file.  There isn't a GUI to modify the fstab.  ssh isn't needed between these systems.
> 3. After that you have "Squash" with options: no mapping, Map root as admin, Map root guest, Map all users to admin, Map all users to guest. What exactly is this and what I need to choose??
Those are each questions for which only you can select the answer.  I care about security, so I would never allow a client root account to have control over my NAS storage. I'd want to manage those settings on the NAS itself, but if you aren't good at Unix permissions with multiple userids accessing the storage, if would be likely to cause issues and not being able to fix stuff from the client system could be seen as a hassle by some users.  Typically, on Unix NFS servers, the root account from all clients gets mapped to "nobody" - which means it has less privilege on the storage than a normal userid. The choice is yours.  I would never map all users to guest or a single userid either. That sorta defeats the reason to use NFS ... except the NFS is usually a little faster than CIFS ... though the 5.16.x kernels just added some performance code for faster kernel-mode CIFS support a few days ago.

>  4. Last drop down option is Security with options: AUTH_SYS, Kerberos authentication, Kerberos Integrity, Kerberos privacy. Probably I leave the first option?
If you don't run Kerberos infrastructure, then you want to not choose any of those options.  NFSv4 supports Kerberos system-to-system authentication tokens along with AES encrypted connections, which would be considered sufficiently secure to have NFSv4 over the internet.  Without those two choices setup, NFS v3/v4 have only the security provided by strict control of IPs from the clients and exports to specific clients by the server along with specific userid/groupid controls.  Their example of using a /24 for the sharing is extremely lazy.  If you let me visit your home and hope on the network, I'll have access to everything on the NFS server quickly if settings like that are used.  I export specific shares to specific clients, not the entire subnet.

From an NFS client, if you run
```
$ showmount -e romulus
```
  where "romulus" is either DNS or /etc/hosts or an IP address to the NFS server, it will display the available mounts for that client along with the other systems allowed to mount that same share.

With that information, you can create a mount line in the /etc/fstab file.  Something like this:
```
romulus:/raid/media/Music  /M   nfs   nconnect=4,proto=tcp,rw,async  0 0
```
1 line for each share you want to access.  Then run
```
sudo mkdir /M  # the mount point must exist before it can be mounted!@!!!
sudo mount -a   # this will mount any storage in the fstab that isn't mounted

```and Bob's your uncle.
```
cd /M 
ls
```
See the files.  Normal Unix permissions and ownership apply.  Different userids from different nfs client systems need to have the same uid/gid numbers to be treated as the same username/userid.  The '**id**' command shows those numbers.  Make them consistent across all your systems to be happy.

If that doesn't work, try a test mount command. This is only active until the reboot or umount.
```
sudo mount -t nfs  romulus:/raid/media/Music  /M
```
That's without the other options, but should work well enough.

[https://kb.synology.com/en-us/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://kb.synology.com/en-us/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS) has more detailed steps.  I saw something about NFSv4 not being the default on Synology.  The nconnect option is NFSv4.1, I think. It is relatively new on Ubuntu, though NFSv4 has been around 15 yrs.

---

### Post by uros-likar on 2021-11-16
Thanx for the info.

No luck for now. I'm trying with different permissions and mount using:

[FONT=monospace][COLOR=#000000] sudo mount -t nfs 192.168.0.13:/volume1/Share /mnt/share/ [/COLOR]

and I always get error:
mount.nfs: access denied by server while mounting 192.168.0.13:/volume1/Share

I need to digg more into this. I'm a linux noob and I'm not familiar with a lot of stuff here :)




[/FONT]

---

