---
title: "remapping a single key"
date: 2014-10-04
forum: General Help
---

### Post by amarumayo on 2014-10-04
Hi all,

My keyboard left parenthesis is broken and I would like to remap it to a different key on the numberpad that I never use. I have read various threads about xkb however, I cannot seem to make sense out of the process. Can anyone suggest a simple way to do this on ubuntu 14.04?

Thanks in advance.

---

### Post by bashiergui on 2014-10-05
This covers a few ways to remap keys, hopefully it will steer you in a direction you can manage: 

[http://ragle.sanukcode.net/articles/remapping-keyboard-in-ubuntu/](http://ragle.sanukcode.net/articles/remapping-keyboard-in-ubuntu/)

---

### Post by Christmas on 2014-10-05
As mentioned in the above tutorial, you can do it with **xev** and **xmodmap** (to install them, use **sudo apt-get install x11-utils x11-xserver-utils**. Then type xev to see the keycodes, and use xmodmap to assign a value to another key, for example:

```
xmodmap -e "keycode 134 = bracketleft"
```

The key with the code 134 (in my case that's the right Windows key or Super key in Ubuntu) will be assigned the left bracket value. This may differ for your keyboard, so test with xev.

---

