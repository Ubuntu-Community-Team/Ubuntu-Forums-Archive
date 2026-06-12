---
title: "Root Terminal"
date: 2007-03-27
forum: General Help
---

### Post by donmor on 2007-03-27
Hello.
New to Ubuntu and loving it.
How does one get into a root terminal?
Su only gets  Unauthorized.

Thanks for any help.

Don

---

### Post by 23meg on 2007-03-27
```
sudo -i
```

---

### Post by kerry_s on 2007-03-27
sudo<-command line command
gksu<-command line graphical launcher, can also use gksudo, but it's just a link to gksu.

---

### Post by Jose Catre-Vandis on 2007-03-27
The safer way is just to run commands prefixed with a sudo e.g.
```
sudo thiscommand
Password: <specify password>
sudo thatcommand
(no need for password up to 15 minutes)
``` 
 - stops you running stuff in root and forgetting you are. This is by design in Ubuntu.

If you really want a root terminal:
```
sudo -s -H
Password: <specify user password>
```

---

### Post by 23meg on 2007-03-27
Here's more information on sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by donmor on 2007-03-29
Thank you all for your reply.
Got things working just nice.
Once again thanks.

Don

---

