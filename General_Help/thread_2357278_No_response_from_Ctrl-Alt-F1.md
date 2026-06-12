---
title: "No response from Ctrl-Alt-F1"
date: 2017-03-29
forum: General Help
---

### Post by bert2694u on 2017-03-29
I seem to have the same problem, upgrade from 16.10 to 17.04(Beta2). 

I cannot enter a command line (by pressing CTRL+ALT+F1) - that gives me no response.
I can boot with Grub into recovery mode and then select reboot and I get into Ubuntu GUI, just fine.

How do I fix this? I cannot seem to find anything.
_When I do :_
[B][I]apt-get update
dpkg --configure -a
apt-get dist-upgrade
apt-get -f install[/I][/B]
Nothing seriously happens.
I also did ***ls -al /etc/modules-load.d***, I see:
cups-filters.conf
modules.conf -> ../modules

Doing a ***cat /etc/modules-load.d/cups-filters.conf*** gives me:
lp
ppdev
parport_pc

Since I know that with 17.04 is trying to use IPP printing, I commented out these three lines, and rebooted.
***But is still does not change***. I cannot boot directly into Ubuntu from GRUB, I have to boot into recovery and then normal boot - frustrating.

Any ideas on how to fix this?

Thanks

---

### Post by Bashing-om on 2017-03-29
bert2694u; Hello;

Perhaps most likely your issue is not related to this thread.
Verify :
Boot to the login screen and here execute ctl+alt+F! to gain a console interface,
Login here with user name and password ( no response to the screen when password entered, Enter pass word blindly and hit the enter key) .
Now what shows:
```

sudo lshw -C display

``` where here is the supposition that you have a broken proprietary graphic's driver.
AND if so we move to your own thread :)


[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by oldos2er on 2017-03-31
Posts moved to their own thread. [**[COLOR=#000000]bert2694u[/COLOR]**]("https://ubuntuforums.org/member.php?u=2063086"), please create a new thread rather than posting in an old one where your question will be far less visible. Thanks.

---

