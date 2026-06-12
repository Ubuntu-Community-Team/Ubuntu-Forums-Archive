---
title: "GDM not starting"
date: 2007-06-02
forum: General Help
---

### Post by sharperguy on 2007-06-02
Hey

Since this morning GDM has not been starting up and just giving a screen with a timer icon.

There doesn't seem to have been a cause for this like an update or anything

I'm sorry I can't give more info than that but I'm not at the computer at the moment.

Also for the same reason could you just post your ideas instead of asking a question which when answered would help you decide weather the idea is right or not (if that makes sence :P).

Thanks

---

### Post by kellemes on 2007-06-02
Well.. a lot of ideas come to mind, about a million. ;)

Listen, /var/log/Xorg.0.log probably has the answer.

---

### Post by sharperguy on 2007-06-02
are you sure it would be xorg logs because x works, just not GDM

---

### Post by jfinkels on 2007-06-02
> **sharperguy said:**
> are you sure it would be xorg logs because x works, just not GDM

Try disabling automatic startup of GDM by removing its executable:flag:
```

sudo chmod -x /etc/init.d/gdm

```

Then restart the computer, and you will boot into one of the 'tty' terminals. To start GDM, then just type this to make it executable again:
```

sudo chmod +x /etc/init.d/gdm

```

Then start it like this. Maybe you'll get some error output...
```

sudo /etc/init.d/gdm start

```

---

### Post by cosbear on 2007-06-02
Hey Buddy:

Check out this Post:  [http://ubuntuforums.org/showthread.php?t=460114](http://ubuntuforums.org/showthread.php?t=460114)

Hope it helps, just had the same problem myself.  cosbear

---

### Post by sharperguy on 2007-06-02
Hmm, well reinstalled now.

I'll check it out if it happens again.

---

