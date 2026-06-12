---
title: "Any reasons not to use 771 for my folder permissions"
date: 2008-06-23
forum: General Help
---

### Post by mactece on 2008-06-23
I've carefully set my home pc up so that everyone is in an appropriate group (children have the lowest access, then wife, then  me - I am a member of all groups). I tried setting my permissions to 770 but couldn't use nautilus. After searching the forums and an earlier post [http://ubuntuforums.org/showthread.php?p=5245528#post5245528]("http://ubuntuforums.org/showthread.php?p=5245528#post5245528")
I have set permissions to 771. Any reasons why I shouldn't? Will this mess up anything I don't understand (e.g. packages)

Any comments appreciated (no, really:))

David

---

### Post by chrisccoulson on 2008-06-23
What do you mean "couldn't user nautilus". If you can't access a folder with 770 permissions, then you are neither the owner or a member of the group. I have 750 permissions on my home folder to restrict read-write access to myself and read access to a group of my choice. There should be no point in setting the executable bit alone (771), as you need the read bit set as a minimum in order to be able to list the folder contents anyway.

---

### Post by sisco311 on 2008-06-23
Are you talking about the /home folder or /home/your-username folder?

You can set 0771 permissions on the /home folder, but you will not bee able to list the users home folders. The default permission on the /home folder is 0755(and it's owned by root:root).

---

### Post by mactece on 2008-06-23
Sorry Chrisccoulson, I meant I couldn't USE nautilus. When I tried to open "PLACES" it gave me a don't have permission error. From what Sisco311 says this is because the /home folder is owned by root:root. None of my users is a member of the group root so I guess that was the problem when I set it to 770.

My /home is now root:root and 755. I have also now set my /home/david ("home") folder to 770 and I can still list it in PLACES so I guess there is some protocol which prevents a user from listing /home/user if they cannot read /home. 

So a better idea would be to set everyone's folder to 770, it seems.

I'm still curious about my earlier question - will setting all my users folders to 770 (including hidden files because I was using "chmod -R")  mess with the software. Will Thunderbird still be able to store my messages etc etc?

Regards

David

PS I went with 770 because I have created a dummy user called "control" who has the same privileges as me. Then if I mess up my account in some unforeseen way I can still log on as an administrator and get to all the files. My thinking is that I can control everyone else's files from my login (for ease of backup and housekeeping the kids' accounts). Most of this is probably Windows(TM) induced hysteria on my part. One year on and I still wake up screaming.

---

### Post by chrisccoulson on 2008-06-23
In general, recursive chmod'ing can lead to bad things, so you shouldn't use it unless absolutely necessary. Setting the permissions of /home/david using a 'chmod 770 /home/david' should be sufficient to control access to your home folder without having to do a recursive chmod.

---

### Post by sisco311 on 2008-06-23
Make sure everything in your home folder is owned by you:
```
sudo chown -R $USERNAME. $HOME
```Set the default permissions on your home folder and files(recursively):
```
chmod -R 0644 $HOME
```**r**ead/**w**rite/e**x**ecute for the owner
**r**ead for group
**r**ead for others

In order to open directories you need execute permission. This command will set execute permissions on directories in your home folder (recursive) 
```
chmod -R ug+X $HOME
```Set the permission of the dmrc file:
```
chmod 0644 $HOME/.dmrc
```Set the permission of the home folder(NOT recursive)
```
chmod 0750 $USERNAME
```If you follow my instructions to setup the permissions on the home folder for your kids, then anybody who is member of the group parents will be able to read/write/execute the files from the kids home folder, without root privileges(until they learn to boot in single user mode and take full control over the system:)).

for more info:
```
man umask
man newgrp
```read more about file permissions:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

