---
title: "Unetbootin - Not accepting my password"
date: 2013-06-24
forum: General Help
---

### Post by carmen2012 on 2013-06-24
I only have one account on my Ubuntu 13.04 install and that is the one that was setup during the installation of Ubuntu.  After the install and all of the system updates, I installed Unetbootin through the Ubuntu Software Center.

When I click on the icon to try and run it, it asks for the administrator password and when I enter the password that I use to log on to my computer, it says that the password is invalid.  I do not have any other passwords or accounts associated with this computer.

Would anyone know if there is a default password or how I can get this application to run?

Thank you

---

### Post by Vormeph on 2013-06-24
There are no other passwords associated when you create one. You should be able to use Unetbootin using your system password. Remember, passwords are case-sensitive. There is the possibility that your ROOT password is different from your USER password. By default, your root password is the same as your user password.

---

### Post by snowpine on 2013-06-24
Try launching it by pressing Alt+F2 and typing:

```
gksu unetbootin
```

---

### Post by carmen2012 on 2013-06-24
> **snowpine said:**
> Try launching it by pressing Alt+F2 and typing:

```
gksu unetbootin
```

Thanks for the command.  It didn't work, but I did find a similar command that did work.  It was

1.  Go to a terminal session
2.  Type sudo unetbootin.

---

### Post by MidnightGrey on 2013-06-24
wait **gksu unetbootin** didnt work, but **sudo unetbootin** worked?? 
how is that possible.

---

### Post by snowpine on 2013-06-24
I agree with MidnightGrey; gksu (not sudo) should be used for graphical apps, and if gksu is not properly configured, it may point to a larger problem.

More info here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Irihapeti on 2013-06-24
Possibly a problem that's easily fixed, though.

Open a terminal and enter the command: gksu-properties

You'll get a small gui. Make sure that you have sudo (not su) chosen as authentication mode. Then close.

gksu should work properly after that.

---

### Post by carmen2012 on 2013-06-25
> **Irihapeti said:**
> Possibly a problem that's easily fixed, though.

Open a terminal and enter the command: gksu-properties

You'll get a small gui. Make sure that you have sudo (not su) chosen as authentication mode. Then close.

gksu should work properly after that.

Not that I understand what is the difference between sudo and gksu, but I tried it once more and sudo unetbootin worked, gksu did not.

I then made the above change and then tried gksu unetbootin and it now works.

Does it really matter whether I use sudo unetbootin or gksu unetbootin and if so, could someone tell me why?

Thank you

---

### Post by claracc on 2013-06-25
Here, you have explanation of difference between sudo and gksu: [http://www.highgeekvalue.com/2012/08/the-difference-between-sudo-gksu.html](http://www.highgeekvalue.com/2012/08/the-difference-between-sudo-gksu.html)

---

