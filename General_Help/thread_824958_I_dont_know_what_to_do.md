---
title: "I dont know what to do"
date: 2008-06-10
forum: General Help
---

### Post by kayslay on 2008-06-10
I dont have soung after installing ubuntu 7.10,i have tried every help i got from here but its not still working,im using lenovo laptop 0769ANU

---

### Post by cmnorton on 2008-06-10
Using sudo, try editing this file:

/etc/modprobe.d/alsa-base

I added this line to the bottom of the file:

options snd-hda-intel model=thinkpad-t61p

Edit:
---------

I have a Lenovo Thinkpad T61p, and I guessed at splitting thinkpad from t61p with a dash (-) character. This worked for me.

You will need to add what you believe is the closest thing to your model number. 

Good luck.

---

### Post by kayslay on 2008-06-10
> **cmnorton said:**
> Using sudo, try editing this file:

/etc/modprobe.d/alsa-base

I added this line to the bottom of the file:

options snd-hda-intel model=thinkpad-t61p

Edit:
---------

I have a Lenovo Thinkpad T61p, and I guessed at splitting thinkpad from t61p with a dash (-) character. This worked for me.

You will need to add what you believe is the closest thing to your model number. 

Good luck.
i  followed what u said but all i got was permission denied 
kayslay@kalinichenko:~$ /etc/modprobe.d/alsa-base
bash: /etc/modprobe.d/alsa-base: Permission denied

---

### Post by dje on 2008-06-10
Use this:
```
sudo gedit /etc/modprobe.d/alsa-base
```

hope that helps,
dje

---

### Post by kayslay on 2008-06-10
> **dje said:**
> Use this:
```
sudo gedit /etc/modprobe.d/alsa-base
```

hope that helps,
dje

i managed to edit with yurs and i restarted the computer but still its not working,im even fraustrated

---

### Post by d.kusummmanth@gmail.com on 2008-06-10
> **kayslay said:**
> i  followed what u said but all i got was permission denied 
kayslay@kalinichenko:~$ /etc/modprobe.d/alsa-base
bash: /etc/modprobe.d/alsa-base: Permission denied
u got permission denied, because u r **NOT root user**.
 To get root privileges, type **sudo su** in _Terminal_. 
Then enter ur current password.
 This will provide u with **root privileges.**

THen u can paste the commands suggested by the above user:
> Using sudo, try editing this file:

/etc/modprobe.d/alsa-base

I added this line to the bottom of the file:

options snd-hda-intel model=thinkpad-t61p

If u wanna exit from **root mode** to **normal mode**, just type **exit**.

---

### Post by kayslay on 2008-06-10
> **d.kusummmanth@gmail.com said:**
> u got permission denied, because u r **NOT root user**.
 To get root privileges, type **sudo su** in _Terminal_. 
Then enter ur current password.
 This will provide u with **root privileges.**

THen u can paste the commands suggested by the above user:


If u wanna exit from **root mode** to **normal mode**, just type **exit**.

I still cant get permission,im about to even cry,lol

---

### Post by cmnorton on 2008-06-11
> **kayslay said:**
> I still cant get permission,im about to even cry,lol

Edit:
------------------

When you type sudo vi /etc/modprobe.d/alsa-base you will be prompted for a password. If your user name is the user who installed the system, use your own password, the one you used to log in. 

You do not have to use the vi editor; that is what I use. You can try another one. If it's an X-based editor, use gksudo.

gksudo kwrite /etc/modprobe.d/alsa-base

I'm hoping someone will bail me out by listing one of Gnome's nice X text editors, because I'm on KDE.

---

