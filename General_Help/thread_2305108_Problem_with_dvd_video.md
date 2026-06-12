---
title: "Problem with dvd video"
date: 2015-12-02
forum: General Help
---

### Post by houlouk on 2015-12-02
Hello,
When I insert a dvd video, nothing happens but if I go in vlc it is well recognized.
I would want that it automatically proposes me something when I insert a dvd video (like for all other types of cd/dvd).

---

### Post by QDR06VV9 on 2015-12-02
With not knowing what DE you are using, But it should be the same or at least similar in most file manager's
Go to  Edit and then to Preferences(Click This)  and then at the top of that window that should have poped up.
There will be  a tab at the top, Navigate to the Multimedia Tab and there you can set your own Pref's there.
Enjoy

---

### Post by houlouk on 2015-12-03
I'm using gnome-shell.
I can't find anything about multimedia in nautilus prefs.

---

### Post by coldraven on 2015-12-03
In Ubuntu 15.10 the settings that you want are in "Details" > Removable Media

---

### Post by houlouk on 2015-12-03
In details dvd video is on "ask what to do" but nothing happens when I insert one.

---

### Post by coldraven on 2015-12-03
> **houlouk said:**
> In details dvd video is on "ask what to do" but nothing happens when I insert one.
Try changing  the setting to "Open with VLC", if that works see if changing back to "Ask what to do" fixes the problem.

---

### Post by houlouk on 2015-12-03
It doesn't work either with "open with vlc".

---

### Post by QDR06VV9 on 2015-12-03
Sometimes you have to re-login for the changes to take effect.

---

### Post by houlouk on 2015-12-03
It doesn't work (even if I reboot).

---

### Post by QDR06VV9 on 2015-12-03
@houlouk I just don't know what to say I rebooted to Unity and works nicely here.
But I am on 16.04 Development cycle and using nautilus 3.14

---

### Post by houlouk on 2015-12-03
When I insert a dvd, I have this error that appears in  journalctl : 

```


déc. 03 20:01:09 houlouki-N73SV kernel: blk_update_request: I/O error, dev sr0, sector 4096
déc. 03 20:01:09 houlouki-N73SV kernel: blk_update_request: I/O error, dev sr0, sector 4096
déc. 03 20:01:09 houlouki-N73SV kernel: Buffer I/O error on dev sr0, logical block 1024, async page read
déc. 03 20:01:09 houlouki-N73SV kernel: blk_update_request: I/O error, dev sr0, sector 4100
déc. 03 20:01:09 houlouki-N73SV kernel: Buffer I/O error on dev sr0, logical block 1025, async page read



```

---

### Post by QDR06VV9 on 2015-12-03
What is the output of this in the terminal

```
apt-cache policy libdvdread4 
```

---

### Post by houlouk on 2015-12-03
Here it is : 

```

houlouki@houlouki-N73SV:~$ apt-cache policy libdvdread4 
libdvdread4:
  Installé : 5.0.0-1ubuntu1
  Candidat : 5.0.0-1ubuntu1
 Table de version :
 *** 5.0.0-1ubuntu1 0
        500 http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/ wily/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by QDR06VV9 on 2015-12-03
Huumm??
Have you tried another DVD yet?

---

### Post by QDR06VV9 on 2015-12-03
Just to make sure we are looking at this the right way and ruling out software.
```
sudo apt-get install ubuntu-restricted-extras
```
 And also
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Not going to hurt but just to be sure just log-out and log-in again.
Fingers Crossed

---

### Post by houlouk on 2015-12-04
In fact, I can read dvds but they are not automatically mounted when they are inserted.
I've tried with virtualbox and it works with ubuntu 14.04 but not after.

---

### Post by QDR06VV9 on 2015-12-04
> **houlouk said:**
> In fact, I can read dvds but they are not automatically mounted when they are inserted.
I've tried with virtualbox and it works with ubuntu 14.04 but not after.
Ok Understood..But the errors you showed in a earlier post
> [COLOR=#000000][FONT=Ubuntu Mono]déc. 03 20:01:09 houlouki-N73SV kernel: blk_update_request: I/O error, dev sr0, sector 4096
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]déc. 03 20:01:09 houlouki-N73SV kernel: blk_update_request: I/O error, dev sr0, sector 4096[/FONT][/COLOR]
Can point to non readability from the disk..
I am all out of ideas sorry..
Best Regards

---

