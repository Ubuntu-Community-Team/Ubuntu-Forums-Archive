---
title: "Hibernate question"
date: 2013-03-24
forum: General Help
---

### Post by roly33 on 2013-03-24
Is it possible to put a Laptop in Hibernate or not, as on my 13.04 Pre-Release system the Hibernate option is in Power settings but it's grayed out?

Roland

---

### Post by Gwaro on 2013-03-24
Well I did this to my Ubuntu 12.04 box and it worked (I haven't tried 13.04 yet):

 Check whether your machine supports hibernation
    
    ```
sudo pm-hibernate
```

If the hibernate test works, you can continue to use the sudo pm-hibernate command when you want to hibernate.

You can also enable the hibernate option in the menus. To do that, use your favorite text editor to create /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
Add the following to the file and save:
```

[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```

---

### Post by roly33 on 2013-03-24
> **Gwaro said:**
> Well I did this to my Ubuntu 12.04 box and it worked (I haven't tried 13.04 yet):

 Check whether your machine supports hibernation
    
    ```
sudo pm-hibernate
```

If the hibernate test works, you can continue to use the sudo pm-hibernate command when you want to hibernate.

You can also enable the hibernate option in the menus. To do that, use your favorite text editor to create /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
Add the following to the file and save:
```

[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```

I've created the file, but when I try to save I get a Permission error.

[ATTACH=CONFIG]240490[/ATTACH]

Roland

---

### Post by Gwaro on 2013-03-24
You need root privilages to create the file.

```

sudo gedit /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

```

---

### Post by roly33 on 2013-03-24
> **Gwaro said:**
> You need root privilages to create the file.

```

sudo gedit /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

```

That worked thanks.

Roland

---

### Post by Gwaro on 2013-03-24
> **roly33 said:**
> That worked thanks.

Roland

Welcome.

---

