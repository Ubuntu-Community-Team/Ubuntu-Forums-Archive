---
title: "Question about the root account and video..."
date: 2007-03-05
forum: General Help
---

### Post by Cr00zng on 2007-03-05
I have a Dell 620 laptop with Intel video on the motherboard with widescreen display capable of doing 1280x800. The setup configured 1024x768 as the only resolution that is available in the GUI interface. How do I make the resolution the supported 1280x800?

I've tried to login as root, but it says that the account is not allowed to login from this station. I am not sure as to why, but how do I change that to allow the root to login locally to this laptop?
10QIA...

Cr00zng

---

### Post by taurus on 2007-03-05
1.  You can edit /etc/X11/xorg.conf to include that resolution 

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```
or you can reconfigure it again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then reboot.

2.  Root account is disable as default so you don't log in as root.  Instead, you use sudo (or gksudo) if you need to access your system as root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Cr00zng on 2007-03-05
> **taurus said:**
> 
1.  You can edit /etc/X11/xorg.conf to include that resolution

Thanks, now I have the 1280x800...
> 
2.  Root account is disable as default so you don't log in as root.  Instead, you use sudo (or gksudo) if you need to access your system as root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

But I do want to login as root when I need to make a number of changes to the system; it's tiring typing the password all the times. I most certainly know how to use sudo and/or just plain "su -" to the root, that's not the issue. 
If there's no way to login as root, Ubuntu is gone from my box; dictating what people can and cannot do remind me to another OS which actually let you login as administrator.
10Q...

Cr00zng

---

### Post by taurus on 2007-03-05
> **Cr00zng said:**
> 
If there's no way to login as root, Ubuntu is gone from my box; dictating what people can and cannot do remind me to another OS which actually let you login as administrator.
10Q...

Cr00zng

Hey, easy there...

If you must.  Here it is so be careful and good luck.
```
sudo passwd root
```
Then, 

```
su -
```

---

### Post by Cr00zng on 2007-03-05
> **taurus said:**
> Hey, easy there...

If you must.  Here it is so be careful and good luck.
```
sudo passwd root
```
Then, 

```
su -
```

So you **_can_** login as root :) 
Thanks and I'll be careful!!!

Cr00zng

---

### Post by taurus on 2007-03-05
> **Cr00zng said:**
> So you **_can_** login as root :) 
Thanks and I'll be careful!!!

Cr00zng

Of course, you can log in as root but it's _highly_ not recommended.

---

### Post by Cr00zng on 2007-03-06
> **taurus said:**
> Of course, you can log in as root but it's _highly_ not recommended.
Thank you for your help and concerns; this laptop will be used for vulnerability assessment over the network with Nmap, Nessus, SARA, Nikto, etc. All of these program can run with sudo and/or su once their installed. This laptop pretty much well be fired up only when needed. 
Thanks again...

Cr00zng

---

### Post by anaconda on 2007-03-06
Givin root a password isn't quite enough.. in addition you also have to enable graphical root login..

In Dapper it can be enbled from here:
"system>Administration>Login Window"
and from there the security tab and select the "allow local system administrator login"

---

### Post by 3rdalbum on 2007-03-06
Another way to get around Ubuntu's restriction without negating it entirely is to go to System > Administration > Services and turn off GDM. This drops you to the terminal. Log in and type:

```
sudo startx
```

You will be logged into Gnome as root, yet you haven't actually activated a root account. When you restart, GDM will start up again as normal and you can log in as normal.

---

### Post by Cr00zng on 2007-03-06
> **anaconda said:**
> Givin root a password isn't quite enough.. in addition you also have to enable graphical root login..

In Dapper it can be enbled from here:
"system>Administration>Login Window"
and from there the security tab and select the "allow local system administrator login"

Sweet, that works just fine; thanks!!

Cr00zng

---

