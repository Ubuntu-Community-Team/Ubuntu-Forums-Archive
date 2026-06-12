---
title: "swap increases"
date: 2020-09-20
forum: General Help
---

### Post by T6&amp;sfpER35% on 2020-09-20
why,the longer the uptime on my pc,the more swap gets?
if i reboot swap goes back to 0%. is that normal?
i thought swap only kicks in when you running out of ram.
(ps. swappines set to 10)
my uptime now is 3,5 days and swap is at 10% , ram 61%.

---

### Post by Impavidus on 2020-09-20
It's normal. Swap that only kicks in when there's really no ram available any more wouldn't be the fastest way to handle memory and swap.

Just after booting, there isn't much in ram, so there's no need to use swap. Caching a file that's used every hour is more useful than keeping a page of memory that's never used after process initialisation in ram, so if you run out of ram, it may sometimes be better to use swap than to drop cached files. And it may be a good idea to begin copying things to to swap when it's likely the system will run out of ram, so that you won't see a long delay when it indeed has run out of ram and has to drop things.

---

### Post by HermanAB on 2020-09-20
3.5 days?  Linux can run for years without a reboot, but after 3 or 4 years the PSU usually blows up.

---

### Post by T6&amp;sfpER35% on 2020-09-20
> [COLOR=#000000]It's normal.[/COLOR]

thanks you , i feel easier now 

> [COLOR=#000000]Linux can run for years without a reboot[/COLOR]

yea i know , but in this country my pc wont be on for longer than a week cause off loadshedding lol

thanks guys!

---

