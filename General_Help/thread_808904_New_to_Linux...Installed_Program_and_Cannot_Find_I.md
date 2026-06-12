---
title: "New to Linux...Installed Program and Cannot Find It?"
date: 2008-05-26
forum: General Help
---

### Post by DeanZ on 2008-05-26
I've just installed compiz settings manager as well as NVclock and I do not have them in my Applications, places or systems.

I'm just wondering how do I find these programs?

---

### Post by sweeneytodd on 2008-05-27
not sure but maybe from the root goto /etc folder

---

### Post by madelaki on 2008-05-27
If you used this command: *sudo apt-get compizconfig-settings-manager emerald*, it should be at System > Preferences. Not sure about NVClock though.

---

### Post by DeanZ on 2008-05-27
another problem whenever u use sudo before a command it asks for a password and then it will not let me type any password in

---

### Post by sweeneytodd on 2008-05-27
its letting you type the password, u just can't see it,type ur password and hit enter

---

### Post by werries on 2008-05-27
compiz settings will be the entry of System > Preferences > Advanced Desktop Effects Settings.

---

### Post by sdennie on 2008-05-27
If you know the name of the package, you can also figure out what binaries it's likely to have installed by typing:

```

dpkg -L name_of_package | grep bin\/

```

For example:

```

$ dpkg -L nvclock | grep bin\/
/usr/bin/nvclock

```

---

