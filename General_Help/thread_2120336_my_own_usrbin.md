---
title: "my own /usr/bin ?"
date: 2013-02-26
forum: General Help
---

### Post by DonTommy on 2013-02-26
Hey
I have startet making small scripts, placing them in /usr/bin so that I can run them from any folder.

However, is it possible to add a new folder like that, so I can place my scripts where I want them, to keep them organized?

Lets say putting my scripts in /home/user/scripts/ instead, would that be possible?

Thanks

---

### Post by bantuvez on 2013-02-26
Put your scripts to /home/USERNAME/bin directory.

---

### Post by DonTommy on 2013-02-26
I dont want that, I want to choose my own folder, eg for placing it inside a dropbox folder so I that I have my scripts at all times on all my computers

---

### Post by cortman on 2013-02-26
~/bin is included in your $PATH, so scripts that are in there can be run just by calling the script name, as you're wanting.
If for some reason it hasn't been included in $PATH yet, you can by simply running

```
$PATH=PATH:\home\user_name\bin
```

---

### Post by bantuvez on 2013-02-26
Then edit your .profile file in your home directory and add the directory what you want to your PATH.  Just like it is done there with the $HOME/bin directory.

---

### Post by DonTommy on 2013-02-26
Thanks for the quick answers guys :)

---

