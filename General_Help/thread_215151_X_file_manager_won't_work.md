---
title: "X file manager won't work"
date: 2006-07-13
forum: General Help
---

### Post by Tohtori on 2006-07-13
I just installed xfm using apt-get and it did not display any errors. There is xfm manual and it says xfm [options] for the syntax but the thing is that there is no such command. Do I need to do something before it works or is it supposed to work in a different way.

...this is secound time when this happenes to me

---

### Post by Ramses de Norre on 2006-07-13
What's the output of ```
sudo updatedb && locate xfm
```

---

### Post by Tohtori on 2006-07-13
after updatedb locate xfm gives me this [http://jensei.propelli.cop.fi/locate.txt]("http://jensei.propelli.cop.fi/locate.txt")

---

### Post by Ramses de Norre on 2006-07-13
The executable is /usr/X11R6/bin/xfm and /usr/X11R6/bin/ is included in the path for root (when executing after sudo -i) but not in the path of a regular user (normal executing or executing with sudo). So the easiest fix is ```
sudo ln -s /usr/X11R6/bin/xfm /usr/bin/xfm
```

---

### Post by Tohtori on 2006-07-13
That did the trick. thx (:

---

