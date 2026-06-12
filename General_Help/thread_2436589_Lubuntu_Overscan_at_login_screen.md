---
title: "Lubuntu Overscan at login screen"
date: 2020-02-09
forum: General Help
---

### Post by jimmyc888 on 2020-02-09
Hello,
  I'm running Lubuntu 16.04.3 and have an overscan problem at the login screen that I can't seem to solve. 

Running 
xrandr --output HDMI0 --set underscan on 
through a script after login takes care of the problem but nothing works before login. Is there any way to get xrandr to run before a user logs in?


Thanks for any help with this

---

### Post by guiverc on 2020-02-09
This will just be informational, and not help with your problem sorry.

Lubuntu 16.04 was released 2016-April (thus 16.04) with 3 years of support, reaching it's EOL on 2019-April, so is now EOL.  ( [https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/) , [https://lubuntu.me/lubuntu-16-04-4-has-been-released/](https://lubuntu.me/lubuntu-16-04-4-has-been-released/) [https://lubuntu.me/test-xenial-6/](https://lubuntu.me/test-xenial-6/) )

> [COLOR=#555555][FONT=Ubuntu]Lubuntu 16.04 will be supported until April 2019.[/FONT][/COLOR]

Yes software found in the 'main' repository for Ubuntu 16.04 is still supported by Canonical, however the result is a propotion of your system is now unsupported & security fixes are all on you to back-port & patch yourself.  Use `ubuntu-support-status` to view which packages are not supported for your actual install.

As such I'd suggest *release-upgrading* to a supported system such as Lubuntu 18.04 LTS as soon as possible.

If you need to remain on 16.04, Ubuntu 16.04 LTS desktop (with Unity 7), Kylin desktop, and no desktop (ie. Ubuntu 16.04 LTS server) are still supported.  

> [COLOR=#333333]Maintenance updates are provided for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, Ubuntu Base, and Ubuntu Kylin. All the remaining flavours are supported for 3 years.[/COLOR]

[http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

---

