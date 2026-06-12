---
title: "Unable to mount Encrypted drive"
date: 2016-06-23
forum: General Help
---

### Post by sean121 on 2016-06-23
so trying to follow this thread solution as i A. cannot start my own  thread yet (older user new account old account got deactivated after a  long absence newer but not total noob) and this is the closest that i  can find to the issue i am having. i have an older hdd with a corrupted  version of 12.04 on it. the home directory is encrypted so when i have  it plugged in as an external, i cannot access the files to copy them to a  different drive so i can load a new distro onto the corrupted drive. i  am trying to acess it through and external mount to usb on a laptop  running 16.04

```
sean@sean-Presario-CQ56-Notebook-PC:~$ sudo ecryptfs-recover-private
[sudo] password for sean: 
INFO: Searching for encrypted private directories (this might take a while)...
find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied
mount | grep ^/
sean@sean-Presario-CQ56-Notebook-PC:~$ mount | grep ^/
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb1 on /media/sean/d2883916-8b62-4eea-bd2d-5ef74b122d54 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
sean@sean-Presario-CQ56-Notebook-PC:~$ ls -l /home
total 4
drwxr-xr-x 39 sean sean 4096 Jun 23 12:56 sean


```

i get about that far and then i get lost. can you point me a little more directly at the next step please?
Thanks in advance

---

### Post by QDR06VV9 on 2016-06-23
There you go started your own Thread as to not confuse others helping with other thread.

---

### Post by sean121 on 2016-06-23
So after reading around i found that if this is tried from a live usb there is a lot less issues encountered. so setup a 16.04 liveusb it no mounts properly and
```
ubuntu@ubuntu:~$ sudo ecryptfs-setup-private
Enter your login passphrase {ubuntu}: 
```

also thanks runrickus i had an old profile associated with a dead email account that had enough posts to allow me to start my own thread,  but it was culled due to inactivity which i completely understand. and i will just update this post as i work through on my own and a more complete description until someone replies just to avoid double posting

The hdd with issue has 12.04 and i can log into it, however the home folder will not open and the distro isnt recognizing usb devices. room mates cat interrupted my update when i was afk and that was when the issue started. trying to finish or redo the update does nothing and im afraid to make the issue worse, so i think this is the best way to rescue my data off of the hdd. 

originally tried to acess through my normal disto/hdd but because of multiple home folders ecrypt wasnt mounting the correct folder. found that this could be solved by trying to mount from a live usb. created a 6.04 usb and am now trying to access it from there. 

now when i run ecrypt i get the output listed above. however the login passphrase isnt the same as the user login for that distro. so how can i recover that passphrase for that folder. 

so logged into the corrupt distro and tried to recover using ecrypt, but the passphrase is still different than the login so i am now trying to work around that

---

### Post by howefield on 2016-06-24
> **sean121 said:**
> also thanks runrickus i had an old profile associated with a dead email account that had enough posts to allow me to start my own thread,  but it was culled due to inactivity which i completely understand. ....

Just to make sure that there are no misunderstandings here, (for casual readers as well as yourself).

We do not cull accounts due to inactivity, people are free to come and go without fear of losing their account with the obvious exception of when in conflict with the forums Code of Conduct and secondly, there is no minimum post requirement before being able to start your own thread.

---

### Post by banceu_sergiu_ione on 2016-06-24
> **sean121 said:**
> 
```
ubuntu@ubuntu:~$ sudo ecryptfs-setup-private
Enter your login passphrase {ubuntu}: 
```


Why do you run a command that is meant to setup a cryptography if you try to mount it? First make sure you understand what commands do before to run it.

You should read this [Wiki]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory") see if helps. Pay attention and read 1st the points from 5 to 8  before you try to run any command. At botom of it you can find more links that might be of help.

---

