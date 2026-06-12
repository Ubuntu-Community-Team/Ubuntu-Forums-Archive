---
title: "Simple File Server"
date: 2006-07-02
forum: General Help
---

### Post by penguinmaster on 2006-07-02
Hey guys,

   Just wondering if anyone can give me some suggestions on how to setup a simpel file server.  Basically what I'm looking for is a way to have a folder in my home folder  on my laptop that is connected back to my desktop computer.  Also I would like to be able to login and use that through the web when not at home.  I've read suggestions about FTP, but I'm not sure if that's what I want.  Basically I just want a way to store stuff on my desktop for backups and storing big files that I don't use that often.  Any suggestions would be helpful.  I would also prefer a GUI interface for it, not sure what is out there.  Thanks in advance!

---

### Post by snowx1000 on 2006-07-02
You could always setup a samba server. Then from wherever you connect, the share would appear as a hard drive/directory.

---

### Post by penguinmaster on 2006-07-02
[QUOTE=snowx1000]You could always setup a samba server. Then from wherever you connect, the share would appear as a hard drive/directory.[/QUOTE]


With a samba server can I login to it though from outside my network.  Say, I'm at work but want to access files from my home desktop\.  Will that work?  Sorry these may be simple stupid questions, i've never setup a server like this before so I'm not sure.

---

### Post by Ctrl+Alt+Del on 2006-07-02
It will work, but i would recommend going for ftp. A simple FTP Server should do the trick. There's a Gui frontend for ProFTP which should make configuration as trivial as it can be.

---

### Post by nix4me on 2006-07-02
There are many ways to do it.  ssh, ftp or a webserver.

I would share the dir with samba for local access and then set up a ftp server to access from outside.

Are all the machine on your network linux?  If so share the dir with NFS and not samba.

nix4me

---

### Post by NeoGreen on 2006-07-02
Where could I go to see a How-To for a File Server with those specs?  I saw one for 5.10 but not for 6.06.

---

### Post by master_b on 2006-07-03
Unless you actually need the files/data on your laptop for some reason, why not just use Freenx to remotely access your home pc from your laptop?

Saves all of that data transfer/Syncing.

Bill

---

### Post by meridius on 2006-07-03
I recommend that you setup the file server using Samba.

Also, in order to access the file server remotely, I suggest installing Hamachi ([www.hamachi.cc](www.hamachi.cc)) on both your server and laptop and using samba by connecting through that. Hamachi is a VPN software that creates a secure virtual tunnel between your computers and also encrypts the traffic going through it. Go to the site and learn how to use the service.

Hamachi is also great for internet facing servers (computers connected directly to the internet without any routers). Using Hamachi, you can firewall every port and connect exclusively through the VPN.

---

### Post by airtonix on 2006-07-16
I recommend you take an extra step and stay with repository software and us openVPN instead.

hamachi central server keesp a list of hamachi networks names and ips.....not controlled by you. if your ok with this, then please be aware that openVPn doesn't need this as far as im aware.

---

