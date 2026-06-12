---
title: "Nvidia accelerated graphics problems"
date: 2007-10-10
forum: General Help
---

### Post by acl123 on 2007-10-10
Hi,

I installed my GEForce 7300 GS card using Envy and it all seemed to go OK at first. I have a ViewSonic VG2021m and the recommended resolution is 1400x1050/60hz.

Now I am trying to enable Nvidia accelerated graphics so I can run Google Earth.

After I enable it though, my resolution is all messed up and I get fuzzy lines running down my monitor. I've spent weeks trying to get rid of them but I can't.

With accelerated graphics disabled the resolution is better but I can't use Google Earth. Obviously I could use it on Windows.

I believe I've setup xorg.conf correctly in terms of horizsync, vertrefresh, modeline etc.

What can I do?

---

### Post by dabl on 2007-10-10
> **acl123 said:**
> 

What can I do?

Assuming the appropriate Nvidia proprietary driver really is installed,

1. Open a console window, and enter ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

When it is done re-writing xorg.conf (2 seconds later) you can restart the xserver with Ctrl-Alt-Backspace, and log back in.

2. Verify that glx is working correctly by entering in the console window ```
glxgears
```

You should see a graphic and in the console window a frames-per-second display rate should be calculated, until you stop it with Ctrl-C or Esc.

3. Open a console window and enter ```
sudo nvidia-settings
```

Click the "X Server Configuration" tab.  Click "detect displays".  Set the resolution as you would like to have it for default.  Set refresh to "Auto". Click the "Save to X Configuration File", then "X" "merge", then click "Save". Confirm that it is defaulting to your chosen settings by restarting the X server with Ctrl-Alt-Backspace.

If these all worked as intended, you should be able to install Google Earth and have it work as well as it will ever work on your system.  :)

---

### Post by acl123 on 2007-10-11
Hi thanks, I hadn't tried those steps before.

However my monitor resolution is still much worse (fuzzy lines) once accelerated graphics is enabled.

---

### Post by Kevin_Jim on 2007-10-29
I have the exact same monitor, but when I install the 3rd party drivers from nvidia, whenever that is... I get a message that says " Out of Range" and I get pissed of, I've tried everything I knew,  I search at "Screen and Graphics" for my monitor, but I didn't find it. Can anyone help me ? 

( sorry for my terrible English )

---

### Post by acl123 on 2007-10-29
Hi,
I don't know if you've tried it, but the best way to get graphics to work is using Envy : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Everything basically works, although the resolution is still not great (although this could be my monitor).

---

