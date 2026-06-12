---
title: "CIFS permissions issue with fstab but not mount command"
date: 2017-11-30
forum: General Help
---

### Post by ianmanning on 2017-11-30
I want to mount a Windows share using CIFS on my Ubuntu 17.04 machine. If I use the mount command below it works fine, and I can access the Windows share:
```
sudo mount -t cifs //servername/sharename /home/myuser/mediafolder -o credentials=/home/myuser/.smbcredentials,dir_mode=0777,file_mode=0777
```

[COLOR=#222222][FONT=Verdana]If I attempt to make this permanent using the following entry in /etc/fstab I get a permissions error when I try to access the mount point at /home/myuser/mediafolder :[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Consolas]//servername/sharename /home/myuser/mediafolder[/FONT][/COLOR] cifs credentials=[COLOR=#111111][FONT=Consolas]/home/myuser/.smbcredentials[/FONT][/COLOR],gid=1000,uid=1000,iocharset=utf8,file_mode=0777,dir_mode=0 0 0
```

What is the difference between the two options above, and why am I denied permissions with the 2nd approach?

---

### Post by deadflowr on 2017-12-01
You might need to add the _netdev option to the fstab.
_netdev delays mounting of the file system until after networking connection has been established.
And yes, that's how it's suppose to be spelled with the underscore: _netdev

---

### Post by ianmanning on 2017-12-01
> **deadflowr said:**
> You might need to add the _netdev option to the fstab.
_netdev delays mounting of the file system until after networking connection has been established.
And yes, that's how it's suppose to be spelled with the underscore: _netdev

Thanks for the suggestion. I just gave it a shot but still have the "Permission denied" error.

---

### Post by deadflowr on 2017-12-01
Is the dir_mode=0 right?

---

### Post by ianmanning on 2017-12-01
> **deadflowr said:**
> Is the dir_mode=0 right?

Yes

---

