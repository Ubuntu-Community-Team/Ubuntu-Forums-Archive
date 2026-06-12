---
title: "Login screen does not obey config file"
date: 2015-04-09
forum: General Help
---

### Post by rdh61 on 2015-04-09
Hi,

I am running Lubuntu 14.04 LTS. I do not want my login screen to appear at start up. I have modified my lxdm.conf file (at /etc/xdg/lubuntu/lxdm/lxdm.conf) in order to achieve this. (See manpage at [http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html))

By default the top of the file reads:

```
[base]
## uncomment and set autologin username to enable autologin
# autologin=dgod

## uncomment and set timeout to enable timeout autologin,
## the value should >=5
# timeout=10
```

I have uncommented and modified as follows:

```
[base]
## uncomment and set autologin username to enable autologin
autologin=myusername

## uncomment and set timeout to enable timeout autologin,
## the value should >=5
timeout=5
```

I saved the modified file. Nevertheless, every time I boot, the login screen appears and, although I can login just by hitting enter without putting in my password, it does not log in automatically after 5 seconds as I have specified.

I would like either (a) the login screen not to appear, or (b) automatic login after a few seconds.

I would like to know why may actions have not resulted in the desired behaviour, and how I can achieve this behaviour.

Many thanks for any suggestions.

---

### Post by steeldriver on 2015-04-09
Are you actually using lxdm as the display manager? I thought Lubuntu had switched over to lightdm by default. What does

```

cat /etc/X11/default-display-manager 

```

say?

---

### Post by rdh61 on 2015-04-10
> **steeldriver said:**
> Are you actually using lxdm as the display manager? I thought Lubuntu had switched over to lightdm by default. What does

```

cat /etc/X11/default-display-manager 

```

say?

Ah...

```
robert@robert-P4i65GV:~$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm
```

Thank you!

So to /etc/lightdm/lightdm.conf I added:

 autologin-user=robert 
autologin-user-timeout=0

Now I have my desired behaviour, i.e. no login screen.

I'll just add that I was looking to do this because even though in System Tools -> Users and Groups (User settings) I had set it to "Password: Not asked on login", the login screen still appeared. Solved now.

---

