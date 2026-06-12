---
title: "Starting compiz, doesn't finish."
date: 2008-05-23
forum: General Help
---

### Post by Kayos02 on 2008-05-23
I am trying to start up Compiz Desktop Effects with this command:

```
compiz --replace
```

The output starts out fine 

```
kayos@kayos-b0x:~$ compiz --replace
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Xgl with nVidia drivers...
```

But ends there. What exactly is the problem?

I have an Nvidia FX 5200

The output of 'dpkg -l | grep compiz' is

```
ii  compiz-core                                1:0.7.4-0ubuntu6                            OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                              Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                              Collection of plugins from OpenCompositing f
rc  compiz-gnome                               1:0.7.4-0ubuntu6                            OpenGL window and compositing manager - GNOM
ii  compiz-kde                                 1:0.7.4-0ubuntu6                            OpenGL window and compositing manager - KDE 
ii  compiz-plugins                             1:0.7.4-0ubuntu6                            OpenGL window and compositing manager - plug
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                              Settings library for plugins - OpenCompositi
ii  compizconfig-backend-kconfig               0.7.4-0ubuntu1                              KConfig Settings library for plugins - OpenC
rc  compizconfig-settings-manager              0.7.4-0ubuntu2                              Compiz configuration settings manager
rc  desktop-effects-kde                        0.4                                         compiz setup tool for KDE
ii  libcompizconfig0                           0.7.4-0ubuntu1                              Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.7.4-0ubuntu1                              Compiz configuration system bindings

```

---

### Post by Forlong on 2008-05-23
You do not need Xgl with an Nvidia card, remove it:
```
sudo apt-get remove xserver-xgl
```
Afterwards, restart X and try again.

---

### Post by Kayos02 on 2008-05-23
After I did that and then tried compiz --replace again, I got this:

```

kayos@kayos-b0x:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present
```

Then it just stopped, not returning to prompt, no window bars.

---

### Post by Forlong on 2008-05-23
Open another terminal and run
```
kde-window-decorator
```

---

### Post by Kayos02 on 2008-05-23
I did that, and it did nothing. No errors or anything.

```
kayos@kayos-b0x:~$ kde-window-decorator


```

---

### Post by Forlong on 2008-05-23
That's weird. When the window boarders are missing, are you able to move the windows via [Alt]+[Left Mousebutton]?

---

### Post by Kayos02 on 2008-05-23
nope

---

### Post by Forlong on 2008-05-23
OK, that means Compiz is most probably not running at all.

What output gives
```
compiz.real --replace ccp
```

---

### Post by Kayos02 on 2008-05-23
It gives no output. By the way I think it is running, for these reasons:

The switch desktop boxes got bigger, my application launcher menu got bigger.

These changes were made with the second attempt to start compiz after the removal of xgl.

---

### Post by Forlong on 2008-05-23
OK, let's try this:

First run
```
compiz.real --replace ccp & kde-window-decorator &
```
And then
```
ps -e | grep "compiz\|kde-window"
```

---

### Post by Kayos02 on 2008-05-23
```
kayos@kayos-b0x:~$ compiz.real --replace ccp & kde-window-decorator &
[1] 6406
[2] 6407
kayos@kayos-b0x:~$ kde-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the--replace option to replace the current decoration manager.
```

And then
```
kayos@kayos-b0x:~$ ps -e | grep "compiz\|kde-window"
 6149 ?        00:00:00 kde-window-deco
 6406 pts/0    00:00:01 compiz.real
kayos@kayos-b0x:~$
```

---

### Post by Kayos02 on 2008-05-23
Sorry, accidental double post.

---

### Post by Forlong on 2008-05-23
According to that output, both Compiz and kde-window-decorator (responsible for window boarders) are running...

---

### Post by Kayos02 on 2008-05-23
But shouldn't compiz --replace replace kwin ?

---

### Post by Forlong on 2008-05-23
Kwin is _not_ kde-window-decorator.

The only thing I can think of is this:
Install ccsm (again): ```
sudo apt-get install compizconfig-settings-manager
```
And make sure the **Window Decoration** plugin is enabled.

---

### Post by Kayos02 on 2008-05-23
wewt, Compiz is working now, but now I can't move my windows?

EDIT: Got it.

---

### Post by Zorael on 2008-05-23
Noteworthy is that compiz never "finishes" since it's technically not set up to run in the background.

The ampersand (&) at the end of the command makes it a child process of the console window, which will leave you with terminal control. Closing it with the X button terminates compiz, but if you enter **exit** instead it'll keep running.

---

### Post by Kayos02 on 2008-05-23
> **Zorael said:**
> Noteworthy is that compiz never "finishes" since it's technically not set up to run in the background.

The ampersand (&) at the end of the command makes it a child process of the console window, which will leave you with terminal control. Closing it with the X button terminates compiz, but if you enter **exit** instead it'll keep running.

Good to know, thanks.

---

