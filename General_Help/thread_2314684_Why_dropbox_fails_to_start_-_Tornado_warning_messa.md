---
title: "Why dropbox fails to start - Tornado warning message"
date: 2016-02-23
forum: General Help
---

### Post by arie6 on 2016-02-23
I'm using Dropbox on Ubuntu 14.04.
Few minutes after I start Dropbox, I get these warning message and Dropbox crushes.

WARNING:tornado.access:404 HEAD /blocks/86881494/fdg9aKCV-1U2Knp7jOxX3YrNfp_VjSnt1tFXd3nBlfo (10.0.0.154) 192657.15ms
WARNING:tornado.access:404 HEAD /blocks/86881494/Qe_ijDSh5SND6ta7UcXLcIkQPpNSi_RWdy2OE-KVfYg (10.0.0.154) 198219.98ms
WARNING:tornado.access:404 HEAD /blocks/86881494/fC6DVdtSoBoK9GwEWNvaOw2WjXGUcDGxX1G6Aq3Znag (10.0.0.154) 172373.14ms
WARNING:tornado.access:404 HEAD /blocks/86881494/nifdTkVXGWrjN8FkwgBOSyIsaAo9xCbEVQ-1rfheB0g (10.0.0.154) 187801.91ms
WARNING:tornado.access:404 HEAD /blocks/86881494/kHjt4zDaqB6XX9qZlucuT-ZITMUBvVKmYLpUhUd5fd0 (10.0.0.154) 163042.36ms
WARNING:tornado.access:404 HEAD /blocks/86881494/0jBGhY4F4AyW_PsgcnkcIWzjnTUnG7rA_M5YyBolQXw (10.0.0.154) 157879.59ms

What is the meaning of these warnings?
What should I do in order to fix it?

Thanks.

---

### Post by drpjkurian on 2016-02-23
Hi
Check this [website]("http://stackoverflow.com/questions/27629797/python-tornado-render-static-directory"). it might give you some clue

---

### Post by arie6 on 2016-02-24
Thanks, but it didn't help much.

I realized that starting Dropbox triggers these warnings, but I think it's not related to it at all.
Where can I find this tornado process, I've searched for it and found nothing.
I didn't write/start any python script that cause this, what is the source of these warnings?

this is the problematic part I get from ps -aef|grep user:

user      30340      1  0 11:35 ?        00:00:00 dbus-launch --autolaunch 487c57e6bc8d0829f77cb9fe5574b5aa --binary-syntax --close-stderr
user      30341      1  0 11:35 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
user      30359      1  0 11:35 ?        00:00:00 /usr/lib/x86_64-linux-gnu/notify-osd
user      30405      1  0 11:35 ?        00:00:00 /usr/lib/gvfs/gvfsd
user      30409      1  0 11:35 ?        00:00:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1003/gvfs -f -o big_writes

---

### Post by Bucky Ball on 2016-02-24
*Thread moved to* ***General Help***.
[B][I]
Ubuntu, Linux and OS[/I][/B] Chat is not a support forum. :)

---

