---
title: "avoid inadvertent non-breaking space"
date: 2014-12-27
forum: General Help
---

### Post by mättu on 2014-12-27
How do I avoid having non-breaking space inserted?

It happens in libreoffice, vi, mysql..

While hacking, it is especially annoying to have non-breaking space inserted after characters like "=", "*" etc. 
Therefore, in .vimrc, I have a line 
```
%s/\%xa0/ /e
```to replace non-breaking whitespace with "regular"*whitespace whenever I*save a file.

In a mysql console, a simple command like 
```
select * from my_table
```fails with an "ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '*from my_table' at line 1".
```
mysql> select *from student;
```however works.

I do not mind to loose non-breaking space completely. All I want is a simple space whenever I push "space". 

I can see "it"*inserts non-breaking space by pasting the strings in question into [http://www.htmlescape.net/htmlescape_tool.html](http://www.htmlescape.net/htmlescape_tool.html)
(If you wonder where the "*" in the sentence above is from.. That is what ubuntuforums  produced when I type '"-space'.)


Here is my locale:
LANG=de_CH.UTF-8
LANGUAGE=de_CH:de
LC_CTYPE="de_CH.UTF-8"
LC_NUMERIC="de_CH.UTF-8"
LC_TIME="de_CH.UTF-8"
LC_COLLATE="de_CH.UTF-8"
LC_MONETARY="de_CH.UTF-8"
LC_MESSAGES="de_CH.UTF-8"
LC_PAPER="de_CH.UTF-8"
LC_NAME="de_CH.UTF-8"
LC_ADDRESS="de_CH.UTF-8"
LC_TELEPHONE="de_CH.UTF-8"
LC_MEASUREMENT="de_CH.UTF-8"
LC_IDENTIFICATION="de_CH.UTF-8"
LC_ALL=

---

### Post by schragge on 2014-12-28
Does non-breaking space get inserted each time you press Space key or only after certain characters? From looking into */usr/share/X11/xkb/symbols/ch* I see that non-breaking space on the Swiss-German keyboard gets inserted when you press Shift+Space. Can it be a faulty keyboard that always sends codes for Shift+Space instead of Space?

---

### Post by mättu on 2014-12-28
Thanks. 
I am not 100% sure yet, but I think I really happen to push Shift too long. Ending in a non-breaking space. Hrmpfs.
To be sure, I changed the respective line in /usr/share/X11/xkb/symbols/ch to ```
   key <SPCE> { [&#8594; space, &#8594;space,&#8594; space&#8594;  &#8594;   ]&#8594;  };
``` and deleted the xkb cache. ```
sudo rm /var/lib/xkb/*.xkm
```
After a reboot (I think a restart of X would be enough.) I am now unable to produce a non-breaking space. Nice!

A good write-up with examples on how to change key bindings can be found here: [http://rlog.rgtti.com/2014/05/01/how-to-modify-a-keyboard-layout-in-linux/]("http://rlog.rgtti.com/2014/05/01/how-to-modify-a-keyboard-layout-in-linux/")

I think I am actually going to play around with that a bit more. On my keyboard there are quite a few things left to improve..

---

### Post by schragge on 2014-12-29
The problem is your change to that file will get overwritten on the next update of *xkb-data*. A much better approach is just to put
```

XKBOPTIONS="nbsp:none"

```
into */etc/default/keyboard*.

---

### Post by Holger_Gehrke on 2014-12-29
> **mättu said:**
> Thanks. 
I am not 100% sure yet, but I think I really happen to push Shift too long. 

Might be an unwanted feature, not a bug. Check the state of accessibility ('Barrierefreiheit') keyboard settings. 'Sticky Keys' are meant for people who can't type normally (think of a paraplegic typing with a stick held with his lips ...)

---

### Post by mättu on 2014-12-29
Thank you for the hint.
Sticky keys and all that are off.
Anyways, with my current setup I am more than happy now.

It was just that I found my environment to be almost unusable, did not remember when that started, and was trying to find a solution that worked for me. Also, thanks to you people caring here in the forums, I have been able to even go beyond the point of simply removing "the nuisance". With my modified keyboard layout I am even more productive than I would be with the standard layout.
It was only the original issue that got me the understanding. Really nice.

---

### Post by mättu on 2014-12-29
Point taken. :-)

Thank you for the advice.

I think the correct way was to define a new keyboard layout and make that available to the system. Until then, I just keep a copy of my layout in a save place (my home) and link that back to the original when needed.

---

### Post by schragge on 2014-12-29
Unfortunately, extending XKB rules is not quite so simple as it should be. [Here]("http://madduck.net/docs/extending-xkb/") is a good write-up by Debian developer Martin Krafft aka madduck (he's also Swiss by the by).

---

