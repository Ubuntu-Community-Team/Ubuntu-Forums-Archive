---
title: "apt-get woes"
date: 2007-03-30
forum: General Help
---

### Post by spedsta on 2007-03-30
I tried installing the ms fonts via apt-get. That gave an error and didn't install, something about nor being able to dowload the fonts. 

The problem is that everytime I now try install via apt-get the package i want to install does install but then the fonts tries to install again, but fails each time

help

---

### Post by Rams_god on 2007-03-30
Hi,
   You can try using the following command.
sudo apt-get install font* 

If it is not working you can use

sudo apt-get install font* --fix-missing

Before running these commands ensure that all the proxy settings are correct. If you are still facing an issue feel free to contact me.

Thanks,
 Rams.

---

### Post by spedsta on 2007-03-30
nope, unfortunately that doesn't help, I get a lotf failed installs with this message for each one:

Note, selecting xfonts-efont-unicode for regex 'font*'

I don't really want the fonts, just a nice to have , I actually want to get rid of it trying to install each time I install another package.

thanks for the help :)

---

