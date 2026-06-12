---
title: "httpd keeps restarting and blocking apache2"
date: 2018-05-28
forum: General Help
---

### Post by sonocseos on 2018-05-28
Hi,

I have the following problem: if I stop apache2 by

```
sudo service apache2 stop
```

Immediately an httpd instance rises and blocks port 80:

```
sudo netstat -ltnp | grep ':80'
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN      1128/python         
tcp6       0      0 :::8000                 :::*                    LISTEN      1128/python         
tcp6       0      0 :::8096                 :::*                    LISTEN      886/EmbyServer      
tcp6       0      0 :::80                   :::*                    LISTEN      19511/httpd         

```

If I issue

```
sudo kill -9 19511
```

Immediately httpd restarts, and I cannot start apache2.

```
sudo netstat -ltnp | grep ':80'
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN      1128/python         
tcp6       0      0 :::8000                 :::*                    LISTEN      1128/python         
tcp6       0      0 :::8096                 :::*                    LISTEN      886/EmbyServer      
tcp6       0      0 :::80                   :::*                    LISTEN      21299/httpd


```
Can anybody help me? thanks in advance.

---

### Post by TheFu on 2018-05-28
systemd appears to be configured to restart the httpd, so killing it just has it restarted.  Disable the restart, if that isn't something you want.  **systemctl** is the command.
I would remove the httpd package, if I wanted apache as the web server instead.  At least disable the httpd service; I think that is the enable/disable options to systemctl.

It is a bad idea to kill -9 things.  I haven't needed to kill -9 anything in a very long time, maybe 5+yrs.  The tools to control services work pretty well.

---

### Post by sonocseos on 2018-05-29
Thanks for your help.

Your indication did not solve my issue, as this is the result of using systemctl disable:

```
sudo systemctl disable httpd
Failed to disable unit: Unit file httpd.service does not exist.

```

However, it set me on the right way. I tried ```
sudo systemctl status
```and found this line:

```
21299 httpd -d /snap/nextcloud/6916 -k start -DFOREGROUND
```

This is an old installation of nextcloud I thought I had already removed. Anyway, the next step was

```
sudo snap remove nextcloud
```

and httpd disappeared. Now apache2 works correctly.

Thanks again.

---

