---
title: "Function Key Mapping"
date: 2007-05-06
forum: General Help
---

### Post by thomasaaron on 2007-05-06
I've found several posts on mapping function keys, but all of them assume a little too much knowledge on the part of the person posting the thread.

I've written a script that incrementally increases my laptop's LCD brightness,
and I've written a script that incrementally decreases the brightness.

I want to map one function key to run the first script and another to run the second script.

Can anybody help me out with some simple-to-follow instructions for doing that?

Best,
Tom

---

### Post by wtruong on 2007-05-06
you can xbindkeys

sudo apt-get install xbindkeys
sudo apt-get install xbindkeys-config

once you install start:
xbindkeys
xbindkeys-config

use your script for the action, i'm not sure what language is yours in but xbindkeys works with python, maybe others too but im not too sure.

after youre done installing and making it work, make sure you add xbindkeys to startup

---

### Post by thomasaaron on 2007-05-06
Thank you. That worked nicely.

Best,
Tom

---

### Post by panso on 2007-06-21
Hi,

Is there an app to capture a keypress?

To explain my thinkpad G40 has a couple of buttons that act as previous/next commands which I would like to map to rotate my beryl cube.

Thanks in advance.

---

### Post by sgtron on 2007-07-02
xbindkeys-config will capture a keypress

---

