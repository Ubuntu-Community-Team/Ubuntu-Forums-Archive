---
title: "Manually start X"
date: 2007-06-09
forum: General Help
---

### Post by Moonshine on 2007-06-09
Hello,

I am using xubuntu for a home file server. I would like it so that I can start X when I need to use it, (like if I use vnc), but otherwise leave it off.


Thanks.:)

---

### Post by angryhomer17 on 2007-06-10
```
xfce4-session
```

I think this will work. Should open up the xfce gui if it isn't open already. Not sure if you just want to open the xfce gui from a terminal or what...

---

### Post by Moonshine on 2007-06-10
> **angryhomer17 said:**
> ```
xfce4-session
```

I think this will work. Should open up the xfce gui if it isn't open already. Not sure if you just want to open the xfce gui from a terminal or what...

Thanks for the reply....:KS

I would like, as default, when the computer starts up it doesnt start xfce. The only time I would want it started would be if I used VNC to connect to it, and I could type a command via SSH that would start it.

Hope that makes sense.

---

### Post by eggdeng on 2007-06-10
Why don't you take a look at boot up manager? ```
apt-get install bum
```

---

### Post by kvonb on 2007-06-10
I'm not sure about Xubuntu, but if you look in /etc/init.d/ you should find something like xdm/gdm/kdm.

That is the script that starts X on boot.  I would suggest moving it to another location (don't delete it in case you need it later).

```
sudo mv /etc/init.d/xdm /root/
```

That will put it in root's home folder.

Now to manually start X, simply type:

```
startx
```

It will of course run as the user that you start it as.

---

