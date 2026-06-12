---
title: "Slow download speeds in Transmission"
date: 2008-04-07
forum: General Help
---

### Post by tubasoldier on 2008-04-07
I've heard some great things about Transmission. So I decided to give it a shot.
Transmission's GUI is simple and sleek. It sure looks nice. There is a lot to like about it.

However, I am getting unrealistically slow download speeds out of it. 5kb/s - 9 kb/s.
The same torrents in Ktorrent are blazing fast compared to that. 50kb/s - 250kb/s.

Has anyone else had issues with Transmission download speeds?

---

### Post by renzokuken on 2008-04-07
i have exactly the same issue.......transmission never gets above 10kb/s for me either. 

i have everything forwarded/setup correctly. i use ktorrent too and love it, ~300 kb/s at peak times. just a shame it isnt native to Gnome.

i also used to get good speeds with Bittornado, but its a bit featureless for me

---

### Post by Cadmus on 2008-04-07
I'm still on utorrent under Wine, but I realise that's not ideal. Deluge was looking promising, has it made much headway?

---

### Post by batistation on 2008-04-24
Sorry if you already checked this but try increasing the number of peers drastically.  For some reason the defaults are very low, I have mine set to 1000 overall and 250 per torrent and I am currently downloading ~350KB/s.  I don't know much but I have read that is not good to go overboard with the number of connections as it can have the same result as a very high u/l rate. Also check ports make sure that is not being blocked by ISP and or router.  

PS: Transmission is pretty cool after you get it working though.

---

### Post by TenPlus1 on 2008-04-24
Check out Deluge at [www.getdeb.net](www.getdeb.net), that achieves some amazing speeds on my 2mb line...

---

### Post by vishzilla on 2008-04-24
Transmission doesn't support DHT, that may be one reason. But if you get the right settings you will get outstanding speeds. I love transmission bcoz of its simplicity

---

### Post by noland on 2008-06-11
well dunno...  i put 1000 on peers, 200 per download, and its still slow like hell (9k), plus i put a limit on upload and it doesnt even follow it, it often goes double then the limit... gotta say i dont mind Utorrent, which i run in an emulated winXP in QEMU.. downloads full speed.  actually i will try the exact same 5 downloads in transmission and in utorrent at the same time to see what happens... 

Also to max out the number of peers in transmission, i had to go in the hidden files... maybe should that be an option in the GUI if that is really what the problem is?

All right, with 200 peers in utorrent, 50 per torrent, utorrent in QEMU is minimum 5 times faster...  so i will stick with that... i will try transmission once in a while, but up to now it just doesnt cut it...

---

