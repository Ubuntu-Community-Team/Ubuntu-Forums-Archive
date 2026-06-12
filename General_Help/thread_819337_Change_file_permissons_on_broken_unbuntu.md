---
title: "Change file permissons on broken unbuntu?"
date: 2008-06-05
forum: General Help
---

### Post by ChardFi on 2008-06-05
Hi,

I've got a broken HDD that won't boot (makes lots of horrible noises and then falls over) but i can boot off the cd and mount it. I want to be able to copy my data off using the live CD and an external HDD but the files i need say i'm not the owner and have the orange emblem on them.

How can I get access to these files?

Thanks

---

### Post by rraj.be on 2008-06-05
Just try with sudo command.

like this.


```
sudo -i

cp <source path> <destination path>
```

else you can use some data recover utilities like PC INSPECTOR

---

### Post by ChardFi on 2008-06-05
Thanks for the reply,

This just says "omitting directory" and jumps to the next line :-( 

I'm sure there must be some way of doing this isn't there?

These special tools you speak of, i don't see them in ubuntu?

---

### Post by rraj.be on 2008-06-05
What i have mentioned is the most power full Data recover tool in windows that i have used even for extracting root privelaged data's.

I think you can use some thing like D/Recovery tools that comes along with a boot cd.

You can use this

```
[www.hiren.info/pages/bootcd]("www.hiren.info/pages/bootcd")
```

---

### Post by bodhi.zazen on 2008-06-05
Easiest option is to use :

```
gksu nautilus
```

Once you are done, read about permissions.

sudo chown ....
sudo chmod ....

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

@rraj.be : you need a -r for directories

```
sudo cp -r /media/broken_partition/data/* /media/backup_partition/backup
```

---

### Post by rraj.be on 2008-06-05
Yes. sorry. i forgotten that.

---

