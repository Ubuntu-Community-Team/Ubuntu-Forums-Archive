---
title: "complex script (or maybe not so complex)"
date: 2006-10-02
forum: General Help
---

### Post by odysseus.lost on 2006-10-02
Hi, have a look on the script below and then to what I would ideally like to happen... which apparently it does not..

```

#!/bin/bash
gnome-terminal &
cd /home/foo/lala
./papa 1 &
gnome-terminal --tab &
cd /home/foo/lala
./mama 1 &
gnome-terminal &
cd /home/foo/lala
./papa 2 &
gnome-terminal --tab &
cd /home/foo/lala
./mama 2 &

```

What idealy I would like to happen is:
1. Run a new gnome-terminal
2. cd to a certain dir
3. Run in foreground a program
4. Run a new gnome-terminal in tab (ie on the same window)
5. cd to a certain dir
6. Run in a foreground a program
7. Run a gnome-terminal into a new window
8. cd to a certain directory
9. Run in a foreground a program
10....

Well the script does not really do what I want.... The programs are launched on the first terminal, in background (yes that is the & symbol, but then again how can I make the script continue without halting?) and the two new terminal windows are open seperately doing nothing...

Any help?

Thanks.

---

### Post by Ramses de Norre on 2006-10-02
This is the closest I can get to it, I can't get it to work to do two commands inside that gnome-terminal and the "--tab" option doesn't exist.```
#!/bin/bash
gnome-terminal -x /home/foo/lala/papa\ 1
gnome-terminal -x /home/foo/lala/mama\ 1
gnome-terminal -x /home/foo/lala/papa\ 2
gnome-terminal -x /home/foo/lala/mama\ 2
exit 0
```

---

