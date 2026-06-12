---
title: "sudo problem"
date: 2008-01-21
forum: General Help
---

### Post by macuser2000 on 2008-01-21
Every time I use sudo in terminal for the second time since I boot up, I get a message like this

```
sudo: timestamp too far in the future: Jan 22 02:26:37 2008
```

This only happens in the gnome terminal, when I use xterm or a full-screen terminal it works fine.

Could someone help me?

---

### Post by y-lee on 2008-01-21
Try

```
sudo -v
```

This extends the sudo timeout for another 15 minutes (or whatever the timeout is set to in sudoers) but does not run a command.

Also you might want to see [how to solve "sudo:timestamp too far in the future" error]("http://my.opera.com/render/blog/show.dml/337121")

I've never had that problem so I can't vouch for either method.

---

### Post by bodhi.zazen on 2008-01-21
sudo -k

should work

---

### Post by p_quarles on 2008-01-21
I vaguely recall that happening to me once after I incorrectly configured my time/date settings.

If you run:
```
date
```
in a terminal, does it display the correct time?

---

### Post by macuser2000 on 2008-01-23
yes

---

