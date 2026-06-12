---
title: "Connect to my friend's computer"
date: 2006-11-05
forum: General Help
---

### Post by GabrielWolff on 2006-11-05
Hey, I'd like to be able to connect to my friend's computer. He uses Ubuntu and I use Xubuntu. I'd like to be able to put/copy files on/from his machine and the other way around.

How do I do that?

Gabriel

---

### Post by taurus on 2006-11-05
Best way is to set up a ftp server either on your machine or his machine.  Then, you can upload or download whatever you want between two machines.

---

### Post by GabrielWolff on 2006-11-05
If I got a server on *my *machine, will he each time have to connect to my ftp server from *his *machine for me to be able to transfere files?

Is there a possibility of allowing each of us to access the other's computer when it's working, but when the other one is not physically at his machine?

G

---

### Post by taurus on 2006-11-05
Then, you are talking about NFS then.  It allows you to mount his drive on your machine or vice versa so it will always available to you as long as his machine is on...

[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

### Post by GabrielWolff on 2006-11-05
Bingo, that's what I meant. Thanks, and I'll surely be back with 1.000 further questions :-)

Gabriel

---

### Post by elettronicha on 2006-11-05
> **GabrielWolff said:**
> Hey, I'd like to be able to connect to my friend's computer. He uses Ubuntu and I use Xubuntu. I'd like to be able to put/copy files on/from his machine and the other way around.

How do I do that?

Gabriel
You forgot to mention where your friend is located, whether in your LAN or not.

---

### Post by GabrielWolff on 2006-11-05
No no, we're just two users in two different homes, no LAN connecting us.

Is the NFS answer still good?

Gabriel

---

### Post by taurus on 2006-11-05
> **GabrielWolff said:**
> No no, we're just two users in two different homes, no LAN connecting us.

Is the NFS answer still good?

Gabriel
It's the best as long as both computers are connected to the net...

---

### Post by bettlebrox on 2006-11-05
I would not use NFS over an unsecured network (nor consider using ftp) as it is not a secure protocol and more easily hacked. U could look into tunnelling NFS over ssh:

[http://www.samag.com/documents/s=4072/sam0203d/sam0203d.htm]("http://www.samag.com/documents/s=4072/sam0203d/sam0203d.htm")

The main problems with NFS are that it relies on the inherently insecure UDP protocol, transactions are not encrypted, hosts and users cannot be easily authenticated, and its difficulty in firewalling. ... These principles may also be applied to any UNIX server with ssh installed. This article assumes basic knowledge of NFS and firewalling for Linux.

And here's an HOWTO on tunnelling NFS over SSH on Debian (which is what Ubuntu is based on):

[http://www.howtoforge.com/nfs_ssh_tunneling]("http://www.howtoforge.com/nfs_ssh_tunneling")

Plus, enabling SSH will allow you to use other tools to copy files such as sftp, scp, konqueror ...

Best O' Luck! :)

---

### Post by hoowe on 2006-11-05
Why not just use nautilus or your file manager in kde, to connect to each other with ssh? In Ubuntu you could use 'Places -> Connect to Server' and then select ssh connection and your friends ipaddress. I could recommend you to create an extra user that you connect as so you don't gain "full access" to each others filesystem.

/H

---

### Post by GabrielWolff on 2006-11-05
I thought about that. But *thunar*, Xubuntu's file manager is seemingly missing that option. Does anyone know better?

And another thing: My friend is using a router (maybe my statement about our LANs earlier was wrong...:???: ), does that affect my plans? Will I gain access to *any* computer using that router. Hardly, ah? 

And how do I find out his/my IP?

Gabriel

---

### Post by Gaweph on 2006-11-16
Ubuntu Center allows for this.  If you or your friend install ubuntu center, then it has uploading and downloading capabilities, this seems to do what you are looking for.

---

### Post by GabrielWolff on 2006-11-17
> **Gaweph said:**
> Ubuntu Center allows for this.  If you or your friend install ubuntu center, then it has uploading and downloading capabilities, this seems to do what you are looking for.

Where do I get that from? I looked in Synaptic (on my friend's computer, I don't exactly know which repositories he has listed) and could find nothing...

G

---

