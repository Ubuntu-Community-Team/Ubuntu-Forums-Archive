---
title: "Possible to auto-login with domain account?"
date: 2014-07-07
forum: General Help
---

### Post by Tim_Graffam on 2014-07-07
I have a lubuntu 14 machine added to our Windows Domain and able to log in using domain credentials. 

Im wondering if anyone has had any success configuring auto login with domain credentials. 

I've tried configuring lightdm.conf as outlined [here]("http://www.htpcbeginner.com/enable-lubuntu-auto-login/"), but still getting a prompt to login which defaults to the local lubuntu "admin" account.

If this isnt possible, anyone know if the login screen can at least default to "Other..." so I dont have to manually choose that every time?

Thanks a bunch!

---

### Post by deadflowr on 2014-07-07
I think that link is already deprecated.
Here's the latest how-to's, as far as lightdm on Ubuntu goes.
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by Tim_Graffam on 2014-07-08
Excellent! While the article I posted did touch on the lightdm method, this page helped me figure out exactly how to auto login with a domain account. Thanks!

In case anyone comes across this in the future, this is what I ended up using in my /etc/lightdm/lightdm.conf:
```
[SeatDefaults]
autologin-user=username@domain.local
autologin-user-timeout=1
```

The part I was missing was adding *@domain.local* to the user name (replacing with your domain of course) and setting *autologin-user-timeout* to 1. I originally tried without including timeout at all and also with it set to zero, both of which would not auto login. Once I set to 1, it logged in as it should.

Thanks again for the help!

---

