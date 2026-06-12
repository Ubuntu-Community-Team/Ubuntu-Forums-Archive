---
title: "ubuntu(13.10 &amp; 14.04 beta) takes too long to start on my laptop"
date: 2014-04-13
forum: General Help
---

### Post by AbhimanyuAryan on 2014-04-13
It takes too long at the black screen with blinking underscore icon & after that a message display on the blackscreen saying:  [ 18.052332] usb 1-1.1: string discriptor 0 read error: -22 


Also when I input the password on login screen and login to ubuntu....for a minute i don't see sidebar & icons on screen. After a minute i see everything on screen. How can i fix this. Make ubuntu 14.04 superfast in bootup & other things(just like Mac OSX)  :) :)

---

### Post by tripp98 on 2014-04-13
Please tell us the hardware you are running on.

---

### Post by AbhimanyuAryan on 2014-04-13
I am running it on acer aspire E1-571G (Laptop)

---

### Post by AbhimanyuAryan on 2014-04-13
How can list all the laptop's specs?

---

### Post by CharlesA on 2014-04-14
[http://www.notebookcheck.net/Review-Acer-Aspire-E1-571G-Notebook.88806.0.html](http://www.notebookcheck.net/Review-Acer-Aspire-E1-571G-Notebook.88806.0.html)

Also:

```
sudo lshw
```

```
 sudo lspci
```

---

### Post by AbhimanyuAryan on 2014-04-14
Sir how can i fix this error?

---

### Post by buzzingrobot on 2014-04-14
You need to provide the results of the two commands shown above, which will list your hardware specifications. Performance issues are most often hardware-related.

The USB-related error message might, as a guess, be due to an unsuccessful attempt to read from a USB device. The system would make repeated attempts to do that before giving up and displaying that message.  If you have a USB device attached, try booting with it unattached.

---

### Post by AbhimanyuAryan on 2014-04-15
Ok i fixed it thanks :)

---

### Post by mörgæs on 2014-04-15
Please post how in order to help other people with similar hardware.
Also please mark the thread 'solved' using 'thread tools'.

---

### Post by syedmohdabbasmehdi on 2014-05-22
> **AbhimanyuAryan said:**
> Ok i fixed it thanks :)


i am also facing exactly the same problem on my DELL XPS M1330.
please post the solution for this problem, how did you fix it?

---

