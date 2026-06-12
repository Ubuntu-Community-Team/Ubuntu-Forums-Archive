---
title: "Media Folder Permissions"
date: 2012-12-23
forum: General Help
---

### Post by tgreena on 2012-12-23
I am having trouble setting permissions of a few disks I added to my ubuntu server. I got the disks working fine and mounting on boot-up. The disks boot and mount into the location /media/TV for one, and /media/Movies for another drive. I have them both shared via SMB and the server is shared via SSH so I can connect to the drive via SMB or SSH. 


I can go to the terminal on my Mac, connect to the server via ssh, and enter the command

```
sudo cp /home/myhome/stuff /media/TV/stuff
```

and it will copy over the content to my TV drive with no problem. The minute I try and open up the SSH via an sftp program, cyberduck is what I am using, or Filezilla is an alternative. Neither work. I get an error: 
```
"Failure (SSH_FX_FAILURE: An error occurred, but no specific error code exists to describe the failure.)."
```

I then tried to copy over the files by connecting to it from Finder on my Mac via smb://myUbuntuServer

 I tried to copy some files over that were on my mac to this /media/TV SMB share and it feeds me the error:

```
"Items can’t be copied to “Ubuntu-TV” because you don’t have permission to read them."
```

When I set up the SMB share... I specifically called the folder Ubuntu-TV, (pointing straight to /media/TV) here is my /etc/samba/smb.conf file

```
[Ubuntu-TV]
path =/media/TV
available = yes
valid users = myUserAccount
read only = no
browsable = yes
public = yes
writable = yes
```


I've tried 

```
sudo chmod -R 775 /media/TV
```

nothing

```
sudo chmod -R 777 /media/TV
```

nothing

What am I doing wrong here!?

---

### Post by tgreena on 2012-12-23
Doh!

I was able to solve the problem with the following lines, I did all 4 of them. If anyone would like to roughly explain what these lines did, and from my understanding, I think if I would have done the top line only it would have worked. But I did them all. Is this bad/good? A quick explanation would be amazing :)

```
sudo chown -R USERNAME:USERNAME /media/TV
sudo chgrp plugdev /media/TV
sudo chmod g+w /media/TV
sudo chmod +t /media/TV
```

Now it works!

---

