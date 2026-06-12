---
title: "Prevent newly opened apps to steal the focus"
date: 2014-08-15
forum: General Help
---

### Post by luvshines on 2014-08-15
Hi

I have been using Ubuntu since a while now. But I am always pestered with this issue wherein if I open a new application, the focus shifts to that app
I am using Ubuntu 14.04 now with Unity and NOT using multiple desktops/workspaces.

Is there any way to prevent it ?
I just want the new apps to open in the background and continue with all the initializations etc. I will switch to them only when I want to

---

### Post by TheFu on 2014-08-15
I don't use unity, but with openbox, there is a setting to control exactly this. [http://openbox.org/wiki/Configuration](http://openbox.org/wiki/Configuration)

---

### Post by JKyleOKC on 2014-08-15
The file manager in Xubuntu, Thunar, also has this capability, with a single checkbox to control it.

---

### Post by vasa1 on 2014-08-15
> **TheFu said:**
> I don't use unity, but with openbox, there is a setting to control exactly this. [http://openbox.org/wiki/Configuration](http://openbox.org/wiki/Configuration)

Just to expand on that, rc.xml or its equivalent has this near the top of the file:```
  <focus>
    <focusNew>yes</focusNew>
    <!-- always try to focus new windows when they appear. other rules do
       apply -->
    <followMouse>no</followMouse>
    <!-- move focus to a window when you move the mouse into it -->
    <focusLast>yes</focusLast>
    <!-- focus the last used window when changing desktops, instead of the one
       under the mouse pointer. when followMouse is enabled -->
    <underMouse>no</underMouse>
    <!-- move focus under the mouse, even when the mouse is not moving -->
    <focusDelay>200</focusDelay>
    <!-- when followMouse is enabled, the mouse must be inside the window for
       this many milliseconds (1000 = 1 sec) before moving focus to it -->
    <raiseOnFocus>no</raiseOnFocus>
    <!-- when followMouse is enabled, and a window is given focus by moving the
       mouse into it, also raise the window -->
  </focus>

```
You can also set application-specific focus rules in the last section of rc.xml.

---

### Post by luvshines on 2015-03-20
Found an option in Compiz manager -> General options -> Focus and raise behaviour

Changed the 'Focus prevention level' from "Low" to "Normal" and it seems to have worked

---

