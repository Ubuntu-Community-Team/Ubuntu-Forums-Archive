---
title: "I cant install MICROSIM!!!"
date: 2006-12-29
forum: General Help
---

### Post by sociallyteamed on 2006-12-29
PLEASE help me istall microsim [http://http://sourceforge.net/project/showfiles.php?group_id=144264]("http://http://sourceforge.net/project/showfiles.php?group_id=144264")
I tried installing this program but i get the following:what should i use, i tried using alien but that didnt work out to well thanks.
t0k3r@t0k3r-laptop:~/Desktop$ cd version-1.0
t0k3r@t0k3r-laptop:~/Desktop/version-1.0$ ./install
Make microsim ...
make: *** No rule to make target `/usr/lib/qt-3.3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.
Done
Change ownership ...
chown: cannot access `microsim': No such file or directory
Done
Change permissions ...
chmod: cannot access `microsim': No such file or directory
Done
t0k3r@t0k3r-laptop:~/Desktop/version-1.0$ su
Password:
root@t0k3r-laptop:/home/t0k3r/Desktop/version-1.0# ./install
Make microsim ...
make: *** No rule to make target `/usr/lib/qt-3.3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.
Done
Change ownership ...
chown: cannot access `microsim': No such file or directory
Done
Change permissions ...
chmod: cannot access `microsim': No such file or directory
Done
root@t0k3r-laptop:/home/t0k3r/Desktop/version-1.0# microsim
bash: microsim: command not found
root@t0k3r-laptop:/home/t0k3r/Desktop/version-1.0# microSim
bash: microSim: command not found
root@t0k3r-laptop:/home/t0k3r/Desktop/version-1.0# make install
make: *** No rule to make target `/usr/lib/qt-3.3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.
root@t0k3r-laptop:/home/t0k3r/Desktop/version-1.0# make ./install
make: *** No rule to make target `/usr/lib/qt-3.3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.
root@t0k3r-laptop:/home/t0k3r/Desktop/version-1.0# Make install
bash: Make: command not found
root@t0k3r-laptop:/home/t0k3r/Desktop/version-1.0#

---

