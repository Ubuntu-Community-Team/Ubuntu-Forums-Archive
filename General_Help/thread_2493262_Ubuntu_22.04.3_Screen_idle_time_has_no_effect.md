---
title: "Ubuntu 22.04.3 Screen idle time has no effect"
date: 2023-12-08
forum: General Help
---

### Post by cscj01 on 2023-12-08
I have Ubuntu 22.04.3 x64 Flashback with an Nvidia graphics card and a Viewsonic monitor.  Until the other day, the idle time would cause the screen to blank after the specified idle time.  Now it will never blank.  I have applied some updates recently, but I don't specificaly recall any that involved the Nvidia drivers.  Does anyone have any idea what might cause this?

---

### Post by MAFoElffen on 2023-12-08
No, I have not seen that.

I, curiously, have the opposite problem, where mine on 22.04.3, I cannot keep it from suspending from being idle, without using the Caffeine app.

What do these show?
```

gsettings get com.canonical.unity-greeter idle-timeout   # Default is 300
gsettings get org.gnome.desktop.session idle-delay       # Default is 300

```

---

### Post by cscj01 on 2023-12-08
> **MAFoElffen said:**
> No, I have not seen that.

I, curiously, have the opposite problem, where mine on 22.04.3, I cannot keep it from suspending from being idle, without using the Caffeine app.

What do these show?
```

gsettings get com.canonical.unity-greeter idle-timeout   # Default is 300
gsettings get org.gnome.desktop.session idle-delay       # Default is 300

```


```
gsettings get org.gnome.desktop.session idle-delay  uint32 1200

gsettings get com.canonical.unity-greeter idle-timeout
No such schema “com.canonical.unity-greeter”
```

---

### Post by MAFoElffen on 2023-12-08
Okay then. Yours, right now is set for 20 minutes (1200/60=20). Default is 5 minutes (300/60=5)

You could reset it back to 300 via
```

gsettings set org.gnome.desktop.session idle-delay 300

```
Or via the settings panel, under the power settings...

---

### Post by cscj01 on 2023-12-09
I have reset the idle time several time.  The only time it seems to work is when I have some unworkable short time such as 1 or 2 minutes.  I don't recall the the value at which it stopped, but it seems to be 5 minutes.  I actuall chose another driver with no real change in behavior.  I rebooted ant tested it at 1 and 2 minutes and it worked.  Then I moved it to 15 minutes, and it failed.  I'm at a loss.

---

### Post by MAFoElffen on 2023-12-09
Then turn in a bug reported against gnome-control-center...

After creating the bug report, link it here so people here can track it.

---

### Post by cscj01 on 2023-12-09
I finally got it to work.  I tried another Nvidia driver and it has worked since (last 24 hours).  So I would presume there is something with the Nvidia driver.  I'll see if I can post on their site.  Thanks for your help.

---

