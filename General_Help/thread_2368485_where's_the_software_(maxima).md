---
title: "where's the software (maxima)"
date: 2017-08-11
forum: General Help
---

### Post by William_Labbett on 2017-08-11
[ATTACH=CONFIG]276359[/ATTACH]


Hi,

 I'm running ubuntu 17.04 and I've used apt-get to install the package maxima.

I doesn't show up on the search box of the dash and won't run from the command line.

I've had this issue before with 12.04 and am wondering what I need to do to be able to use the program.

please help,

Will

---

### Post by oldos2er on 2017-08-11
I'm not familiar with maxima, but run ```
dpkg -L maxima
``` and look for an executable in /usr/bin, that'll likely be the program you'd need to run in terminal.

---

