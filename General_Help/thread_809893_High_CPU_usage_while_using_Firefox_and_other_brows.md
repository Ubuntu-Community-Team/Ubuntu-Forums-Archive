---
title: "High CPU usage while using Firefox and other browsers"
date: 2008-05-27
forum: General Help
---

### Post by xdavidx on 2008-05-27
I was getting an high CPU usage when browsing with Firefox so i've installed Web Epiphany thinking it was getting better..but it get worst..it gets 92% of usage with it..while Firefox gets 82%..and when i close the it the CPU goes down to 4-13%

Anyone knows other better browser to surf withouth bugs? (i don't want to test every gnome browsers).

Thanks.

---

### Post by werries on 2008-05-27
it really depends on what you're doing with the browser. cause loading images/video does take a lot of processing power, its normal.
firefox is about as good as it gets.

---

### Post by jrusso2 on 2008-05-27
Usually flash causes high cpu usage with Firefox

---

### Post by xdavidx on 2008-05-27
> **werries said:**
> it really depends on what you're doing with the browser. cause loading images/video does take a lot of processing power, its normal.
firefox is about as good as it gets.

i've seen your post and the answer someone gave to you, but i don't agree with it, cause i used another browser and it was worse..and the only thing i did it was browsing trough a myspace page, waited for the downloading of everything on the page and even with the music stoped i got 82% of usage and with the other browser exactly on the same conditions and viewing trough the terminal with htop (cause the other way gives u more usage) it gets 90% - 100% 90% ou usage..so there's something wrong that is enabled with browsers..btw just for opening my browser at google.com it gets 63% not normal..

---

### Post by werries on 2008-05-27
well how good is your processor

---

### Post by xdavidx on 2008-05-27
Intel Celeron 2.80GHz

---

### Post by |{urse on 2008-05-27
had the same processor/same problem a few weeks ago, install Opera. That helped a lot.

---

### Post by xdavidx on 2008-05-27
i'll try it and then i reply my experience ;)

---

### Post by xdavidx on 2008-05-27
> **|{urse said:**
> had the same processor/same problem a few weeks ago, install Opera. That helped a lot.

Okay..it's really faster than firefox and the usage of CPU got really better than with the other 2, but i've a problem..when it gets to show flash..it appear a white screen in front of it and it says "click to enable it" and i click and don't see nothing of flash..

---

### Post by Anduu on 2008-05-28
not sure how to install flash for opera but trust me...once flash is enabled your CPU useage will be right back up there again.

---

### Post by madara on 2008-05-28
> **xdavidx said:**
> Okay..it's really faster than firefox and the usage of CPU got really better than with the other 2, but i've a problem..when it gets to show flash..it appear a white screen in front of it and it says "click to enable it" and i click and don't see nothing of flash..

To install Adobe Flash Player after you installed Opera in Ubuntu,

sudo aptitude install flashplugin-nonfree

After the install routine is done you need to add the path to plugins options in opera. Alternatively you could link To find where the new binaries are located do

dpkg -S flashplugin-nonfree

app-install-data: /usr/share/app-install/desktop/flashplugin-nonfree.desktop
flashplugin-nonfree: /usr/lib/flashplugin-nonfree
flashplugin-nonfree: /var/cache/flashplugin-nonfree
flashplugin-nonfree: /usr/share/lintian/overrides/flashplugin-nonfree
flashplugin-nonfree: /usr/share/doc/flashplugin-nonfree
flashplugin-nonfree: /usr/share/doc/flashplugin-nonfree/changelog.gz
flashplugin-nonfree: /usr/share/doc/flashplugin-nonfree/copyright

Alternatively you could link the lib’s binary to Opera’s plugin directory:

sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/opera/plugins/

you may need to restart opera in order for plugins to actually work.

In opera’s address field type opera:plugins to see what opera knows about flash

---

### Post by xdavidx on 2008-05-28
> **madara said:**
> To install Adobe Flash Player after you installed Opera in Ubuntu,

sudo aptitude install flashplugin-nonfree

After the install routine is done you need to add the path to plugins options in opera. Alternatively you could link To find where the new binaries are located do

dpkg -S flashplugin-nonfree

app-install-data: /usr/share/app-install/desktop/flashplugin-nonfree.desktop
flashplugin-nonfree: /usr/lib/flashplugin-nonfree
flashplugin-nonfree: /var/cache/flashplugin-nonfree
flashplugin-nonfree: /usr/share/lintian/overrides/flashplugin-nonfree
flashplugin-nonfree: /usr/share/doc/flashplugin-nonfree
flashplugin-nonfree: /usr/share/doc/flashplugin-nonfree/changelog.gz
flashplugin-nonfree: /usr/share/doc/flashplugin-nonfree/copyright

Alternatively you could link the lib&#8217;s binary to Opera&#8217;s plugin directory:

sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/opera/plugins/

you may need to restart opera in order for plugins to actually work.

In opera&#8217;s address field type opera:plugins to see what opera knows about flash

..thanks for trying to help me, but Opera have flash plugin installed..and i've tried to install again and again and the result is always the same..it seems it doesn't recognize the plugin :\

---

