---
title: "Window Tile Snapping"
date: 2014-10-23
forum: General Help
---

### Post by 3246251196 on 2014-10-23
I do not have the *tile* options in my Window Manager Settings menus.

I would like to use SUPER+L/R to do Windows type things where the window is halfed and tiled to the left/right.

Why I have no *tile* options in Window Manager.

Thanks.

[I]xfwm4 --version
    This is xfwm4 version 4.8.3 (revision 360ccf2) for Xfce 4.8
    Released under the terms of the GNU General Public License.
    Compiled against GTK+-2.24.10, using GTK+-2.24.10.

    Build configuration and supported features:
    - Startup notification support:                 Yes
    - XSync support:                                Yes
    - Render support:                               Yes
    - Xrandr support:                               Yes
    - Embedded compositor:                          Yes
    - KDE systray proxy (deprecated):               No
[/I]

---

### Post by vasa1 on 2014-10-23
If you update to the latest, you'll get snapping. In older versions, I don't remember which, you needed to install a ppa. Now (4.11), snapping is there by default.

Edit: [http://askubuntu.com/questions/103456/automatically-size-windows-using-xfce-like-in-gnome](http://askubuntu.com/questions/103456/automatically-size-windows-using-xfce-like-in-gnome)

Oops ... just noted that you want to use the keyboard for snapping. I don't know whether that is provided by xfwm4 or not.

---

### Post by Dennis N on 2014-10-24
Xubuntu 14.10 allows window snapping from the keyboard. These actions are left undefined by default. As a test, I defined **Alt+Rt-Arrow** to snap to the right edge and it works.

---

### Post by Dennis N on 2014-11-06
> I do not have the *tile* options in my Window Manager Settings menus.
You probably need a newer version of xfwm4 than the 4.8.3 version you have. Xubuntu 14.04 comes with version 4.11.1
  
Xubuntu 14.04 (and of course 14.10) can tile windows from the keyboard. How to this up:

Go tho Settings > Window Manager > Keyboard Tab

Scroll down in the menu at the left to the four selections beginning "Tile window to ..."

None of these are defined - to define an action, select an item and double click in the 'shortcut' column. A small dialog will let you press the keys you want to produce that action and they will be set for you.

---

### Post by CaptainMark on 2014-11-06
Without wanting to hijack a thread can windows be snapped to corners? I use cinnamon which support keyboard window snapping but cant do instant snap to corners.

---

### Post by vasa1 on 2014-11-06
> **CaptainMark said:**
> Without wanting to hijack a thread can windows be snapped to corners? I use cinnamon which support keyboard window snapping but cant do instant snap to corners.I think that depends on the window manager. Openbox can do so. There's a text file in *~/.config/openbox* called *rc.xml* or *lubuntu-rc.xml* or whatever a distro decides to call it. I have this code in the <keyboard></keyboard> section:```
    <keybind key="W-w">        # Center on screen
      <action name="MoveResizeTo"><x>center</x><y>center</y></action>
    </keybind>

    <keybind key="W-7">        # Top left corner
      <action name="MoveResizeTo"><x>0</x><y>0</y></action>
    </keybind>

    <keybind key="W-8">        # Top right corner
      <action name="MoveResizeTo"><x>-0</x><y>0</y></action>
    </keybind>

    <keybind key="W-9">        # Bottom right corner
      <action name="MoveResizeTo"><x>-0</x><y>-0</y></action>
    </keybind>

    <keybind key="W-0">        # Bottom left corner
      <action name="MoveResizeTo"><x>0</x><y>-0</y></action>
    </keybind>

```that addresses your issue. There are more "actions" listed [here]("http://openbox.org/wiki/Help:Actions").

I don't know what xfwm4 provides in this regard.

---

