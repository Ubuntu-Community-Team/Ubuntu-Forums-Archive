---
title: "Receiving Terminal Error Code"
date: 2008-02-26
forum: General Help
---

### Post by Metaphysical on 2008-02-26
Every time I run a program directly from the terminal I get this error message:

X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

the program still opens and runs properly, but this message still comes up every time. Anyone know what the problem could be?

---

### Post by PeterJS on 2008-02-26
Take a look at your Xorg config, if you've got extra input devices configured, like a touch screen or table you don't have, when a program launches it will try and read from those devices, but clearly they don't exist, which is problematic. If you do have extranous input devices you can comment them out, and the problem should go away after you restart X.

---

### Post by Metaphysical on 2008-02-27
thanks for the quick help. i commented out the tablet pc devices and it's still giving me the same error. i think i had edited a different xorg.conf file to try to get my usb mic or 5button mouse to work a while ago, but i cant find that file again. im pretty sure it was empty before i put anything in it

---

### Post by taurus on 2008-02-27
Don't forget to restart X server after you've edited /etc/X11/xorg.conf.  Otherwise, you are still running the old version.

<Ctrl><Alt>backspace

---

### Post by PeterJS on 2008-02-27
The xorg config file is located at /etc/X11/xorg.conf, so that's the file you're looking for. Also changes won't take effect until you restart X with ctrl+alt+backspace.

---

### Post by Metaphysical on 2008-02-27
ok, i did ctrl+alt+backspace and restarted, now all i get is a shell. how do i get the graphical part back?

---

### Post by PeterJS on 2008-02-27
That's bad... it should automatically restart. Well, go ahead and login, and run:
```

sudo /etc/init.d/gdm start

```
to manually start gdm.

---

### Post by Metaphysical on 2008-02-27
ok i did this and then it said:
Staring Kdm: kdm is already running

and nothing changed

---

### Post by PeterJS on 2008-02-27
???

Well, what happens if you stop and start it?
```

sudo /etc/init.d/kdm stop
sudo /etc/init.d/kde start

```

Barring that how about starting X manually with:
```

startkde

```

---

### Post by Metaphysical on 2008-02-27
> **PeterJS said:**
> ???

Well, what happens if you stop and start it?
```

sudo /etc/init.d/kdm stop
sudo /etc/init.d/kde start

```

Barring that how about starting X manually with:
```

startkde

```

none of these worked so i went ahead and reinstalled kubuntu. still getting the same error though and i'm scared to do ctr+alt+ backspace again :(

---

### Post by PeterJS on 2008-02-27
Did the startkde script at least give good error messages? X might not have started becuase of excessive pruning or a typo in it's config.

---

