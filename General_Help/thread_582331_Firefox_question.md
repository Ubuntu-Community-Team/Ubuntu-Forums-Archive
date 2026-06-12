---
title: "Firefox question"
date: 2007-10-19
forum: General Help
---

### Post by Brizoken on 2007-10-19
Alright, I had firefox when I was on Windows XP like 10 hours ago:D (Yeah im new to it all)

and I have a 5 button wireless mouse, and i used to use my two side buttons for forward and back (A lot of people do; do this.) but now it wont work, is there a way, or a plugin or anything i can do, to get this working again? (It's an annoyance to have to always hit the actual back button.)

---

### Post by rfruth on 2007-10-19
what does a 5 button mouse have to do with Firefox :confused:  -  no matter does the manufacturer of the mouse have a linux driver ?

---

### Post by Brizoken on 2007-10-19
I know it's not my mouse drivers, atleast im 98% sure.

I think it has something to do with ubuntu and or firefox.

I use to have MOUSE4 and MOUSE5 as shortcuts for forward and back...

---

### Post by rfruth on 2007-10-19
need to narrow it down, don't run Firefox at all (for now) - all mouse buttons work ?  (what make mouse (Logitech) ?

---

### Post by Brizoken on 2007-10-19
Yeah, I just tested it, and all 5 buttons work.

And its a Microsoft IntelliMouse 2.0 (A couple of years old, but a 5 button wireless.)

---

### Post by bodhi.zazen on 2007-10-19
See if this helps : [http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/](http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/)

[http://dotnet.org.za/matt/pages/39097.aspx](http://dotnet.org.za/matt/pages/39097.aspx)

Of course you could also contact Microsoft and ask for the Linux drivers for your mouse ...

---

### Post by Brizoken on 2007-10-20
I tried both of those, when I opend up my conf, there was nothing in there.. so I didnt know what to do..

---

### Post by bodhi.zazen on 2007-10-20
> **Brizoken said:**
> I tried both of those, when I opend up my conf, there was nothing in there.. so I didnt know what to do..

You have to open the file as root :

```
gksu gedit /etc/X11/xorg.conf
```

Always a good idea to back up first ...

---

