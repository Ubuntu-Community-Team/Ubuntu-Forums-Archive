---
title: "How to autofs and Samba"
date: 2013-12-31
forum: General Help
---

### Post by DeMus on 2013-12-31
Hi all,

Let me start with wishing you a very happy New Year.

As you can read in the title I am having problems to setup autofs with samba.
I have the following computers:
1) Desktop, running Kubuntu 13.10, IP 192.168.2.21
2) Laptop, running Kubuntu 13.10, IP 192.168.2.22
3) Desktop, running Windows 7, IP 192.168.2.11
4) Media player, running some kind of Linux system, IP 192.168.2.13

What I want is this:
From computer 1, I want to be able to read and write from and to shared disks in 2, 3 and 4, without any passwords or security.
From computer 2, I want to do the same
From computer 3, I want to read files in 1 (my main computer with all the data)
From the media player I want to be able to read files from computer 1

I want to use autofs because when I use a fixed mount in fstab and the other computer is switched off, my computer (nr 1) hangs because of that. Using autofs I can unmount automatically a few seconds after having used the connection.

Questions:
a) What do I need to install?
b) How do I setup Samba correctly so all my disks will be shared the right way?
c) How do I setup autofs so I can use the shared disks as if they were local disks?

I have read a lot the last couple of days and I still don't get it. I see so many things which are not completely like I want it and then it doesn't work. So no I am having some messed up conf files for Samba and for autofs.
Who can give me the correct settings for the conf files? 
As I said I read a lot and it costed me several days already and I still am not even close to the solution.  Please help me.

---

### Post by tcl2 on 2013-12-31
The first thing to do is to set up your shares on each machine with access users defined by machine since you are looking for access by computer on network rather than user on network. Each computer will use its own 'network user' to access the network shares. This should be testable by seeing them with an smb* utility or the network browser.

To use autofs access the shares, set up the autofs access files -- /etc/auto.master -- /etc/auto.cifs -- and /etc/auto.cifs.[machine name on smbfs network]

autofs.master needs only one line: "/lan /etc/auto.cifs" -- this says autofs will create a mount point at /lan for your shares as defined in auto.cifs

For auto.cifs I used  [http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs](http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs) as a resource. I had to play around a bit with mount options to get things the way I wanted them - note you can run this script to see what it feeds to autofs and this can be a handy debugging tool.

Each credentials file contains three lines with username, password, and [optionally] domain. This information is used to log in to shares for proper access. There is one file for each machine whose shares you want to access.

As for what to install: autofs and smbfs should take care of it
For "setup Samba correctly" I think the key is getting the nomenclature of machine names and share user names clearly defined. I put the machine names in /etc/hosts although I am not sure this is needed for cifs access only.
With autofs, access will be via the mountpoint/machine name/share name and share mountpoints will exist only as you use them - there is a timeout parameter you can use to set persistence. If you want permanent mounting of shares, use fstab (it can use the credential files as well if you don't want user and password in the fstab options list)

Using nfs shares might be easier. The big issue with that is to set up the user and group numbers in a consistent scheme on each machine. The smbfs or cifs security system is much more complex.

---

### Post by DeMus on 2014-01-01
Hi tcl2,

Thank you for your help. Unfortunately it didn't help me so much since you lost me in line 1 already.
I guess I need a step by step instruction how to do things or I am lost.

I noticed you are talking about a credential file, something I don't need. I want it to be open so no need to type passwords when I want to do something.
I will try to understand your answer and keep searching the net for a tutorial.
Thanks again.

---

### Post by tcl2 on 2014-01-01
sorry 'bout that

First step is to set up sharing: open up the target folder in your file browser and find its properties. There should be a share tab (at least with nautilus) that you can use to set up the necessary parameters for sharing that folder on the network

second step is to be able to access the share from another machine. You can usually do this with the file browser, too.

third step would be to set up autofs but you might want to start simple with a mount command.

There are some good 'howto's' out there for each step that provide step by step.

---

