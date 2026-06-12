---
title: "[SOLVED] AAAAAAH!! What Happend!!!"
date: 2008-07-09
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-07-09
I tried logging into my gnome session and I got this:
```

/etc/gdm/Xsession: Beggining session setup...
Can't create dir /home/jared/Desktop
Can't create dir /home/jared/Desktop
Can't create dir /home/jared/Templates
Can't create dir /home/jared/Public
Can't create dir /home/jared/Documents
Can't create dir /home/jared/Music
Can't create dir /home/jared/Pictures
Can't create dir /home/jared/Videos
Can't create dir /home/jared/
Setting IM through im-switch for locale=en_ZA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default

(seahorse-agent:6065): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory `/home/jared/.gnome2/': Permission denied
```

HELP HELP HELP

---

### Post by forger on 2008-07-09
1)is this ubuntu hardy heron 8.04??

2)are you logged in as user jared?

3)change the owner:
```
sudo chown -hR jared:jared /home/jared/.gnome2/
sudo reboot
```

it will restart your machine

---

### Post by 4t0m1c_w07f on 2008-07-09
> **forger said:**
> 1)is this ubuntu hardy heron 8.04??

2)are you logged in as user jared?

3)change the owner:
```
sudo chown -hR jared:jared /home/jared/.gnome2/
sudo reboot
```

it will restart your machine

Yes
Yes
OK will try

It says no such file or directory!

---

### Post by iaculallad on 2008-07-09
Try to login using Restore mode:

```
sudo chown your_username /home/your_username/.ICEauthority
sudo reboot
```

---

### Post by 4t0m1c_w07f on 2008-07-09
And the other thing that happend was that splashy doesn't work properly now. I installed it yesterday and it was working nicely but now it freezes and then complains that it is waiting for a message.

---

### Post by 4t0m1c_w07f on 2008-07-09
Sorry, Another thing: Since i installed Splashy the first boot-up doesnt load gdm but then I reboot and it does.

---

### Post by forger on 2008-07-09
> **4t0m1c_w07f said:**
> I tried logging into my gnome session and I got this:

Wait, is it fixed now?
Is it **your** home dir? Are you user jared? Just to be sure

make a text file with the output of
```
ls -la $HOME/.*
```
then attach it here

---

### Post by 4t0m1c_w07f on 2008-07-09
> **forger said:**
> Wait, is it fixed now?
Is it **your** home dir? Are you user jared? Just to be sure

make a text file with the output of
```
ls -la $HOME/.*
```
then attach it here

Fixed it :D

---

