---
title: "Cannot copy files from windows to Ubuntu using Network Servers"
date: 2007-01-13
forum: General Help
---

### Post by MJSOnline on 2007-01-13
Hi all.  I can not copy my files from my Windows XP laptop to my Ubuntu system.  I am using the Places > Network Servers > option as I did in 6.06, but under Edgy 6.10 it does not work and will not connect.

Can  anyone please explain why this does not work and poss  walk though or howto?  Thanks. M

---

### Post by MJSOnline on 2007-01-13
BUMP!!  Anyone got any ideas? Thanks. M

---

### Post by peterLinux on 2007-01-13
You don't give much information, so a general answer:

Go to the command line and see if you can get smbclient to work.

Also check the basics:
Can you ping to other winBlows laptop from your Ubuntu?

---

### Post by SuperMike on 2007-01-13
Several routes are possible:

* Install WinSCP on Windows (free download from the web). Then, install OpenSSH Server (sshd, essentially) on your Ubuntu. Then, using WinSCP, connect to your SSH Server and transfer files.

* Build a Windows share on your Windows system. Let's say it's at IP address of 192.168.32.32 and the share is called 'myshare'. Mount it on Ubuntu like so:

From Windows, let's assume you did Start, Run, lusrmgr.msc, and edited your Local Administrator account password to be something like 'superAdmin100' for the example below.

From Ubuntu, do:
$ sudo apt-get update
$ sudo apt-get install smbclient
$ sudo mkdir /mnt/windows
$ sudo mount -t smbfs -o 'username=administrator,password=superAdmin100,workgroup=192.168.32.32,rw'  //192.168.32.32/myshare   /mnt/windows

And now, using Nautilus, you should be able to go to /mnt/windows and be able to read/write your Windows file share. There's also an /etc/fstab technique for this too so that this works on every reboot, although I don't have it handy right now -- left that instruction at my office.

* Otherwise, the whole problem might just come down to the fact that your Ubuntu network control panel might not have the proper DNS settings like your Windows box has and therefore none of the names are translating. You can find out your Windows client DNS settings by typing 'ipconfig /all' at a command prompt on Windows. Then, you can set those on your Ubuntu network control panel. These actually get written into a file called /etc/resolv.conf with something like:

search myoffice.domain
nameserver 10.1.23.22
nameserver 10.1.24.23

Then, bounce your networking service:

$ sudo /etc/init.d/networking stop
$ sudo /etc/init.d/networking start

and it should have your DNS settings set properly.

---

### Post by MJSOnline on 2007-01-14
Hi all. Thanks for the info.  Would not having the samba client installed give the the error of " cannot find/connect //smb" ?  Thanks again. M

---

### Post by MJSOnline on 2007-01-14
> **MJSOnline said:**
> Hi all. Thanks for the info.  Would not having the samba client installed give the the error of " cannot find/connect //smb" ?  Thanks again. M
BUMP!! Anyone got the answer?  Thanks. M

---

### Post by SuperMike on 2007-01-15
$ sudo apt-get install smbclient samba-common smbfs libsmbclient samba

---

