---
title: "Democracy player is not working any more"
date: 2006-08-02
forum: General Help
---

### Post by Marcos.Rufino on 2006-08-02
It was working fine until yesterday...

This is the message I get when running it from terminal:

> marcos@marcos-desktop:~$ democracyplayer
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 80, in ?
    startapp()
  File "/usr/bin/democracyplayer", line 37, in startapp
    import singleclick
  File "/usr/lib/python2.4/site-packages/democracy/singleclick.py", line 17, in ?
    import app
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 7, in ?
    import views
  File "/usr/lib/python2.4/site-packages/democracy/views.py", line 2, in ?
    import feed
  File "/usr/lib/python2.4/site-packages/democracy/feed.py", line 3, in ?
    from item import *
  File "/usr/lib/python2.4/site-packages/democracy/item.py", line 31, in ?
    _charset = locale.getpreferredencoding()
  File "/usr/lib/python2.4/locale.py", line 417, in getpreferredencoding
    setlocale(LC_CTYPE, "")
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting



Does anyone have any idea?

Thanks.

---

### Post by mister_p_1998 on 2006-08-05
Yeah, mine went down yesterday... the day after I upgraded it...
Ive got no replies on here or the democracy Forums. It runs, then quits after a few seconds.
Steve

---

### Post by Hairy_Palms on 2006-08-05
what is democracy player btw? 
[EDIT] nvm i just downloaded it and it worked fine for me, although it didnt work till i instealled the mozilla browser package

---

### Post by mister_p_1998 on 2006-08-06
This fixed it for me, working fine now...
Steve

code:
sudo apt-get install sun-java5-jre sun-java5-plugin

---

