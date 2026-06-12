---
title: "Sudden Death"
date: 2007-07-14
forum: General Help
---

### Post by LiveRock on 2007-07-14
Hi

I installed Feisty LAMP Server and all was working... but suddenly, today, I can access the server at all (remotely)

(a) I cannot access using SSH
(b) I cannot access WEBMIN using browser
(c) I can ping to the machine
(d) My iptables are normal
(e) All I can remember I did the previous day was to plug a video encoder device into the USB port. Ubuntu complained of some errors but later I just unplugged it.
(f) I can do apt-get update so it should be connecting to the internet without problems.
(g) On booting, there is no errors at all.
(h) It is set to have DHCP and obtain a PUBLIC address from my router and setting it in the DMZ area
(i) It was working just a day ago!!

I am newbie in Linux and has no idea how to fix it; only way I know is to reinstall Ubuntu all over again.
That will fix it but I will learn nothing :-(

HELP!!!

---

### Post by apoth on 2007-07-14
Don't reinstall yet!

Do you get ssh access back if you run:

```
sudo /etc/init.d/ssh restart
```

---

### Post by apoth on 2007-07-14
And does it just time out for connecting to webmin or do you get an error page?

Does this affect it:

```
sudo apache2ctl restart
```

---

### Post by LiveRock on 2007-07-14
>>>>>And does it just time out for connecting to webmin or do you get an error page?

It took a long time and in the end, it shows a timed-out message.

I even do a 'dpkg-reconfigure webmin' and there are no errors and says I can access webmin.

------------------------------------------------------------------------------------------

I am out of town now so I will try what you suggest when I am back... Thanks!!

>```
sudo apache2ctl restart
```
>```
sudo /etc/init.d/ssh restart
```

---

