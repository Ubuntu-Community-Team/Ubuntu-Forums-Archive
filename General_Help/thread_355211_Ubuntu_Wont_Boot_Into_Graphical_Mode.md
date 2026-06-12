---
title: "Ubuntu Wont Boot Into Graphical Mode"
date: 2007-02-06
forum: General Help
---

### Post by jasonpeinko on 2007-02-06
Im using (xfce).

I was using xfce, and i installed some games from synaptic. Then the menu stopped working to i decided to reboot. When ubuntu completely rebooted it took me into the text login. No matter what i do i cant get into the graphical login.

---

### Post by bodhi.zazen on 2007-02-06
Error message ???

Log in, try these commands, post any error messages:

1. ```
X
```

That should start a gray screen with a black X that moves with the mouse. Ctrl-Alt-Backspace to exit.

2. ```
startx
```

Does that start xfce ?

3. ```
xfce4-session
```

Does that start xfce ?

4. ```
sudo gdm
```

Does that start your log-in screen (gdm)?

---

### Post by jasonpeinko on 2007-02-06
x: displays correcly,
startx: does nothing
xfce4-session: sysmbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_hash_table_ref
sudo gdm: same error.

So im guessing that i need to reinstall gtk?

---

### Post by true_friend on 2007-02-07
try Ctrl+Alt+F1 to F7
may it start Display Manager

---

### Post by jasonpeinko on 2007-02-07
no. HELP i need to use my computer.

---

### Post by bodhi.zazen on 2007-02-07
You could try re-installing xfce :

```
sudo aptitude reinstall xubuntu-desktop
```

---

### Post by jasonpeinko on 2007-02-07
nope

---

### Post by mcduck on 2007-02-07
> **bodhi.zazen said:**
> 
4. ```
sudo gdm
```

Does that start your log-in screen (gdm)?

Shouldn't that be 'sudo /etc/init.d/gdm start' ;)

---

### Post by Maestro23 on 2007-02-07
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by bodhi.zazen on 2007-02-07
> **mcduck said:**
> Shouldn't that be 'sudo /etc/init.d/gdm start' ;)

sudo gdm works as well ;)

---

### Post by jasonpeinko on 2007-02-07
says starting gnome display manager

---

### Post by bodhi.zazen on 2007-02-07
> **jasonpeinko said:**
> says starting gnome display manager

And ...

Error message ?

If not, hit Ctrl-Alt-F7

---

### Post by jasonpeinko on 2007-02-08
I ment to say
it says

* String Gnome Display Manager...    [FAIL]

---

### Post by jasonpeinko on 2007-02-08
should i just reinstall ubuntu?

---

### Post by jasonpeinko on 2007-02-08
or is there a way to fix from boot cd?

---

### Post by bodhi.zazen on 2007-02-08
You could try the Ubuntu irc ...

irc://irc.freenode.net/#ubuntu

Otherwise I can not solve the problem at the moment and no one else has offered better advice ...

Sorry you have to re-install ...

---

### Post by jasonpeinko on 2007-02-08
is there a way to overwrite a installation? just the system files? so all my stuff is still there?

---

### Post by cleentrax on 2007-02-08
If you have more than one kernel installed, you could try booting from an older kernel in GRUB.

---

### Post by jasonpeinko on 2007-02-08
i dont think so, could i download another through apt or someting?

---

