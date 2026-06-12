---
title: "conky"
date: 2014-03-05
forum: General Help
---

### Post by NyteRukh on 2014-03-05
im trying to setup conky..i followed the directions on setting it up and installing it...and i  downloaded sample .conf files to put in the .conkyrc folder in my /home/james folder but when i go to start it i get an error msg
This program is calling the Imlib call:

imlib_context_free();

With the parameter:

context

being NULL. Please fix your program.
what did i do wrong or what am i missing

---

### Post by Habitual on 2014-03-05
```
conky -v
``` output please.

---

### Post by NyteRukh on 2014-03-05
Conky 1.9.0 compiled Fri May 10 23:14:47 UTC 2013 for Linux 3.2.0-37-generic (x86_64)


Compiled in features:


System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky


 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual


 Music detection:
  * Audacious
  * MPD
  * MOC
  * XMMS2


 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * config-output
  * Imlib2
  * apcupsd
  * iostats
  * ncurses
  * Lua


  Lua bindings:
   * Cairo
   * Imlib2

---

### Post by NM5TF on 2014-03-05
you seem to have an older version....

my version looks like this.... 

```

tommy3@tommy3-Inspiron-531s:~$ conky -v
Conky 1.9.0 compiled Wed Feb 19 18:44:57 UTC 2014 for Linux 3.2.0-37-generic (x86_64)

``` 

you might try this...

```
sudo apt-get update
```

and then try...

```
sudo apt-get upgrade
```

and finally try this...



```
sudo apt-get dist-upgrade
```

tommy

---

### Post by vasa1 on 2014-03-05
> **NyteRukh said:**
> im trying to setup conky..i followed the directions on setting it up and installing it...and i  downloaded sample .conf files to put in the .conkyrc folder in my /home/james folder but when i go to start it i get an error msg ...
I have the same version as you and conky works for me.

Maybe you shouldn't "*put in the .conkyrc folder in my /home/james folder*". I have a file (not folder) called .conkyrc in /home/vasa1.

---

### Post by vasa1 on 2014-03-05
> **NM5TF said:**
> you seem to have an older version....

my version looks like this.... 

```

tommy3@tommy3-Inspiron-531s:~$ conky -v
Conky 1.9.0 compiled Wed Feb 19 18:44:57 UTC 2014 for Linux 3.2.0-37-generic (x86_64)

``` 


Could you tell us where you got this recent version from?

---

### Post by deadflowr on 2014-03-06
> **vasa1 said:**
> Could you tell us where you got this recent version from?

I think that's the build for trusty.

To the op, nothing helps move things along quicker when it comes to conky like posting the conkyrc.

If you do post Please Please Please use [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168").

---

### Post by vasa1 on 2014-03-06
> **deadflowr said:**
> I think that's the build for trusty.
...
Thanks for clearing that up :)

I just looked at [http://manpages.ubuntu.com/manpages/trusty/en/man1/conky.1.html](http://manpages.ubuntu.com/manpages/trusty/en/man1/conky.1.html)
and saw 
conky-all_1.9.0-4_i386

---

### Post by NM5TF on 2014-03-06
> **deadflowr said:**
> I think that's the build for trusty.

To the op, nothing helps move things along quicker when it comes to conky like posting the conkyrc.

If you do post Please Please Please use [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168").

+100

and yes, that is the build for 14.04 Trusty:)

and yes, providing your conkyrc file lets us see exactly what you are doing & where potential
problems may be...:)

to use the code tags in your reply, use the # symbol in the menu & copy/paste the conkyrc between the #'s

tommy

---

### Post by NyteRukh on 2014-03-06
ok thanks

---

### Post by NyteRukh on 2014-03-06
ok thankyou everyone for your help..it turns out that i had put the .conkyrc file in the wroong place....i placed it in /home/james instead of just /home

---

### Post by deadflowr on 2014-03-06
Seems nice that you've solved your issue.

For further future reference conky can execute to script anywhere you place it, if you use the --config option.

For example, let's say you have a conkyrc in your Documents folder.
simply run
```
conky --config ~/Documents/conkyrc
```
will load that conky file.

More conky info here
[http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

---

