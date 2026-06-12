---
title: "cal -h no longer works in 17.04"
date: 2017-05-22
forum: General Help
---

### Post by csdgbas on 2017-05-22
Instead of removing highlighting, as expected, as previous versions, and as per the man page, it invokes help.

---

### Post by wildmanne39 on 2017-05-22
Since 16.10 will no longer be supported after July it would be prudent to install 16.04 it has long term support or 17.04 then if you still have the issue post back. Just my opinion.

---

### Post by csdgbas on 2017-05-22
> **wildmanne39 said:**
> Since 16.10 will no longer be supported after July it would be prudent to install 16.04 it has long term support or 17.04 then if you still have the issue post back. Just my opinion. Apologies, the version I have is 17.04.  Brain farted due to overheating. 

 FWIW, output of cal -h is at [http://paste.ubuntu.com/24626161/](http://paste.ubuntu.com/24626161/)  

The man page says ```
[snip]

The options are as follows:

     -h      Turns off highlighting of today.

[snip]

HISTORY
     A cal command appeared in Version 5 AT&T UNIX.  The ncal command appeared in FreeBSD 2.2.6.  The output of the cal command is supposed
     to be bit for bit compatible to the original Unix cal command, because its output is processed by other programs like CGI scripts,
     that should not be broken.
```

That snippet from the history is pretty important, IMO.

---

### Post by steeldriver on 2017-05-22
Maybe it is different implementation of cal? what do

```

readlink -f $(which cal)

dpkg -S $(which cal)

```

say?

---

### Post by csdgbas on 2017-05-22
> **steeldriver said:**
> Maybe it is different implementation of cal? what do

```
readlink -f $(which cal)
```
```
/usr/bin/ncal
```
> ```
dpkg -S $(which cal)
```
say?

```
 bsdmainutils: /usr/bin/cal
```

---

### Post by sisco311 on 2017-05-22
Does it work if you invoke ncal directly?
```
ncal -h
```

---

### Post by #&amp;thj^% on 2017-05-22
This works:
```
cal --color=never
```
"auto' sets it back to colorize again.
```
cal --color=auto
```

---

### Post by csdgbas on 2017-05-23
> **1fallen said:**
> This works: ```
cal --color=never
```  Thanks, but no.  It just gives ```
cal:  invalid option -- '-'
[snip "usage" output]

```

---

### Post by csdgbas on 2017-05-23
> **sisco311 said:**
> Does it work if you invoke ncal directly?

Amazingly, yes, it does!  Okay, that (kind of) fixes it for me, but... **how** did it get broken in the first place, and **why** is 'cal' not "bit for bit compatible to the original Unix cal command" (assuming, of course, that the original command didn't behaved the way that this one does)?

---

### Post by sisco311 on 2017-05-23
Ubuntu uses the BSD version of the cal command (ncal) which has more options than the original UNIX version. ncal is now backward compatible with the original cal command. If you invoke it as cal it will behave like the original UNIX cal command. If you need the extra options you will have to invoke it as ncal.

---

### Post by csdgbas on 2017-05-23
But prior to the "upgrade" to 17.04, I was using standard cal, with the -h option, and it worked as expected.

---

### Post by #&amp;thj^% on 2017-05-23
Well it seems I'm the last to know again..:D
Thanks for pointing that out [COLOR=#000000]sisco311
Cheers
[/COLOR]```
$ inxi -S && echo $DESKTOP_SESSION
System:    Host: me-750-417c Kernel: 4.10.0-22-lowlatency x86_64 (64 bit)
Desktop: Gnome 3.24.1 Distro: Ubuntu 17.04
gnome-wayland

```
I'm going to have to get used to this: :(

---

### Post by sisco311 on 2017-05-23
> **csdgbas said:**
> But prior to the "upgrade" to 17.04, I was using standard cal, with the -h option, and it worked as expected.

Just checked the man page (USAGE/SYNOPSIS part) of the earlier version of the BSD cal command and indeed the -h option was available even when the command was invoked as cal.

```

yakkety (1) ncal.1.gz
Provided by: bsdmainutils_9.0.6ubuntu3_amd64 &#65532;

NAME
     cal, ncal — displays a calendar and the date of Easter

SYNOPSIS
     cal [-3**h**jy] [-A number] [-B number] [[month] year]
     cal [-3**h**j] [-A number] [-B number] -m month [year]
     ncal [-3bhjJpwySM] [-A number] [-B number] [-s country_code] [[month]
         year]
     ncal [-3bhJeoSM] [-A number] [-B number] [year]
     ncal [-CN] [-H yyyy-mm-dd] [-d yyyy-mm]

```

But in the current version the option is no longer available: 

```

zesty (1) ncal.1.gz
Provided by: bsdmainutils_9.0.12ubuntu1_amd64 &#65532;

NAME
     cal, ncal — displays a calendar and the date of Easter

SYNOPSIS
     cal [-31jy] [-A number] [-B number] [-d yyyy-mm] [[month] year]
     cal [-31j] [-A number] [-B number] [-d yyyy-mm] -m month [year]
     ncal [-C] [-31jy] [-A number] [-B number] [-d yyyy-mm] [[month] year]
     ncal [-C] [-31j] [-A number] [-B number] [-d yyyy-mm] -m month [year]
     ncal [-31bhjJpwySM] [-A number] [-B number] [-H yyyy-mm-dd] [-d yyyy-mm]
         [-s country_code] [[month] year]
     ncal [-31bhJeoSM] [-A number] [-B number] [-d yyyy-mm] [year]

```

---

### Post by again? on 2017-05-24
> **csdgbas said:**
> But prior to the "upgrade" to 17.04, I was using standard cal, with the -h option, and it worked as expected.

FYI if you want oldstyle cal date formatting with the abilty to turn off highlighting you can use
the -b option with ncal.

---

### Post by csdgbas on 2017-05-24
> **sisco311 said:**
> Just checked the man page (USAGE/SYNOPSIS part) of the earlier version of the BSD cal command and indeed the -h option was available even when the command was invoked as cal.  [snip]  But in the current version the option is no longer available:   [snip]  Yes, this is exactly what concerns me.  I'm okay, I'm just one person, using cal in my conky config, and it was frustrating, but ultimately no big deal.  There are going to be people and organisations out there who rely on the promise in the man page.  The could be a lot of broken scripts out there.   > **guber2 said:**
> FYI if you want oldstyle cal date formatting with the abilty to turn off highlighting you can use the -b option with ncal. Thank you :)  I do prefer the "old style" layout, so your suggestion is perfect (for me) :)

---

