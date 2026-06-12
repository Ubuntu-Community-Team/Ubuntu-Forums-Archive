---
title: "Xubuntu doesn't start the desktop"
date: 2013-02-27
forum: General Help
---

### Post by ubunet on 2013-02-27
Xubuntu doesn't start the desktop. Look the photo with the error:

[http://img837.imageshack.us/img837/898/dscn27211.jpg](http://img837.imageshack.us/img837/898/dscn27211.jpg)

I searched in the web for this error but any solutions work for me.

---

### Post by steeldriver on 2013-02-27
Are you in recovery mode? if so, the filesystem will be in read-only mode by default, and it won't be possible to write to the Xauthority file (or anywhere else)

Starting X as root isn't usually recommended anyhow

What exactly are you trying to do?

---

### Post by ubunet on 2013-02-27
> **steeldriver said:**
> Are you in recovery mode? if so, the filesystem will be in read-only mode by default, and it won't be possible to write to the Xauthority file (or anywhere else)

Starting X as root isn't usually recommended anyhow

What exactly are you trying to do?

I just want my desktop again! I'm not a expert in linux.

---

### Post by steeldriver on 2013-02-27
What happened before it stopped working?

Did you previously use a graphical display manager or have you always used startx?

IIRC the correct method to start Xubuntu manually is startxfce4 NOT startx - can you log in to the console as a regular (not root) user? if so what happens if you do that and then do startxfce4?

---

### Post by ubunet on 2013-02-27
> **steeldriver said:**
> What happened before it stopped working?

Did you previously use a graphical display manager or have you always used startx?

IIRC the correct method to start Xubuntu manually is startxfce4 NOT startx - can you log in to the console as a regular (not root) user? if so what happens if you do that and then do startxfce4?

I use XFCE everday. I'm a new linux user (I migrated from Windows). Today a works in XFCE all day - Firefox, Thunderbird, LibreOffice, etc... Today, this error happens.

---

### Post by ubunet on 2013-02-27
> **steeldriver said:**
> What happened before it stopped working?

Did you previously use a graphical display manager or have you always used startx?

IIRC the correct method to start Xubuntu manually is startxfce4 NOT startx - can you log in to the console as a regular (not root) user? if so what happens if you do that and then do startxfce4?

When I type **startxfce4**, as normal user,the XFCE4 starts, not Xubuntu Desktop (my desktop). But, how I configure Xubuntu Desktop to start automatically?

---

### Post by steeldriver on 2013-02-27
Well that's a good sign - it means that the basics are all in place

Perhaps the problem is just that your display manager isn't starting? what are the contents of /etc/X11/default-display-manager ?

```
cat /etc/X11/default-display-manager
```

---

### Post by ubunet on 2013-02-27
> **steeldriver said:**
> Well that's a good sign - it means that the basics are all in place

Perhaps the problem is just that your display manager isn't starting? what are the contents of /etc/X11/default-display-manager ?

```
cat /etc/X11/default-display-manager
```

**/usr/sbin/lightdm**

---

### Post by steeldriver on 2013-02-27
OK that looks good - so what exactly happens when you boot? do you get the lightdm 'greeter' (login) screen or does it boot to text mode?

---

### Post by ubunet on 2013-02-27
> **steeldriver said:**
> OK that looks good - so what exactly happens when you boot? do you get the lightdm 'greeter' (login) screen or does it boot to text mode?

When I boot, Xubuntu stop in a black screen:

```
* Checking battery state..       [OK]
```

---

### Post by steeldriver on 2013-02-27
Can you check lightdm.conf please?

```
cat /etc/lightdm/lightdm.conf
```

You could also try logging in at a virtual terminal (Ctrl-Alt-F1 etc) and then doing

```
sudo service lightdm restart
```

and noting any error messages

---

### Post by fdrake on 2013-02-27
the log should be in: /var/log/lightdm/*log*

also try to reinstall lightdm (plug an ethernet cable if you are using wifi)
```

sudo apt-get install --reinstall lightdm xorg xserver-xorg

```
restart

---

### Post by ubunet on 2013-02-27
> **steeldriver said:**
> Can you check lightdm.conf please?

```
cat /etc/lightdm/lightdm.conf
```You could also try logging in at a virtual terminal (Ctrl-Alt-F1 etc) and then doing

```
sudo service lightdm restart
```and noting any error messages

cat /etc/lightdm/lightdm.conf
```
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
```sudo service lightdm restart
```
stop: Unknow instance:
lightdm start/runing, process 1921
```

---

### Post by ubunet on 2013-02-27
**Not work.** What I do now?

---

### Post by fdrake on 2013-02-27
did you try reinstalling them? see my post.

---

### Post by ubunet on 2013-02-27
> **fdrake said:**
> did you try reinstalling them? see my post.

Yes, I reinstall. Didn't work for me.

EDIT:

I reinstall only lightdm xorg xserver-xorg

---

### Post by ubunet on 2013-02-27
Guys,

I saw that my **/** partition are using 100% of space. I tried to install a update and I give a error. Maybe this is a source of this problem.

---

### Post by fdrake on 2013-02-27
check your home dir. That is the reason why you can't login. Check .xerrors

---

### Post by ubunet on 2013-02-27
> **fdrake said:**
> check your home dir. That is the reason why you can't login. Check .xerrors

I could log in, just did not start XFCE automatically.

Something crazy are happening with my Acer laptop. It was turned on since 2 days ago and I shutdown for do other things. After 1 hour, I turn on again and I can start Xubuntu normaly with XFCE.

---

### Post by fdrake on 2013-02-27
> **ubunet said:**
> I could log in, just did not start XFCE automatically.

Something crazy are happening with my Acer laptop. It was turned on since 2 days ago and I shutdown for do other things. After 1 hour, I turn on again and I can start Xubuntu normaly with XFCE.

check the size of your log files in your home dir. This problem may happen again, if you do not know what caused it. Some logs may reach over 10GBs

---

### Post by ubunet on 2013-02-27
> **fdrake said:**
> check the size of your log files in your home dir. This problem may happen again, if you do not know what caused it. Some logs may reach over 10GBs

My **/home** folder is in separate partition with 500GB. But, I will see the logs.

---

