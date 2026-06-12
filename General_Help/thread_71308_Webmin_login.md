---
title: "Webmin login ??"
date: 2005-10-02
forum: General Help
---

### Post by dbee on 2005-10-02
Hi,

Did anyone have a problem logging in to webmin ??

I have read the manual and done everything that it suggested and I still can't seem to get into my webmin. I just get a login failed error

I've adjusted miniserv.conf, changed the changepass.pl, started and stopped the webmin service ... but still no luck

anyone have any suggestions ?

---

### Post by xmastree on 2005-10-12
Well, I have a slight problem which is why I found this thread... (searched for miniserv.conf)

Anyway, I edited my miniserv.conf to :```
allow=127.0.0.1
allow=192.168.1.18
```and I could access it from 192.168.1.18
So far so good.
Then I changed it to:```
allow=127.0.0.1
allow=192.168.1.18
allow=192.168.1.21
```since ...21 is the one I will mostly use for it, and found I could no longer access it from ...18 although I could from ...21

If you can't access it at all, I don't really know. I logged in as root, and I never touched changepass.pl

---

### Post by Lambert on 2005-10-22
When I first installed webmin, during config, I had a prompt saying it copied my root user password from my current file and to use that to access webmin. This didn't make sense as root is disabled on default, what did it copy?

After not being able to log in I found running this command will change the password

```
sudo /usr/share/webmin/changepass.pl /etc/webmin root *new_password*
```

After setting a password I could then log in.

---

### Post by dbee on 2005-10-23
cool, thanks guys

---

