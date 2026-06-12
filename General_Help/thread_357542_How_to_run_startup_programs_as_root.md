---
title: "How to run startup programs as root"
date: 2007-02-09
forum: General Help
---

### Post by holdie on 2007-02-09
After a little wireless fiasco a while back, I'm in the position of having to run "dhclient" every time my computer boots in order to connect to the internet.  I'd like to have my computer do this automatically, however when I write it into sessions it won't work because it is a root command...

is there any way to get my computer to run this each time I boot up, or is there some other way to fix the problem?

---

### Post by taurus on 2007-02-09
You can add your username and that command, the complete path, to /etc/sudoers so it won't ask for your password when you run it.

```
sudo visudo
```
Now, you are using vi text editor so need to be careful.  You can move around with the arrow keys and when you want to insert text, you need to hit letter i for insert.  And when you are done with typing, hit the  Esc key.  And if you want to exit, do :wq! after hitting the Esc key.

```
**username** ALL= NOPASSWD: **/complete/path/to/dhclient**
```
(where username is your actual username.)

---

### Post by kerry_s on 2007-02-09
sudo gedit /etc/rc.local
put
dhclient &

in between,looks like->

# By default this script does nothing.
dhclient &

exit 0

---

