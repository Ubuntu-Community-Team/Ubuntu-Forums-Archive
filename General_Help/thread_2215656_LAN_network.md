---
title: "LAN network"
date: 2014-04-07
forum: General Help
---

### Post by stephenbbb on 2014-04-07
please, refer me to instructions on how to setup a home network where after logging in each user sees the same home dir?

this is the usual setup in a company or university. regardless which machine you login you see your files.

I have 1 desktop, 2 laptops and 2 tablets (these do not have ubuntu for now :-) 

thank you

---

### Post by CaptainMark on 2014-04-07
Do you have a server? A NAS (network attached storge) drive will do. Without one this all becomes kind of pointless. Some routers will let you plug in a hard drive to act as a NAS drive. Thats your first step, then to let us know what OS the server is running and the nature of its filesystem

---

### Post by hardkhora on 2014-04-07
As CaptainMark stated, you'll need something to act as an always on shared path, An HD in a router, or a computer that you can use to share out file space. Once you have one of those you'll need to point your home directories at that path on each of your devices, excluding your tablets but you can use ES Explorer if you're on Android to be able to access your files over the WiFi. Do you need help with changing your home directory path?

---

### Post by SeijiSensei on 2014-04-07
The usual method in *nix networks is to store the users' home directories on a common server as the other posters described.  If you don't have Windows clients, you should use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").  With a mix of Windows and Linux clients, you can run NFS and [Samba]("https://help.ubuntu.com/community/Samba") in parallel as I do here.

In broad outlines, you would create the users on the server, then export /home.  On the clients you would mount that exported directory as /home  during boot with an entry in the client's [/etc/fstab]("https://help.ubuntu.com/community/Fstab") like
```
server:/home  /home  nfs  defaults 0 0
```

Now here's where things get tricky.  The standard Ubuntu desktop doesn't start the network at boot; it's usually started by the user after the desktop appears.  However if there is no network, then the machine cannot mount /home, and the users can't see their desktops.  The solution for this is to start the network at boot.  You do this by editing the file /etc/network/interfaces.  Ethernet connections are [pretty easy]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing") to configure this way; for wireless, take a look at [this thread](http://ubuntuforums.org/showthread.php?t=202834&page=46).

For all this to work the users need to have identical copies of the server's /etc/passwd and /etc/group, so their user IDs are identical on all systems.  On small networks like yours, I'd consider using [NIS as the authentication method]("http://rahulporuri.blogspot.com/2012/06/installing-nis-nfs-on-ubuntu-1204.html").  Even easier, for just a couple of machines, is to create the users on the server first, then copy /etc/passwd, /etc/group, and /etc/shadow to all the clients. You'll have to do this every time you add a user though.  NIS provides that synchronization at the cost of additional complexity.

---

### Post by HermanAB on 2014-04-08
Just google for 'linux nfs home' and you will get a gazillion howto guides.

---

### Post by stephenbbb on 2014-04-08
SeijiSensei,
pls clarify 'export /home'. if I export it as an envir variable on the server then the clients know nothing about it. the local IPs are reserved, so is it possible to use 
server:192.168.0.101 /home nfs defaults 0 0

also pls confirm I do not need special devices like the top posters recommend. I want to use the desktop as the server.
Thanks a lot.

---

### Post by SeijiSensei on 2014-04-08
"Export" in this case refers to the NFS server "exporting" shares to remote clients.  The file where the shares are defined is actually called /etc/exports. Read the documents I linked to above, particularly [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo).

It's not related to the "export" command in the bash shell.

And, no, you don't need any special devices.  You can make the desktop be your server.  Try installing **nfs-kernel-server** on the desktop, and **nfs-common** on another machine.  Figure out how to export a share on the desktop and mount it on a client.

---

### Post by hardkhora on 2014-04-08
As SeijiSensei said, no special setup if you don't want it but the server will always need to be on, which is why it is nice to have a NAS to save on the power bill. I've found routers at second hand stores, such as good will that have the USB port for less than $10 that would let you plug in a USB HD, or if you have a big enough flash drive (although it might be slow if you have a lot of activity).

---

