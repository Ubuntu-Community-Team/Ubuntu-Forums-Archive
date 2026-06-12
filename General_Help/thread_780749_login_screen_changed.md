---
title: "login screen changed"
date: 2008-05-03
forum: General Help
---

### Post by conehead77 on 2008-05-03
Hi,
i tried the slim login manager instead of gdm, but i want to get gdm back now.
Does anybody know how to do that?

---

### Post by ozorba on 2008-05-03
System > Administration > Login Window 

enter your password and then select "Local" tab at the top. Pick your GDM!

---

### Post by conehead77 on 2008-05-03
> **ozorba said:**
> System > Administration > Login Window 

enter your password and then select "Local" tab at the top. Pick your GDM!

I cant open it, i get a error message:
```

GDM (GNOME Display Manager) is not running
You might be using a different display manager, such 
as KDM (KDE Display Manager), CDE login (dtlogin), or 
xdm. If you wish to use this feature, then your system 
will need to be configured to use GDM instead.
```

EDIT: I googled the error message and found the solution, problem solved now. Thanks for caring :)

---

### Post by El_Belgicano on 2008-06-14
Could you please post your solution? It could prove it's useful in some days when I'll give Slim a try ...

---

### Post by conehead77 on 2008-06-14
> **El_Belgicano said:**
> Could you please post your solution? It could prove it's useful in some days when I'll give Slim a try ...

If i remember correct, i just ran
sudo dpkg-reconfigure gdm

There you can choose your default login manager. If i remembered wrong, try one of these:
[http://www.google.de/search?hl=de&q=GDM+(GNOME+Display+Manager)+is+not+running+You+might+be+using+a+different+display+manager%2C+such++as+KDM+(KDE+Display+Manager)%2C+CDE+login+(dtlogin)%2C+or++xdm.+If+you+wish+to+use+this+feature%2C+then+your+system++will+need+to+be+configured+to+use+GDM+instead.&btnG=Google-Suche&meta=](http://www.google.de/search?hl=de&q=GDM+(GNOME+Display+Manager)+is+not+running+You+might+be+using+a+different+display+manager%2C+such++as+KDM+(KDE+Display+Manager)%2C+CDE+login+(dtlogin)%2C+or++xdm.+If+you+wish+to+use+this+feature%2C+then+your+system++will+need+to+be+configured+to+use+GDM+instead.&btnG=Google-Suche&meta=)

---

### Post by El_Belgicano on 2008-06-14
Thank you for that really fast reply :) Amazing ...

---

### Post by conehead77 on 2008-06-14
> **El_Belgicano said:**
> Thank you for that really fast reply :) Amazing ...

Well im still subscribed to this thread and get a email when somebody posts here :)

Good luck with Slim!

---

