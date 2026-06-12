---
title: "Fresh install Ubuntu 16.10 with rtorrent/Rutorrent - Unable to add RSS feed link."
date: 2016-10-18
forum: General Help
---

### Post by fastfwd2 on 2016-10-18
[FONT=arial][SIZE=3]Hey all hope you can help.

Slightly new to Ubuntu, using it here and there when I've needed to so i wouldn't call myself skilled.

I setup a ubuntu VM running off a QNAP and installed Rtorrent and Rutorrent. I've got all of that running perfectly fine, took me some time as i was having some issues with rtorrent downloading to a network cif share but i ended up sorting that out with fstab, i digress.

So now im having an issue when i add a RSS feed into rutorrent. i received this error: [SIZE=4]"[/SIZE][COLOR=#000000][SIZE=4][19.10.2016 07:57:22] Error loading feed. (https://aaaaaaaaa.com/torrents/rss?u=997352;tp=d4653e9738d8b029787fb996d6dfff1c;99;download)"[/SIZE]
[SIZE=4]
I thought first off it might be issue with the stock firewall or security in ubuntu with HTTPS so i ran "ufw 443/tcp" but still didnt work.

i've googled a bit, one person said they changed rutorrent versions to an old one and it fixed it. I dont exactly want to do that because i know its just a setting issue in rtorrent/rutorrent or ubuntu.

Any idea's of what it could be?[/SIZE][/COLOR][/SIZE][/FONT]

---

### Post by fastfwd2 on 2016-10-18
All sorted...

found that [COLOR=#263238][FONT=Roboto]/var/www/rutorrent/plugins/rss/cache needs read/write perms. 

Granted those, restarted rutorrent and apache services. worked.[/FONT][/COLOR]

---

