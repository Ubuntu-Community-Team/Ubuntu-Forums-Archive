---
title: "How can I get Samba to work ?"
date: 2013-03-21
forum: General Help
---

### Post by Tim036 on 2013-03-21
Ubuntu 12.04 64 bit

I'm accessing two Raspberry Pi, one other an Ethernet network and the other over a WiFi network using 'ssh'.

A friend told me with Samba I could easily use the files which were on those Rasberry Pi's.

But I've no idea how to go about it.

has anyone done this ?

If so, in very simple terms what do i have to do to get it working ?

A very curious ,

Tim

---

### Post by Cheesemill on 2013-03-21
There's no need to go down the Samba route as you already have an ssh server installed on your Pi's.

You can copy files around either by using the scp command from a terminal or opening your file manager and going to File > Connect to Server.

---

### Post by Kirboosy on 2013-03-21
I agree with Cheesemill, but if you end up using a non-Linux machine and want to access files from the Pi you will need samba.

Here is a quick and dirty [guide ]("https://help.ubuntu.com/community/Samba/SambaServerGuide")to Samba.

---

### Post by Cheesemill on 2013-03-21
> **Caboose885 said:**
> I agree with Cheesemill, but if you end up using a non-Linux machine and want to access files from the Pi you will need samba.

Not really.

If you need to access files over an ssh connection from a Windows machine you can just use [WinSCP]("http://winscp.net/eng/index.php").

---

### Post by Kirboosy on 2013-03-21
True, WinSCP is a wonderful tool but if you don't like or can't install additional programs to achieve SCP then Samba will be helpful.

---

### Post by Tim036 on 2013-03-21
> **Cheesemill said:**
> There's no need to go down the Samba route as you already have an ssh server installed on your Pi's.

You can copy files around either by using the scp command from a terminal or opening your file manager and going to File > Connect to Server.

I can see the raspberry ikon using file manager , but there is nothing I can do after that.

scp is a mystery...

many thanks for responding.

a puzzled,

Tim

PS I use Linux.   Does winscp run on Windows ?  Not too keen on windows, very keen on Ubuntu.

---

### Post by Kirboosy on 2013-03-22
WinSCP is a windows only tool. Since Linux has native SCP support WinSCP is unneeeded. [Filezilla ]("http://filezilla-project.org/")is a alternative to WinSCP that runs on Linux. (You can apt-get install it) However like Cheesemill said above SCP is built into the File Manager in ubuntu so really Filezilla is not needed for this situation. 


(I am doing this from Nautilus)
Open File Manager->File->Connect to Server
**Server**: <IPADDRESS OF PI> **Port**:22 (unless you changed the default port of SSH)
**Type**: SSH
**Folder**:[I]What directory you want to mount 
[/I]**Username**: useraccount on pi
**Password**: password on that account.

[Guide for SCP through command line]("https://help.ubuntu.com/community/SSH/TransferFiles")
[SSHFS Guide]("https://help.ubuntu.com/community/SSHFS") -- For mounting an SSH connection to the local directories. (command line)

If that does not work make sure that your ssh server is installed/running, firewalls have appropriate rules, etc.

Hopefully that information helps.

---

