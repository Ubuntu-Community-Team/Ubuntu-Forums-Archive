---
title: "Mount automatically - WD Cloud Nas Server"
date: 2019-10-31
forum: General Help
---

### Post by jfca283 on 2019-10-31
Hi, 
I need to mount automatically my WD Cloud.
I can mount it using Nautilus, but some applications can't navigate ( or maybe I don't know) to the NAS folder.
I know that I need to edit the fstab, but I am not familiar with this kind of filesystem. 
Nautilus mount the drive as afp: when I access some folders/files.
Thanks for your time and interest.

---

### Post by #&amp;thj^% on 2019-10-31
Been a while since I've used one of those, Because the My Cloud uses Samba over the local network you should be able to access it like any other network Samba share.
```
 
apt-get install autofs cifs-utils
```

edit /etc/autofs.master and add this line at the end.
```

/nas /etc/auto.mycloud --timeout 120,&#8211;ghost
```

create a file /etc/auto.mycloud and add:
```

myshare -fstype=cifs,user=someuser,domain=WORKGROUP,password=&#8220;someuserpass&#8221; ://mycloud.ip/myshare/
public -fstype=cifs,user=,domain=WORKGROUP,password="" ://mycloud.ip/public/
```

for an example only.
More information found here: [https://cocoaallocinit.com/2014/01/04/wd-my-cloud-nas-on-ubuntu/](https://cocoaallocinit.com/2014/01/04/wd-my-cloud-nas-on-ubuntu/)
This is just one way, others will have more for your consideration.

---

### Post by jfca283 on 2019-10-31
It didn't work.
I needed it to use nautilus in order to connect the WD.

---

### Post by TheFu on 2019-10-31
> **jfca283 said:**
> It didn't work.
I needed it to use nautilus in order to connect the WD.

Nautilus will see the storage, when it gets mounted using autofs and other programs will be able to use it.  

*It didn't work* is not very helpful for someone trying to provide help. 
Exact error messages and exact log messages?
Also, showing the exact configuration files would be good too.

---

### Post by jfca283 on 2019-11-01
I'm sorry for posting without any further info.
I edited the fstab file, but when I reboot my system I didn't get the WD Cloud mounted.
Only using nautilus I can see the NAS drive. "Other Locations" and then I click on MyCloud.

---

### Post by TheFu on 2019-11-01
If you don't answer the questions asked, nobody can help.  Good luck.

---

### Post by jfca283 on 2019-11-01
¿where can I get the error messages from the fstab?

---

### Post by TheFu on 2019-11-01
> **jfca283 said:**
> ¿where can I get the error messages from the fstab?

If you run **sudo mount -a** any errors should be displayed on the terminal.
If you will post the complete fstab file, it is likely someone will see some issues. Start by using the IP address for the storage, not a name.

Using a GUI tool to create mounts isn't the same sort of 'mount' as using autofs or the fstab.  External storage, like networked or USB really can use the added flexibility of the autofs mount method. Autofs deals with storage that isn't available better.

---

