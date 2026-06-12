---
title: "Changing number of workspaces in 15.04"
date: 2015-05-08
forum: General Help
---

### Post by anthony60 on 2015-05-08
How does one change the number of workspaces in Ubuntu 15.04 (vivid vervet)? Enabling workspaces in the UI defaults to 4, but there doesn't seem to be a way to change that number (I'm happy with a command line approach if no UI options)

Thanks!

---

### Post by khelben1979 on 2015-05-08
It looks like you need to use something which is called Unity Tweak Tool. Read more about it here: [http://askubuntu.com/questions/34572/how-can-i-reduce-or-increase-the-number-of-workspaces-in-unity](http://askubuntu.com/questions/34572/how-can-i-reduce-or-increase-the-number-of-workspaces-in-unity).

---

### Post by mc4man on 2015-05-08
As additional - from cli pretty easy, X is replaced with number desired
```
dconf write  /org/compiz/profiles/unity/plugins/core/hsize X
dconf write  /org/compiz/profiles/unity/plugins/core/vsize X
```

---

### Post by anthony60 on 2015-05-11
Thanks a lot! I will try these and post back for the results.

---

### Post by Doug S on 2015-05-12
This is just slightly different than mc4man mentioned: [https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces.html](https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces.html)

---

### Post by jduhachek on 2015-08-04
Ok, here is a work around to the bug that worked for me.  Go to the Workspace screen.  Click on the number of workspaces field. Use the up and down arrows to add or lower the number of workspaces you desire.  Then click ok.  It seems the field cannot be directly edited but the value can be modified.  Good luck and happy computing.

---

