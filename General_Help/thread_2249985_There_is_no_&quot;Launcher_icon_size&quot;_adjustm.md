---
title: "There is no &quot;Launcher icon size&quot; adjustment bar"
date: 2014-10-25
forum: General Help
---

### Post by ruwan2 on 2014-10-25
Hi,
I have two PC installed Ubuntu 12.04, the same version OS, 32 bit. One Ubuntu launcher icon size has been adjusted to small font long time ago. I want to get the same small icon/font on another Ubuntu PC (12.04, 32 bit OS). But it does not have the slide bar to make the adjustment. That is, it has no the line below "Theme". The following picture is the right one having the launcher icon size slide bar.




Can you tell me how to make the slide bar appear on my second PC?

Thanks,

---

### Post by deadflowr on 2014-10-25
That's because the second machine is most likely unable, at this point in time, to render the 3d graphics necessary to run full unity.
So instead it falls back to what was/is known as unity2d.

You can make the launcher icons smaller, or bigger, but it is not as straight forward.
Looky at this link for a simple guide
[http://www.dedoimedo.com/computers/ubuntu-unity-2d-resize-launcher.html](http://www.dedoimedo.com/computers/ubuntu-unity-2d-resize-launcher.html)

You can also verify if unity2d is running by running the following command in a termial
```
/usr/lib/nux/unity_support_test -p
```
If any of the responses are no then you could only be running in 2d.

---

### Post by mc4man on 2014-10-26
This would also probably tell - 
```
echo $DESKTOP_SESSION
```

---

### Post by jklex on 2014-11-29
Has same problem with lack of launcher icon adjustment after installing 12.04 LTS.  Logged out and restarted system.  On login screen, clicked the icon above loging box.  Offered to switch to 2D mode and selected that.  After login, still no launcher icon adjustment in Appearance settings.  Rebooted again and this time selected 3D mode.  Now it all works.  Ran the command in the post above and output shows full support for 3D.  I don't understand it at all.

---

### Post by grahammechanical on 2014-11-29
> [COLOR=#000000]I don't understand it at all.[/COLOR]

The ability to adjust the size of the launcher icons comes with the ability of the graphic adapter to do hardware accelerated 3D rendering for then the graphic adapter can run Ubuntu Unity 3D.

If we have a graphic adapter that can run Unity 3D it will also run Unity 2D but when we are in a Unity 2D session we do not get the option to adjust the size of the launcher icons. We only get that option when running the Ubuntu (Unity 3D) session.

If the graphic adapter cannot run Unity 3D then we only get Unity 2D and a very limited ability to make adjustments. This is because Unity 2D uses Metacity as the window manager/compositor. Whereas, Unity 3D uses Compiz as the window manager/compositor.

There you are. It is as clear as mud. :)

Regards.

---

