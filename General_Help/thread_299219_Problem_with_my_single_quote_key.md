---
title: "Problem with my single quote key"
date: 2006-11-13
forum: General Help
---

### Post by Reeves1016 on 2006-11-13
These is something wrong with my single quote key.

When i wanna input a single quote,i must press the key twice,and it can't be identified when i telnet to a AIX and send a sql with single quote to a db2 database.

And it is worse with double quote:I wanna input a ",but it gives me a ¨.Can u find the difference??yeah ,the ascii of " is 22(HEX),but i get a double quote ¨ with ascii A8(HEX),it's really awful.

Sorry 4 my bad Englise,I'm a Chinese.And i hava post a thread in my locale forum,but it seems nobody can answer it.There are several people have the same problem in my locale forum.

I need help.

---

### Post by sjm on 2006-11-15
hi, i'm using debian with KDE (I think ubuntu uses Gnome)

I've been having the same problem as you and have just fixed it by changing my keyboard layout from US to UK. So you probably have a similar problem - your keyboard layout is incorrect.

[This guide]("http://www.gnome.org/learn/users-guide/latest/prefs-keyboard.html") might set you on the right path.

---

### Post by dl7und on 2006-11-20
> **Reeves1016 said:**
> These is something wrong with my single quote key.

I think it is not just your single quote, but also the double quote - and I got the same problem. I think it is not a problem of having chosen the wrong layout, but more a problem with the layout settings. I have to use an US layout, since that is what keyboards in Taiwan are arranged like.

So now (since I freshly installed Edgy) I have to press both single and double quote twice to get the weird character (definitely not the real quote sign) Reeves spoke about. Otherwise, if I press it once and then a letter, they may well be combined. Oh, the same applies to ^...

For both US and UK layouts I encounter these problems. If I switch to German layout, everything (quotation marks) seems to work just fine. So, could it be that some keyboard layouts got messed up? And if, how/where can I modify them?

---

### Post by dl7und on 2006-11-20
OK, I may have a solution. Unfortunately, Gnome does not offer a working layout, so I went into xorg.conf:
```
sudo nano -w /etc/X11/xorg.conf
```

In the keyboard layout, I replaced "pc105" with "pc104" (not sure if this is really necessary) and changed the "XkbVariant" from "intl" to "basic".

Restarting Gnome after these two modifications made it complain that the Xorg settings were different from the Gnome settings, so I should pick which I wanted to use. Going for the Xorg settings, things have been working fine since.

I never encountered this before on any Linux distribution, including Ubuntu's. Very strange that the included layouts would cause such trouble...

---

### Post by jinks on 2006-12-07
Thanks dl7und!  Changing the Xorg.conf to the settings you specified worked perfectly for me.

---

### Post by ceswiedler on 2007-10-04
How I fixed this: Go to System -> Preferences -> Keyboard, switch to the Layouts tab. I had the "US English International" layout (apparently this is the problem). Click Add and select "US English". It's strange because it looks like it's a group, not an actual layout, but you can select it individually. Click OK and then apply the changes.

---

### Post by dl7und on 2007-10-05
Interesting. Just this week I solved this annoyance (again), but slightly differently. After upgrading to Feisty, the method I mentioned above (and which is usually recommended everywhere) did not work any longer. Gnome did not care at all what I would write into xorg.conf...

So I went directly to this file:
```
~/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml
```
There I modified the the keyboard name from US International something to just "us" and deleted the options. I suppose that did the same as ceswiedler's method, just "manually"...

---

### Post by nooblot on 2007-10-20
forget about editing xorg.conf

just  follow post#6 , works for me

---

