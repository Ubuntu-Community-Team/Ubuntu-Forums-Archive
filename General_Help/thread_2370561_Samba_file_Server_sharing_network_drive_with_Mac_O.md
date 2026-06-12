---
title: "Samba file Server sharing network drive with Mac OS X Serria"
date: 2017-09-04
forum: General Help
---

### Post by dmbomer on 2017-09-04
1. install Samba
2. edit the /etc/samba/smb.conf
At the bottom of the file I used the following.  I found examples from multiple sources which was confusing as hell.  I went through all the steps and still couldn't get my macbook pro to connect to the server.  So after a bit of time I realized I'm thinking about this wrong.  All I want is a simple file server for home use.  No remote access from the Net.  Only local area access.  

So you need a directory or drive to share 

[share]
    comment = Ubuntu File Server Share
    path = /media/dmbomer
    browsable = yes
    guest ok = no
    read only = no
    create mask = 0755
[account]
    valid users = dmbomer
    public = no
    writable = yes

Save and Exit

Samba file server needs a user name that will have permission to access this directory or drive  from the server.  
To keep it simple I used the user name and password I  login into on the macbook pro.
Create the following file smbusers in /etc/samba/smbusers and just add this line

<username> = "<dmbomer>"

Save and Exit

Now this user name needs a password.
sudo smbpasswd -a dmbomer than enter the password and retype when asked.

Finally restart the server 
sudo systemctl restart smbd.service nmbd.service

On the Macbook click Go from the menu bar while on the desktop select connect to server 
type in the server address than click connect.

A moment later you will be prompted to connect as guest or registered user
Enter the user name 
Enter the password 
Click connect

And if all works out you will get another screen Select the volumes you want to mount on "just click the ok button"  Bingo your done another window appears with the drive or directory you wanted to share.  

I hope this information is helpful to anyone that just wants something simple when it comes to a file server.

---

### Post by TheFu on 2017-09-05
Have you considered using NFS instead?  Unix systems use NFS for file sharing.  All permissions work for local and remote storage as expected under NFS. NFS is about 20% more efficient than samba too.  The only trick is that under NFS, the userid/groupid needs to be consistent between the NFS client and server systems.  I think OSX userids begin at 500. On Ubuntu, they begin at 1000.  Changing it isn't very hard, but those numbers need to match. Make a plan before you do this. There are 3 steps.
* change the passwd file number(s) # I'd use sudoedit
* change the group file number(s)  # I'd use sudoedit
* change each of the files owned by any of the users on the system to their respective new numbers. I'd use 'find' with a 'chown'.
It is easiest/safest to perform these tasks from a live-boot flash drive and mount the different storage media into that environment.  You'll want to have a good plan for each step, regardless.  On a small system, I can do it in about 3 minutes.

Usually after I post about NFS, someone else will come in and help with samba, if that is still your interest.

---

### Post by Morbius1 on 2017-09-05
I realize this is a HowTo and the share definitions are examples but you do have an error in one of them. You have no path defined:
> [account]
    valid users = dmbomer
    public = no
    writable = yes
Also, and again this is your HowTo not mine so I am hesitant to offer any changes or alternatives to what you posted, but you might want to explore one more step on your Linux server:

Create a file at **/etc/avahi/services/samba.service** with this content:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```
Your samba server will now show up automatically under Shared in the left side panel of Finder so you won't have to use Go. Avahi = Bonjour so if this is an all Linux or a Linux / macOS network you don't need nmbd or any of the other Windows host discovery stuff.

---

### Post by dmbomer on 2017-09-05
I am no where near that skill level. 

 I found Samba to effective for straight simple dirty sharing for now.  But the Go to server is becoming a pain now.  So I will explore your suggestions Morbius and I don't get any errors at least visible.  

I will also look into the NFS TheFu thank you both for the suggestions.

---

### Post by Morbius1 on 2017-09-06
> **dmbomer said:**
> So I will explore your suggestions Morbius and I don't get any errors at least visible. 
> [account]
    valid users = dmbomer
    public = no
    writable = yes
Run the following command that tests the settings you have in smb.conf:
```
testparm -s
```
Within the output you will get this error message:
> WARNING: No path in service account - making it unavailable!
NOTE: Service account is flagged unavailable.
Samba has disabled the "account" share as it does not know what to share because you did not tell it what to share by giving it a path. If it's a subfolder of /media/dmbomer you may access it through the [share] share but not directly from the "account" share. I suppose it's possible you have the path in the [global] section but that's not the usual way of setting up shares/

In any event you posted a howto and having a share defined without a path to the folder being shared will confuse people.

---

