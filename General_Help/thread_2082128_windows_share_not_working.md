---
title: "windows share not working"
date: 2012-11-08
forum: General Help
---

### Post by Marloes on 2012-11-08
Hi,

I've spend half a day reading all the threads I could find on this, but have not been able to solve my problem.

I could mount and bookmark windows share servers in my company without any problem in 11.10.  I now have a new laptop on which I run 12.04 (64 bit) and it is impossible to browse to the server via: go, network, etcetera.

This morning I could see it, but it would not accept my credentials (which I am sure are fine as they are still working on my old computer and when I log into windows). After updating I cannot see the server at all under the windows share. 

I can mount it by using this command:
sudo smbmount //server/group/folder /home/myname/static/server -o user=username

How can I mount it and bookmark it in such a way that it is always there when I boot my computer? I must admit that I can do a little bit in the terminal, but your answer would have to be pretty detailed.

Thanks in advance for your help.

---

### Post by jerome1232 on 2012-11-08
Try in nautilus pressing ctrl+L and typing in

```
smb://servername/path/to/share
```

You should be prompted for credentials, once in, ctrl+D to bookmark it.

---

### Post by Marloes on 2012-11-09
> **jerome1232 said:**
> Try in nautilus pressing ctrl+L and typing in

```
smb://servername/path/to/share
```You should be prompted for credentials, once in, ctrl+D to bookmark it.

I did try that already and tried again this morning, but it did not work. Same problem as when I try to use the 'connect to' option...I fill in my credentials and nothing happens. It prompts me again for my credentials.

Any other suggestions?

---

### Post by mastablasta on 2012-11-09
sometimes samba needs to be restarted to see windows propperly
 
otherwise you could make a simple short script to run your command.

---

### Post by Marloes on 2012-11-09
> **mastablasta said:**
> sometimes samba needs to be restarted to see windows propperly
 
otherwise you could make a simple short script to run your command.

Thanks for the suggestion and yes, I could do that, but I run the GUI version because I have no programming background what so ever...in other words...writing a simple script takes me a long time...I was hoping to get it working the 'normal' way.

---

### Post by mastablasta on 2012-11-12
well like i said sometimes i see it sometimes i don't. i think it depends which computer boots up first.
 
this kind of script owuld be easy to do. my newbie attempt
open a text editor, you put this into it (well with your values and names) and save it to your home. name it for example *mountscript *
```
 
#!/bin/bash   
sudo smbmount //server/group/folder /home/myname/static/server -o user=username


```
 
right click on it and mark the file as executable under propperties. now you can double click it to run it. it will aks for user password.  you can then make a shortcut somewhere, launcher etc... maybe someone can come up with a nicer script....
 
maybe restarting samba will also do the trick: 
```
 
sudo service smbd restart


```
 
either way password is needed.

---

### Post by Marloes on 2012-11-12
Hi,

Thanks for your help. I have managed to solve it with help from our IT department and info from the internet. This is what I did: 

Get samba: sudo apt-get install smbfs

Make dir where I want to mount: sudo mkdir /folder

Give myself permission to them: sudo chown -R $LOCALUSER:$LOCALGROUP /folder

Make file with logon credentials: gedit ~/.smbcredentials 

Enter windows username and password in the file:
username=msusername
password=mspassword

Save the file and exit the editor

Change the permissions of the file to prevent unwanted access to credentials

Chmod gid ~/.smbcredentials (to find your gid type id at terminal prompt)

Edit fstab file: sudo nano -Bw /etc/fstab

At the bottom of this file add
//server/group/user /folder cifs credentials=/home/ubuntuusername/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 

As I did not know what the numbers meant I went to check with a more clued in colleague and he explained that it is read, write, execute access for yourself and others (read = 4, write = 2, execute = 1...add them all up to get 7). The first one is you, the second the group, the third is everyone. If you do not want anyone to execute and others only to read,  you can for example change the 0777 to 0644.

---

