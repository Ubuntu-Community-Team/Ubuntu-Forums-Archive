---
title: "Logs me off"
date: 2007-07-02
forum: General Help
---

### Post by mwk001 on 2007-07-02
Hi i'm new to linux and don't know much so any help is greatly appreciated. I've noticed that anytime I go to change my screensaver as i'm scrolling through the ones available it will crash the session and brings me to the log in screen name. Thanks again.

---

### Post by khedron on 2007-07-02
Does this happen when a particular screensaver is selected?

I reckon it's something to do with your graphics card. What graphics card do you have?

---

### Post by mwk001 on 2007-07-02
no it's not a particular one, it's just as I start scrolling through them it acts like it has crashed then takes me to the login screen. it's an nvidia graphics card, not sure of the exact model. thanks for your help.

---

### Post by khedron on 2007-07-02
Could you post the contents of /var/log/xorg.conf after you have crashed your session and logged on again?

---

### Post by mwk001 on 2007-07-03
yeah I did what you said and it told me: "No such file or directory"

---

### Post by khedron on 2007-07-03
Sorry, my mistake. I meant /var/log/xorg.log
xorg.conf is a different file...

---

### Post by mwk001 on 2007-07-03
tried that, but it also said "No such file or directory", thanks again for your help

---

### Post by khedron on 2007-07-03
Sorry, I am incompetent.
/var/log/Xorg.0.log
Try that one. (Teaches me to work from memory :()
If that doesn't work (and it should) get the first file listed by this command:
```
for i in /var/log/?org*; do echo "$i"; done
```Sorry for wasting your time.

---

### Post by mwk001 on 2007-07-09
Here are the contents:
mwk001@ss-5-53:~$ for i in /var/log/?org*; do echo "$i"; done
/var/log/Xorg.0.log
/var/log/Xorg.0.log.old


Thanks again for your help!

---

### Post by khedron on 2007-07-09
Ok, could you copy and paste the contents of **/var/log/Xorg.0.log** into a message, please? Could you put **&#091;[B]code]**[/b] in front of the contents, and **&#091;[B]/code]**[/B] at the end as well? This makes it easier to read.

Thanks for your patience ;)

---

### Post by mwk001 on 2007-07-13
Ok here is what I got
[code]

root@ss-5-53:/home/mwk001# /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied

[\code]

Not sure why it says Permission denied. Thanks again for your help.

---

### Post by Rui Pais on 2007-07-13
> **mwk001 said:**
> Ok here is what I got
```


root@ss-5-53:/home/mwk001# /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied

[\code]

Not sure why it says Permission denied. Thanks again for your help.

No :)
you need sudo to open that file. And a text editor ;)

It's too long and to boring anyway just past the output of:
[CODE]sudo cat /var/log/Xorg.0.log | grep  EE
```

---

### Post by mwk001 on 2007-07-13
Alright I did that and here is what I got:
```


mwk001@ss-5-53:~$ sudo cat /var/log/Xorg.0.log | grep EE
Password:
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER


```

Thanks again for your help.

---

### Post by Rui Pais on 2007-07-13
so no errors logged ...
have you done that after it logs you off?

check your screensaver config do make it log you off, 
then log in and past the output off:
```
sudo cat /var/log/Xorg.0.log | grep  EE
```

```
cat .xsession-errors
```

```
cat /etc/X11/xorg.cong | grep nv
```
please.

---

### Post by khedron on 2007-07-20
That last command should read ```
cat /etc/X11/xorg.conf | grep nv
```

---

