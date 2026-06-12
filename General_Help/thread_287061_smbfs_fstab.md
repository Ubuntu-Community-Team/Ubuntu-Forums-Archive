---
title: "smbfs fstab"
date: 2006-10-28
forum: General Help
---

### Post by Compact on 2006-10-28
Is any way to mount a samba folder every time the computer starts up but with differents credentials for every user?

---

### Post by dbott67 on 2006-10-28
Try this thread:

[http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)

Not sure if it will work, but under step #5 you'll need to modify 2 things:

1. Using ***[COLOR="Red"]'The Better Way'[/COLOR]*** in the HOWTO, change the location of **/root/.credentials** to **~/.credentials**
```
//192.168.1.2/Music /home/dbott/music   smbfs  auto,credentials=[COLOR="Red"]~/.credentials[/COLOR],uid=1000,umask=000,user   0 0
```

2. Instead of creating the **/root/.credentials** file, change the location to the home folder of each user (i.e. change it to **~/.credentials** or **/home/[COLOR="Red"]*user*[/COLOR]/.credentials**)
```
sudo gedit ~/.credentials
```
and add the following text:
```
username=their_smb_username
password=their_smb_password

```

Now, make the file only readable by root:
```
sudo chmod 600 /root/.credentials
```

Repeat for each user.

-Dave

---

### Post by Compact on 2006-10-28
I think it will not work beacause the system mount all the partitions in fstab when any user is logged in.

---

### Post by dbott67 on 2006-10-28
You're right... the script would need to run after login... I don't know what I was thinking there...

However, you could write a script that runs after login with the command:

```
sudo smbmount //192.168.1.2/Music /home/dbott/music -o credentials=~/.credentials,uid=1000,umask=000,user   0 0
```

(I haven't tested the actual command... but it would be something like this)

---

