---
title: "font tahoma not working"
date: 2007-04-26
forum: General Help
---

### Post by Bashed on 2007-04-26
Regarding the fonts in gnome article found here:
[http://howtoforge.org/sharp_fonts_gnome](http://howtoforge.org/sharp_fonts_gnome)

I'm getting nothing but squares (see attached)

chad@Secured:/usr/share/fonts/truetype/custom$ ls -lh
total 1.3M
-r-xr-x--- 1 root root 611K 2007-04-26 12:15 tahomabd.ttf
-r-xr-x--- 1 root root 661K 2007-04-26 12:15 tahoma.ttf

chad@Secured:/usr/share/fonts/truetype/custom$ sudo /usr/bin/defoma-font -v register-all /etc/defoma/hints/custom.hints
/usr/bin/defoma-font -v register-all /etc/defoma/hints/custom.hints
W: /usr/share/fonts/truetype/custom/tahomabd.ttf: already registered in category truetype.
W: /usr/share/fonts/truetype/custom/tahoma.ttf: already registered in category truetype.

chad@Secured:/usr/share/fonts/truetype/custom$ sudo dpkg-reconfigure fontconfig
Cleaning up font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
Regenerating fonts cache... done.


I did everything as shown and rebooted the system. Why is it not working for me?

---

### Post by dahamsta on 2007-04-27
The perms are wrong on the fonts if you copy them direct from a Windows partition, set them to 644 and rerun the last two steps. Might be an idea to update the hints file to the one [here]("http://www.warrenguy.com/docs/ubuntu-linux/configuring-fonts.html") too, I'd say the one in that HOWTO is out of date.

adam

---

