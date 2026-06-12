---
title: "Qtorrent3 Help"
date: 2005-10-25
forum: General Help
---

### Post by tzadokan on 2005-10-25
Anyone notice how qtorrent3 has no settings to change? Any help in changing the port it uses would be much appreciated. Thanks

---

### Post by hamil on 2006-04-19
Sorry...
Just another one bumping this thread...

I have searched for a config script, or anything similar... But not found it yet..
Any help is mostly appreciated!

Brgds
Lasse

---

### Post by hamil on 2006-04-19
Well... Actually, it seems that I have resolved this question myself...
I found a file called: defaultargs.py in the folder: /usr/lib/python2.4/site-packages/pyqtorrent3/BitTorrent/

I opened that file wit sudo gedit, and found some lines with some nice info:
```
    ('forwarded_port', 0,
        "world-visible port number if it's different from the one the client "
        "listens on locally"),
    ('minport', 6881, 'minimum port to listen on, counts up if unavailable'),
    ('maxport', 6991, 'maximum port to listen on'),

```
I edited this to my preference, and it seems like it is working fine with it... :)

---

### Post by scurl on 2008-04-12
a bit late for bumping this i guess, but i had to say thanks! this is almost exactly what i needed, but i found the defaultargs.py file (running gutsy)  in /usr/lib/python2.5/site-packages/pyqtorrent3/BitTorrent/ rather than python2.4. hope this helps someone somewhere.

---

