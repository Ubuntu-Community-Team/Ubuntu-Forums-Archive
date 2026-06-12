---
title: "&quot;System problem detected&quot; and other random errors in 13.04"
date: 2013-05-08
forum: General Help
---

### Post by typos1 on 2013-05-08
Since upgrading I get a "system problem detected" error when I boot. 

Booting takes a while and then takes a further min and a half AFTER I have entered my password to access the desktop and FURTHER delays before I can atually access files on it. 

I also get a "sorry Ubuntu 13.04 has internal error" message. this has happened since 12.04 actually, although if I click "ok" nothing actually happens. I always click "report" when shown in error messages.

Sometimes I cannot get it out of hibernate - it starts up but then the screen goes black with the cursor showing and it does not respond to anything, other times I get a strange collage of the desktop plus random bits of windows, like some graphical error when I come back to the pc and it had locked the desktop - I have to reboot.

can anyone help ? 

Thanks

---

### Post by SuperFreak on 2013-05-08
It was an upgrade not a clean install right? Upgrades can be problematic. Someone else may be able to help you fix your current system but consider backing up your data and doing a clean install

---

### Post by ibjsb4 on 2013-05-08
System problem detected usually means that apport needs to be disabled.

[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

[http://ubuntuforums.org/showthread.php?t=2127847&p=12567395&viewfull=1#post12567395](http://ubuntuforums.org/showthread.php?t=2127847&p=12567395&viewfull=1#post12567395)

[http://ubuntuforums.org/showthread.php?t=1838908&p=11218099&viewfull=1#post11218099](http://ubuntuforums.org/showthread.php?t=1838908&p=11218099&viewfull=1#post11218099)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=system+problem+detected&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=system+problem+detected&sa=Search&cof=FORID:9)

This will not solve all your problems, but should take care of the one.

---

### Post by typos1 on 2013-05-09
I ran 

gksudo geany /etc/default/apport



in a terminal, put pc in suspend/hibernate came back 4 hours later and there was a black screen full of white test (like a terminal). I held down power switched it back on again, it hung on a purple screen. Held down power again and it finally booted, taking even longer to go from the sign in screen to a usuable desktop, then got the "system problem dected error again" :-(

---

