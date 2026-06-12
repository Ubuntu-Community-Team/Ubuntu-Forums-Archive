---
title: "Can't mount Windows share with Nautilus through SMB"
date: 2018-05-20
forum: General Help
---

### Post by lazarus67 on 2018-05-20
Hello everyone

I have 2 problems with my new Ubuntu v18.04 install.

First, i'm having a hard time to mount a Windows shared folder with Nautilus through SMB, it always prompt me for password when the share is not protected or anonymous connection failed.The shared folder is host a Windows 7 and is not password protected, should be really simple. But, if I open a terminal and run smbclient //hostname/share, it works. So it look like the problems is only with Nautilus.

The second problem is Nautilus doesn't shows me any PC in my network. If I use arp or nmap or zenmap, they are all there and i can ping successfully all of them.

I really need your help!

Thank you!

---

### Post by lazarus67 on 2018-05-22
up!

---

### Post by yancek on 2018-05-22
Are both Ubuntu and windows 7 installed on separate partitions on the same computer? 
Or is one of them installed using virtual software?
Or are they on different machines on the same network?

---

### Post by lazarus67 on 2018-05-22
Both are on different computer on the same network, no virtualization!

---

### Post by lazarus67 on 2018-05-22
I've found that if i add this line in the file ***"/etc/samba/smb.conf"***, I can now see all my PCs in the network, but cannot access to them :
    > client max protocol = NT1
***But after that change, smbclient doesn't work anymore***

To make smbclient works again, i have to specify the max client protocol (-m option) which overrides the one written in the smb.conf file
> smbclient //hostname/share -m SMB2

Here are the lines I've added from the original smb.conf file :
> 
[global]

#Added by me
client max protocol = NT1
    security = user
    map to guest = Bad User
client use spnego = no



I can't still mount anything in Nautilus or Thunar!

---

### Post by yancek on 2018-05-22
The link below gives a pretty detailed description of setting up Samba on Linux.  Check the sections Manual and Automatic mounting.  Do you have an entry in the /etc/fstab file?  The second link below is specifically Ubuntu.

[https://wiki.archlinux.org/index.php/samba](https://wiki.archlinux.org/index.php/samba)

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by lazarus67 on 2018-05-22
I was looking for something more user friendly like Windows does : Browse network > connect to the host > see all shares > select the share you want.

I am now able to connect a smb drive with Nautilus or Thunar. But in a first time, I have to know what is the shared folder name I want on the hostname.

My new global section of my smb.conf file :
> 
[global]

#Added by me
   client min protocol = SMB2
   client max protocol = SMB3
   client use spnego = no


The problem with this solution is, I still can't see all PCs in my network.

I've found a workaround with nmap (ping scan) to list all PCs in my network. Then, to find all shared folder on a PC, i'm running this command:> smbclient -L //PC_NAME

Is there any shorter way to do the same as the workaround?

Thank you

---

### Post by yancek on 2018-05-23
I've never used Samba primarily because I don't have any use for windows so doubt I'll be much help.  Have you set up sharing on your windows computers?

---

### Post by lazarus67 on 2018-05-23
Yes the share is well set on Windows. All my PCs and mobiles (iOS and Android) can discover successfully the network, see all shared folders from a host, and open the share.

Why my linux PC is the only one which can't discover the network with a GUI (Nautilus, Thunar, Dolphin or Gigolo) ?

---

### Post by Morbius1 on 2018-05-23
Rock meet hard place:
> **Morbius1 said:**
> 
[COLOR=#0000cd]**But**[/COLOR] ... there is a reason  why Samba set the client max to SMBv3.11. Windows 10 and many other SMB /  Samba servers have disabled SMBv1 for security purposes. If the Linux  client can only use SMBv1 no connection is possible to these servers.

So we as desktop users are [COLOR=#0000cd]**between a Rock:**[/COLOR]

If you set "client max protocol" back to NT1 the Linux client will be  able to find all the servers but will not be able to connect to any that  disabled SMBv1.

[COLOR=#0000cd]**And a Hard Place:**[/COLOR]

If you allow the default of SMBv3.11 it will not be able to discover the servers but it will be able to connect to them.

[COLOR=#0000cd]_**NOTE**: This is not a host name resolution problem - it's a host browsing ( discovery ) problem._
[/COLOR]
** You can still connect to the server by name but you have to know it's  name and you must connect to to it explicitly by that name .. as in ...  smb://hostname or use Connect to Server in Nautilus.

As I stated in a mini rant later in that topic the way samba is currently configured today it works seamlessly in an all Linux network not one with Windows. The ultimate solution in my mind is with one of two paths:

[1] Samba would need to incorporate the WS-Discovery mechanism that Windows uses to find other Windows hosts.
[2] Windows would have to enable the ability to "register" its SMB servers via mDNS they way Linux and macOS does.

If it were a race [2] would win since Microsoft has the talent, resources, discipline, and ( if / when convinced to do so ) the desire to make it happen.

---

### Post by lazarus67 on 2018-05-24
Oh well, like you said, we are between a Rock! I guess the only thing we can do is to wait for a fix (Samba or Windows).

---

