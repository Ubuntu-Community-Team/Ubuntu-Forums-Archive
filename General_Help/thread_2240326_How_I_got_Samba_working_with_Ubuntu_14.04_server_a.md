---
title: "How I got Samba working with Ubuntu 14.04 server and Win 7"
date: 2014-08-19
forum: General Help
---

### Post by bulrush2 on 2014-08-19
I have yet to find docs that are clear, as to what name is used where. But I'll try to explain it.

My PC: Windows 7 connecting to Ubuntu VM via Putty 0.63
VM: Ubuntu 14.04LTS server (no GUI), upgraded all packages with "sudo apt-get update"

First I installed samba with these commands: 
> sudo apt-get install samba samba-common samba-libs
sudo apt-get install samba-doc samba-dev


I went to /etc/samba and moved the smb.conf file to smb.conf.bk. 

In /etc/samba/smb.conf I created a new, minimal file: 
> 
# /etc/samba/smb.conf
# Created Aug 18, 2014
# There MUST be a space around every equals sign.
[global]
#workgroup = WORKGROUP
workgroup = OURDOMAIN.local
browseable = yes
# My Perl programs running via cron create files and the mode MUST be 0766 for those new files.
create mode = 0766
writeable = yes
guest ok = yes
read only = no

[myshare]
# Share /home in Ubuntu. Production and test environments are different users here. 
path = /home
guest ok = yes


I'm the only one accessing this VM so security can be minimal. It is  already behind a firewall. My Ubuntu machine name is MYMACHINE.

Now test the smb.conf with: testparm -s. If there are no errors,  continue. If there are errors, make sure there are spaces around every  equals sign. And check for other errors. 

I already added a samba user called "samba" with Samba password of "mypass". **This is not the same password as the user password!** Using the machine name in place of the IP address did not work for me.

Restart samba. All on one line I typed: "sudo restart smbd; sudo restart nmbd; sudo service samba restart"
(I actually made an alias to do this as I was doing it a lot.)

Find the IP of the Ubuntu VM. I typed "ifconfig" and it was listed under the adapter "eth0" under "inet addr". 

Now open a DOS box and I entered: 
> net use t: \\my.ip.addr.ess\myshare /user:samba mypass

Notice that "myshare" is the sharename word that appears in /etc/samba/smb.conf. **It is not the Ubuntu directory to share!**

I also had to change the permissions on all my subdirs with Perl scripts so I can edit them using a Windows editor. 
My perl programs are all in $HOME/perl, so I went to $HOME and did "sudo  chmod -R a+rw perl/*". That covers the files but NOT the directory. 

For the directory I did: "sudo chmod a+rw perl".

---

### Post by bkvaluemeal on 2014-08-19
There is a commented share for all home directories. Why not use that?

---

### Post by bulrush2 on 2014-08-19
Wait, do you mean the share is called "home" in /etc/samba/smb.conf, and all I have to do is change the path? I didn't know what I was doing, so I did it this other way.

It's taken me a while to understand what name goes where on the Ubuntu vs the Windows side, so that's one reason why I wrote the post above. I haven't found any other doc that explains it this way.

---

