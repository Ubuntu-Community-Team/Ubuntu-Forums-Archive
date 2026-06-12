---
title: "close port 631 (IPP)"
date: 2007-01-13
forum: General Help
---

### Post by PetePete on 2007-01-13
i've just done a pport scan on myself and realised i have 631 (IPP) open, i dont have any printers installed on my computer so theres no need for any printing services to be running.

how do i stop the service from running? 

thanks

---

### Post by Hossie on 2007-01-13
```
sudo /etc/init.d/cupsys stop
sudo update-rc.d -f cupsys remove
```

---

### Post by PetePete on 2007-01-13
thanks :)

---

### Post by Amivit on 2007-10-01
> **Hossie said:**
> ```
sudo /etc/init.d/cupsys stop
sudo update-rc.d -f cupsys remove
```
Oops. I typed in the command to block my port but discovered I need this service!
How do I undo what I just did?
:confused:

---

### Post by pmg on 2007-10-01
I've never run update-rc.d by hand, but I think running **sudo update-rc.d cupsys defaults** will restore the symlinks used at system boot.  To start it by hand run **sudo /etc/init.d/cupsys start** .

---

### Post by Amivit on 2007-10-02
Fixed it, thanks alot.
Phew:)

---

