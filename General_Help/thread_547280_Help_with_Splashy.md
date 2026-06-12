---
title: "Help with Splashy"
date: 2007-09-09
forum: General Help
---

### Post by FuturePilot on 2007-09-09
I've installed Splashy and Splashy themes from the repos but I can't figure out how to set a theme. Here's what I've tried
```
sudo splashy_config --s /etc/splashy/themes/ubuntusplashy/
>Set theme as: /etc/splashy/themes/ubuntusplashy/          [ FAIL ]

```
It always fails.

---

### Post by FuturePilot on 2007-09-09
Doh, silly me. The command is
```
sudo splashy_config --s ubuntusplashy
```

Ok got that but when I go to test it I get
```
nick@FeistyFawn:~$ splashy test
nick@FeistyFawn:~$ Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
```

---

### Post by wjuniorr on 2007-09-09
Try this program:** [http://web.telia.com/~u88005282/sum/downloads.html](http://web.telia.com/~u88005282/sum/downloads.html)**

After post your result ok?!

Good luck! :)

---

### Post by FuturePilot on 2007-09-09
Thanks, but that does Usplash themes. Not Splashy themes;)

---

### Post by FuturePilot on 2007-09-10
Bump.

---

### Post by wjuniorr on 2007-09-10
> **FuturePilot said:**
> Thanks, but that does Usplash themes. Not Splashy themes;)

Ok friend, sorry about that! #-o

Good luck for you!!!

---

### Post by FuturePilot on 2007-09-12
Bump. 
Nobody uses Splashy?:-k

---

### Post by FuturePilot on 2007-09-13
I guess nobody uses Splashy then....:-s

---

### Post by bapoumba on 2007-09-14
Moved to "General Halp" ^^

---

### Post by FuturePilot on 2007-09-14
Hmm. Still seems broken in Gutsy.:-k

---

### Post by Shootfast on 2007-09-24
You have to sudo splashy test

And you will also have to edit the /etc/event.d/rcS file for splashy to work as its filed in [https://launchpad.net/ubuntu/+source/upstart/+bug/76304](https://launchpad.net/ubuntu/+source/upstart/+bug/76304) . Thats where I'm stuck. Anyone know a how to edit this in properly? And could they possibly post the contents of their rcS file?

---

### Post by el_itur on 2007-10-01
I've ran sudo splashy test and I've can't make it work.

It returns Splashy ERROR: Couldn't splashy_start_splashy(). Error -2

---

### Post by FuturePilot on 2007-10-02
Yep, sudo splashy test doesn't work either.

---

### Post by Jimmy_r on 2007-10-22
> **FuturePilot said:**
> Thanks, but that does Usplash themes. Not Splashy themes;)

Splashy support has been added as of version 1.9.5 :)

---

