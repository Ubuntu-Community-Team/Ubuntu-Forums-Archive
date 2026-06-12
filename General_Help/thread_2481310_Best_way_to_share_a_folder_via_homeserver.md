---
title: "Best way to share a folder via homeserver?"
date: 2022-11-25
forum: General Help
---

### Post by Sonador on 2022-11-25
Hello guys, it is a trivial task, but I don't know exactly the terms I am looking for or the direction...


[LIST]
[*]I got a **server** (Raspbian OS) and** two desktop** PC (Kubuntu). 
[*]I want to **share a folder** between the 2 PC with the help of the homeserver. 
[*]The folder should be accessible via **GUI** apps like Dolphin, Gimp etc. 
[*]The question: what am I looking for? Is it called a fileserver? Do I have to install something like samba (but I think it is need only for windows)? Or will be ssh access sufficient? But is ssh good for GUI apps and for ~permanent connection (I have experience with it only from CLI)... 
[/LIST]

---

### Post by yancek on 2022-11-25
Sharing files on a local network between Linux systems can be done with nfs (network file system) which is the default for Linux.  SSH could also be used.  The link below explains installing and setting up NFS.

[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04)

---

### Post by ian-weisser on 2022-11-25
ssh access is often sufficient.

Most File Managers will happily connect to a server using ssh, presenting the server as just another volume.

Use the File Manager's "connect to server" option.

---

### Post by Morbius1 on 2022-11-25
So just to see what it would take I installed Raspberry Pi OS for Desktops on a VBox guest to do all this.

Samba was already installed on the Pi OS on my my system. If it is not on yours install it:
```
sudo apt install samba
```

Avahi is already installed on my system. If it is not on yours install it:
```
sudo apt install avahi-daemon
```

I edited /etc/samba/smb.conf and created a samba share of my Public folder by defining a share at the bottom of the file:
```
[Public]
path = /home/tester/Public
read only = no
guest ok = yes
force user = tester
```

Then I restarted samba:
```
sudo service smbd restart
```

Then I went to Kubuntu 22.04, opened a terminal, and ran:
```
dolphin smb://raspberry.local
```

This displayed the share I defined:
[ATTACH=CONFIG]291301[/ATTACH]

Drilled down to show the contents of the share and added a file:
[ATTACH=CONFIG]291302[/ATTACH]

To automount and made sure cifs was installed on Kubuntu:
```
sudo apt install cifs-utils
```
Created a mount point at /mnt/SMBPi.

Then edited /etc/fstab in Kubuntu and added an automount declaration:
```
//raspberry.local/Public /mnt/SMBPi cifs defaults,guest,uid=tester,noauto,x-systemd.automount 0 0
```
Made systemd happy by running a couple of commands:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

Then went to /mnt/SMBPi in Dolphin to see what's what:
[ATTACH=CONFIG]291303[/ATTACH]

It literally took less time to do all this than it did to post this response.

---

### Post by Sonador on 2022-11-26
That's cool, thank You guys for replies! I think I am going to start easy with ssh and see how it fill my needs.

---

### Post by HermanAB on 2022-11-28
Yup, as suggested above, I have years ago given up with overly complex bug ridden insecure networked file systems and just use SSH for everything.

---

### Post by TheFu on 2022-11-28
> **Sonador said:**
> That's cool, thank You guys for replies! I think I am going to start easy with ssh and see how it fill my needs.

So, ssh is the core tool, but there are sftp:// and sshfs methods.  All ssh-based methods will use ssh-keys, if you set them up, which makes the access more secure AND more convenient.

For seamless access, where the remote storage feels like local storage, use NFS.  NFS is system-to-system and honors normal Unix permissions, ACLs, and most expected users/groups.  The trick is to either use identical uid and gid (the numbers for the users and groups) so the users and groups are what you want across all storage.  The uid/gid are what matter, not the username/groupname to NFS.  There is a way to map usernames between systems, but I've never used that successfully.  To see the numbers for the uid/gids, the 'id' command should be used on all NFS clients and servers. With NFS, chmod and chown work.

Most Linux file managers support the sftp:// URL.  Once ssh is installed on the client system and the ssh-server is installed on the remote system, you can use almost any file manager with the IP or DNS name to access files on the remote systems.  This access is a little clunky, due to the sftp/ftp interface used.  If you are copying files between systems, this sftp method is fine.  

sshfs is a user-to-server way to mount remote storage that end-users can setup themselves. As with all ssh methods, provided that ssh-keys are used, the connection is considered secure enough for use over the internet without any VPN required.

If you want to directly edit files, you'll want NFS probably, but sshfs can be used almost always too.  sshfs doesn't support all the same permissions that NFS does, but it is likely you won't notice any issues.  Just remember to umount/fusermount -u the sshfs storage when done to avoid corrupted files from stale file handles.

On the same LAN, by far, NFS is the best option between Unix-like systems. NFS has been very stable for decades, but there are odd fringe issues from time to time.  NFS definitely works better than the alternatives for media sharing on a LAN.  In theory, CIFS should work as well, but for unknown reasons, it doesn't.  The Kodi forums have a few posts about CIFS shared storage stuttering each week.

CIFS/samba is a limited subset storage protocol.  It allows some interesting overrides for end users who don't want or need to know about Unix permissions.  I consider it lazy, but if you just need something to work, those overrides can be helpful if you trust everyone on the LAN.

Setting up NFS is about 5 steps (3 on the server and 2 on the clients) and then it "just works" and is likely to work for decades.  NFS can be secured sufficiently to allow use over the internet through NFSv4 encryption and Kerberos, but setting those up are hassles.

sshfs is something I use ad hoc.  Usually when I need to process data on a remote system, but don't want to setup the programs needed to process the data AND I don't have NFS working or I'm not on the same LAN.

[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs) is the official documentation for setting up NFS on a server and clients.  NFS is NFS is NFS, so the distro doesn't matter.

---

### Post by Sonador on 2022-12-14
> **TheFu said:**
> So, ssh is the core tool, but there are sftp:// and sshfs methods.  All ssh-based methods will use ssh-keys, if you set them up, which makes the access more secure AND more convenient.

For seamless access, where the remote storage feels like local storage, use NFS.  NFS is system-to-system and honors normal Unix permissions, ACLs, and most expected users/groups.  The trick is to either use identical uid and gid (the numbers for the users and groups) so the users and groups are what you want across all storage.  The uid/gid are what matter, not the username/groupname to NFS.  There is a way to map usernames between systems, but I've never used that successfully.  To see the numbers for the uid/gids, the 'id' command should be used on all NFS clients and servers. With NFS, chmod and chown work.

Most Linux file managers support the sftp:// URL.  Once ssh is installed on the client system and the ssh-server is installed on the remote system, you can use almost any file manager with the IP or DNS name to access files on the remote systems.  This access is a little clunky, due to the sftp/ftp interface used.  If you are copying files between systems, this sftp method is fine.  

sshfs is a user-to-server way to mount remote storage that end-users can setup themselves. As with all ssh methods, provided that ssh-keys are used, the connection is considered secure enough for use over the internet without any VPN required.

If you want to directly edit files, you'll want NFS probably, but sshfs can be used almost always too.  sshfs doesn't support all the same permissions that NFS does, but it is likely you won't notice any issues.  Just remember to umount/fusermount -u the sshfs storage when done to avoid corrupted files from stale file handles.

On the same LAN, by far, NFS is the best option between Unix-like systems. NFS has been very stable for decades, but there are odd fringe issues from time to time.  NFS definitely works better than the alternatives for media sharing on a LAN.  In theory, CIFS should work as well, but for unknown reasons, it doesn't.  The Kodi forums have a few posts about CIFS shared storage stuttering each week.

CIFS/samba is a limited subset storage protocol.  It allows some interesting overrides for end users who don't want or need to know about Unix permissions.  I consider it lazy, but if you just need something to work, those overrides can be helpful if you trust everyone on the LAN.

Setting up NFS is about 5 steps (3 on the server and 2 on the clients) and then it "just works" and is likely to work for decades.  NFS can be secured sufficiently to allow use over the internet through NFSv4 encryption and Kerberos, but setting those up are hassles.

sshfs is something I use ad hoc.  Usually when I need to process data on a remote system, but don't want to setup the programs needed to process the data AND I don't have NFS working or I'm not on the same LAN.

[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs) is the official documentation for setting up NFS on a server and clients.  NFS is NFS is NFS, so the distro doesn't matter.

Sorry for late respond, I didn't expected more replies. It looks like I don't have notifications enabled. Meanwhile I did further research and it did lead to some doubts, but you have just confirmed my opinion, so thanks. I am going to end up with **NFS**. I am not happy it is not encrypted transfer but at home it is really not necessary. I could also go with **Samba**, it is up to personal taste, the "no" for me is, Samba doesn't support case sensitive "operations" (as it comes from M$ Windows). **Sshfs** looked perfect at first glance, but it is not under active development anymore, it still might work good, but I want something with future. **Sftp** - I had troubles with Dolphin or Thunar folder bookmarks, after reboot, it failed to recognize the folders (they appeared empty)... **NFS** is easy to setup and for sharing image album (with digiKam database) - probably the best choice...

---

### Post by TheFu on 2022-12-14
NFSv4 can support Kerberos authentication and AES encryption, but that is harder to setup.  There's a guide on ubuntu.com if you want it.  Both sides of the client/server need to support the authentication and encryption.  [https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs) ... scroll halfway down the page to see the Kerberos stuff under "Advanced".

---

### Post by SeijiSensei on 2022-12-15
If you set up a point-to-point virtual private network with OpenVPN, then you can access the remote machine with NFS but still have the transaction be encrypted. All my remote servers connect over OpenVPN tunnels.  Seems like overkill on a home network to me though.

[https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

---

### Post by Sonador on 2022-12-16
> **SeijiSensei said:**
> If you set up a point-to-point virtual private network with OpenVPN, then you can access the remote machine with NFS but still have the transaction be encrypted. All my remote servers connect over OpenVPN tunnels.  Seems like overkill on a home network to me though.

[https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

Thanks, and yes, I really don't need the encryption right now for home network, but maybe in future I might need it, and now, You know, it is good for learning purposes :) That's great to have OpenVPN as a second option for security, I am just not sure If I can use it when I am already connecting to the internet through VPN (proton).

---

### Post by TheFu on 2022-12-16
> **Sonador said:**
> Thanks, and yes, I really don't need the encryption right now for home network, but maybe in future I might need it, and now, You know, it is good for learning purposes :) That's great to have OpenVPN as a second option for security, I am just not sure If I can use it when I am already connecting to the internet through VPN (proton).

It would depend on how.  How do you connect to home over ssh/sftp/scp/rsync/sshfs/x2go when you are away? Seems like the same method would be needed for any inbound VPN.

I used to use openvpn, but switched to wireguard last year. It is another option, typically easier to setup for small needs than openvpn, but it doesn't have the same proven time in service that openvpn or the *Swan IPSec tools bring.

---

