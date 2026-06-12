---
title: "With XGL / Compiz Num Lock doesn't work..."
date: 2006-07-24
forum: General Help
---

### Post by nemesa on 2006-07-24
Arhh.... The LED isn't on and I can't turn off / on the num. pad... 
Without XGL / Compiz, everything is fine...

---

### Post by richbarna on 2006-07-24
Yup, everyone has keyboard problemss with Xgl/Compiz.

Try reconfiguring your keyboard modmap like this :-
> xmodmap /usr/share/xmodmap/xmodmap.[COLOR=Red]us[/COLOR]

Or your keyboard country code, mine is Spanish [COLOR=Red]es[COLOR=Black].[/COLOR][/COLOR]

---

### Post by tzulberti on 2006-10-11
Thanks, that solved the problem I was having...

---

### Post by koshari on 2006-11-01
i also had the same problem but i had to use

```
xmodmap /usr/share/xmodmap/xmodmap.us-101
```

because cont and alt stopped working

---

### Post by johnny9794 on 2006-11-02
> **koshari said:**
> i also had the same problem but i had to use

```
xmodmap /usr/share/xmodmap/xmodmap.us-101
```

because cont and alt stopped working

Well my xgl-compiz combination keys did not work with

```
xmodmap /usr/share/xmodmap/xmodmap.us
```

untill i tried

```
xmodmap /usr/share/xmodmap/xmodmap.us-101
```

to fix my numlock problem. Did not help with the numlock, but did help in the xgl/compiz combo keys :)

Thanx koshari

---

