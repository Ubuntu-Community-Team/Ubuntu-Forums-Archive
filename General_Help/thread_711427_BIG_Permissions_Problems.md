---
title: "BIG Permissions Problems"
date: 2008-02-29
forum: General Help
---

### Post by austinderrick2 on 2008-02-29
I accidentally made a mistake, I was trying to do

```

sudo chmod 0777 /media/disk1

```

But instead, on accident, I did

```

sudo chmod 0777 /media/disk

```

Now everything on my filesystem is chmoded 0777.

Right now I can't even log in because my home directory has the wrong permissions!!!

:confused:

I booted into the live CD and I have set some of the permissions back to normal, but I still can not sudo anything!!! (It says setuid must be root)

Anyone know where I could find like a list of file permissions to fix, or at the very least point me to a few of the files permissions I need to change???

---

### Post by HermanAB on 2008-02-29
Re-install.

Sorry, but that is really the only way to fix a mess like that.

Cheers,

Herman

---

### Post by austinderrick2 on 2008-02-29
lol... fun fun... I'm gonna dink around a bit before I do that, but I fear you are right... :confused:

---

### Post by austinderrick2 on 2008-02-29
Ok, I can login again, I still have the problem with sudo and su - but that seems to be the worst of my issues:

```

#sudo
sudo:setuid must be root

```

---

### Post by pointone on 2008-02-29
To fix the sudo problem, boot into recovery mode and:

```
chmod u+s `which sudo`
```

However, there's bound to be plenty more errors like this. I'd recommend a reinstall as well.

---

### Post by austinderrick2 on 2008-02-29
> 
However, there's bound to be plenty more errors like this. I'd recommend a reinstall as well.

Yah, but then I wouldn't learn anything new would I?? :P ;) lol...




So far so good:

Booting into the LiveCD, I mounted the drive at **/media/disk** so:

```

sudo chmod 4755 /media/disk/usr/bin/sudo
sudo chmod 4755 /media/disk/bin/su
sudo chmod 0440 /media/disk/etc/sudoers
sudo chmod 0644 /media/disk/root/ -R
sudo chmod 0644 /media/disk/home/**PUT_YOUR_USER_NAME_HERE**/.dmrc

```


And it appears to be working correctly - as far as I can tell!

---

