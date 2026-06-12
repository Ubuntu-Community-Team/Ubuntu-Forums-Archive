---
title: "[SOLVED] xfonts-ay ( and other fonts ) not recognized by xorg - SOLUTION"
date: 2007-06-23
forum: General Help
---

### Post by centyx on 2007-06-23
Distro: Feisty 7.04

Problem:
The "shine" font is still not available after installing the package xfonts-ay via the command
'apt-get install xfonts-ay'

Being obstinate, I refrained from hitting the Submit button on this post until I found the solution. I first followed the instructions found in the Wiki for troubleshooting such font issues, which did not work. I eventually remembered from a previous experience that I needed to do the following:

[LIST=2]
[*]Run mkfontdir in the fonts directory ( this step had already been done by dpkg postint )
```
cd /usr/share/fonts/X11/misc && /usr/bin/mkfontdir
```

[*]Create the file /etc/X11/fonts/misc/xfonts-ay.alias containing the following ( actual font names found in /usr/share/fonts/X11/misc/fonts.dir ):
```
shine.all -ay-shine.all-medium-r-normal--10-100-75-75-p-90-fontspecific-0
shine.no -ay-shine.no-medium-r-normal--10-100-75-75-p-90-fontspecific-0
shine -ay-shine-medium-r-normal--10-100-75-75-p-90-ibm437-0
shine.se -ay-shine.se-medium-r-normal--10-100-75-75-p-90-fontspecific-0
```

[*]Run the following command:
```
Update-fonts-alias misc
```

[*]Restart Xorg 

Log out and log back in.

[/LIST]

With success I have repeated these steps for fonts that I have added by hand and for packages like xfonts-artwiz. I hope someone finds this information useful.

---

### Post by centyx on 2007-09-18
Also, I found that in order to make certain fonts available to all applications, such as the artwiz fonts, I had to run sudo dpkg-reconfigure fontconfig-config and answer "Yes" to the question "Enable bitmapped fonts by default?"

---

