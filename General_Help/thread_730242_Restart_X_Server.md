---
title: "Restart X Server?"
date: 2008-03-20
forum: General Help
---

### Post by LolTrevor on 2008-03-20
Well I updated the dual monitor setting and it says to restart x server. So I do that but when I reboot it just sits at a black screen goin _. Can anyone help me?

---

### Post by bodhi.zazen on 2008-03-20
boot to recovery mode

```
dpkg-reconfigure xserver-xorg
```

Reboot or

```
telinit 2
```

---

### Post by LolTrevor on 2008-03-20
I installed using wubi. So I don't have a recovery mode, and the command did nothing. Any more suggestions?

---

### Post by bodhi.zazen on 2008-03-20
well, wubi still boots to Ubuntu, no ?

So do you have access to a command line ?

If so, what is the output of :

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

??

---

### Post by LolTrevor on 2008-03-20
None worked. Nothin happend.

---

### Post by bodhi.zazen on 2008-03-20
what about ```
startx
```

error ?

---

### Post by steveneddy on 2008-03-20
Ctrl + Alt + Backspace won't work in wubi?

---

### Post by bodhi.zazen on 2008-03-20
> **steveneddy said:**
> Ctrl + Alt + Backspace won't work in wubi?

It should, but my guess is he has no X

> **LolTrevor said:**
> when I reboot it just sits at a black screen goin _. 

---

### Post by LolTrevor on 2008-03-20
> **bodhi.zazen said:**
> what about ```
startx
```

error ?

Tried and It doesn't give me any error messages.

Also tried CTRL + ALT + Backspace. Just made some wierd things like "]" and more stuff. No message.

---

### Post by bodhi.zazen on 2008-03-21
sounds very odd.

What about just X /
```
X
```

That is a cap X not a small x

you should get a gray screen with a large black X on it ...

Ctrl-Alt-Backspace to exit.

What about Ctrl-Alt-F7

Ctrl-Alt-F1 to return to the command line.

---

### Post by LolTrevor on 2008-03-21
Well, I got int o a command line and logged in in the command like but it says fatal server error. I think some things already in use is what it said.

---

### Post by bodhi.zazen on 2008-03-21
It is most helpful to post the exact error message. Is the first time you have gotten to a command line ?

What have you tried up to now ?

If this is the first time you are on the command line , try these commands:

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/inti.d/gdm start
```

---

