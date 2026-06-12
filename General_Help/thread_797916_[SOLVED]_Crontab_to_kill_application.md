---
title: "[SOLVED] Crontab to kill application"
date: 2008-05-17
forum: General Help
---

### Post by FooAtari on 2008-05-17
I have the following cron to control Usenet downloads.  It worked great when I was using Ubuntu;
```

#kill klibido
00 00 * * * allie killall klibido

#start stunnel
05 00 * * * root stunnel4 /etc/stunnel/stunnel.conf

#start klibido
10 00 * * * allie export DISPLAY=:0 && kdocker /usr/bin/klibido -r

#kill stunnel4
36 23 * * * root killall stunnel4
```

However since moving to Kubuntu it no longer seems to kill stunnel4.  That or it starts again straight away...  Any ideas?

doing 
```
sudo kill stunnel4 
```
from the termina works fine

---

### Post by FooAtari on 2008-05-18
Anyone?

---

### Post by ibuclaw on 2008-05-18
Run all "killall" scripts as root then.

That seems the most logical way to do it.
You can specify to do it for only "your" user too.

```
00 00 * * * root killall -u allie klibido
```

Hope that helps.

Regards
Iain

---

### Post by FooAtari on 2008-05-18
Thanks, but I'm not sure that helps, but maybe that's my lack of understanding...

I want to control when downloads are allowed, and also have klibido open at all time so I can monitor downloads.

So I want to enable downloading after midnight.  So I close klibido;

```
#kill klibido
00 00 * * * allie killall klibido
```

start stunnel4 for the secure connection;
```

#start stunnel
05 00 * * * root stunnel4 /etc/stunnel/stunnel.conf
```

And reopen klibido

```
#start klibido
10 00 * * * allie export DISPLAY=:0 && kdocker /usr/bin/klibido -r
```


Then the easitest way to stop downloads before 4pm, without closing klibido seemed to be to kill the secure connection, so I did;
```

#kill stunnel4
50 15 * * * root killall stunnel4
```

But that seems to have no effect, stunnel remains running after that time, and that's my problem.

---

### Post by FooAtari on 2008-05-18
Clear it wasnt setup like I thought in ubuntu.

When I edited roots cron;

```
crontab -e -u root
```

And entered the commands to start and stop stunnel4 it worked fine.

---

