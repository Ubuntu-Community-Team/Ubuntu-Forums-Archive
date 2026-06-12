---
title: "Per application keyboard layout settings?"
date: 2007-05-20
forum: General Help
---

### Post by BisonDesPrairies on 2007-05-20
Hi,

I use 2 keyboard layouts and switch between them on a per-application basis. I use fr_CA by default and en_US in terminal/console windows.

If I open a console and change the layout, it only applies to the current window, this is want I want. The problem is the system doesn't remember the layout setting the next time I launch a console. Is there a way to do this? A parameter on the command line to start the application or something else?

Thanks!

---

### Post by t[h]inker on 2007-05-21
I had the same problem with CZ/US keyboard layouts using tvtime. Buttons on my IR controler are mapped like "+&#283;š&#269;&#345;žýáíé" with CZ layout instead of "1234567890" (which is pretty correct, but tvtime does not recognizes it :(). So I needed to start tvtime *always* with US layout *and* preserving CZ for every other application. No bloody way to set this via some parameter on command line for me, alas.

So this is very ugly workaround I found, but it works well:

**1.** Make sure You have the option "Group per window" enabled (I suppose You already have).
**2.** Make sure You have the fr_CA layout as first and en_US as the second.
**3.** Now make a launcher for Your terminal (on panel or wherever), and copy this to the "command" field:```
sh -c "gconftool --type int --set /desktop/gnome/peripherals/keyboard/general/defaultGroup 1 && gnome-terminal & sleep .1 &&  gconftool --type int --set /desktop/gnome/peripherals/keyboard/general/defaultGroup 0"
```
**4.** Enjoy! (If it works for You, I hope so)

---

### Post by louis-gabriel on 2008-01-10
I had the same wish as BIsonDesPrairies, and your fix worked great!

Thanks!

---

### Post by brunovecchi on 2008-01-16
Thanks! your solution was helpful to change my keyboard distribution when using gvim!
(I have a spanish keyboard, and vim commands are awkard with a spanish distribution)

---

### Post by kclinda on 2008-01-20
> **brunovecchi said:**
> Thanks! your solution was helpful to change my keyboard distribution when using gvim!
(I have a spanish keyboard, and vim commands are awkard with a spanish distribution)

I'm having this problem.
I have an spanish keyboard and I'm not able to put the accents and so.
I realized that my keyboard according to ubuntu's layout is Spain and not Latin American as I though, but I still have problems writing...

BTW, I don't know if it my help, but my locale shows this: 
> LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=


If I'm not mistaken, I should have the CTYPE as spanish...

I'm quite new, so be gentle :)

---

