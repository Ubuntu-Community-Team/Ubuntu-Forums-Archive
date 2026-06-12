---
title: "Remove FireFox3 Beta"
date: 2008-06-15
forum: General Help
---

### Post by Uchiha_madara on 2008-06-15
Fire Fox 3 Beta Cause Many Troubles

When I Open it , Ubuntu hardy well be slow and sometimes seems to be deadlocked 

i need to remove FireFox 3.5 Beta and install Fire Fox 2.14
instead or Opera browser
Some body Help meeeeeeeeeeeee:guitar:

---

### Post by trevelyan on 2008-06-15
use synaptic package manager to uninstall it. search for "firefox"

---

### Post by Nepherte on 2008-06-15
To remove firefox 3:
```
sudo apt-get purge firefox-3.0
```

To install firefox 2:
```
sudo apt-get install firefox-2
```

To install opera:
```
sudo apt-get install opera
```

---

### Post by dslehman on 2008-06-16
I don't want to use Firefox 3 as my primary browser until it's stable. However, I do want to keep it around so that I can play with it.

I've installed Firefox 2.x from Mozilla's pre-compiled binaries from their web site ([http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)).

```

tar xvfz firefox-2.0.0.14.tar.gz
# Start firefox 2.x
user@jude:~/bin$ ./firefox
/home/user/bin/firefox_bin/2.0.0.14/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
# Note: this failed b/c Hardy comes with libstdc++.so.6
# Install necessary libraries
user@jude:~/bin$ sudo aptitude install libxul-dev libstdc++5
user@jude:~/bin$ sudo aptitude ldconfig
# Start firefox 2.x
user@jude:~/bin$ ./firefox

```

I haven't tried this, but this guy appears to have written good docs on how to remove the hardy package firefox 3 and install the hardy package firefox 2.
[http://notatplay.blogspot.com/2008/05/ubuntu-804-downgrading-firefox-and.html](http://notatplay.blogspot.com/2008/05/ubuntu-804-downgrading-firefox-and.html)

---

### Post by Uchiha_madara on 2008-06-17
Thanks a lot for all :lolflag:

---

