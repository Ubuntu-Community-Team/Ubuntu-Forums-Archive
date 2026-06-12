---
title: "How to stop X server and start it with -logverbose 6"
date: 2016-01-12
forum: General Help
---

### Post by bojan2 on 2016-01-12
What is proper way to stop X server and start it with -logverbose 6 so i can fill bug to nvidia. 
I tried with:

```
sudo service ligthdm stop
sudo startx -logverbose 6
```

but ended in login loop problem like this
[http://askubuntu.com/questions/407720/cannot-login-to-ubuntu-after-startx-command](http://askubuntu.com/questions/407720/cannot-login-to-ubuntu-after-startx-command)

While i managed to solve this problem, in order to avoid more problems i ask what is proper way to do this.

---

### Post by bojan2 on 2016-01-12
Bump

---

### Post by deadflowr on 2016-01-12
just use
```
startx --whatever-whatever
```
xsession should be run as your user and your user alone, (so drop the sudo.)

by running with sudo the ownership of the Xauthority became root's.

---

### Post by bojan2 on 2016-01-13
> **deadflowr said:**
> just use
```
startx --whatever-whatever
```
xsession should be run as your user and your user alone, (so drop the sudo.)

by running with sudo the ownership of the Xauthority became root's.

I ran these commands now in tty1:

```
sudo service lightdm stop
startx -- -logverbose 6
```

but i ended with black screen. I can switch to tty 2-6 without problems. 
If i try to switch to gui with Ctrl+Alt+F7 i only get blinking cursor.
Any idea what is problem now?

---

