---
title: "[Solved] Change Alt + Tab Switcher Behavior in Lubuntu"
date: 2013-12-10
forum: General Help
---

### Post by Dennis N on 2013-12-10
I want to configure the ALT-TAB window switcher in Lubuntu to show the windows on all desktops instead of just the current desktop. I know I need to make some changes in:

**~/.config/openbox/lubuntu-rc.xml**

probably in the section **<keybind key="A-Tab">** and also the section **<keybind key="A-S-Tab">**

but I don't know the needed changes and correct syntax. How should I change these sections? Thank you for helping.

---

### Post by Dennis N on 2013-12-10
I figured it out myself.

Information for anyone wanting to do this:

open **~/.config/openbox/lubuntu-rc.xml** in text editor.

1) find section <keybind key="A-Tab"> 
Edit to look like this (added line in [COLOR="#FF0000"]red[/COLOR]):
```
   <keybind key="A-Tab">
      <action name="NextWindow">
        [COLOR="#FF0000"]<allDesktops>yes</allDesktops>[/COLOR]
        <dialog>icons</dialog>
        <finalactions>
          <action name="Focus"/>
          <action name="Raise"/>
          <action name="Unshade"/>
        </finalactions>
      </action>
    </keybind>
```

2) find section <keybind key="A-S-Tab">
Edit to look like this  (added line in [COLOR="#FF0000"]red[/COLOR]):
```
    <keybind key="A-S-Tab">
      <action name="PreviousWindow">
        [COLOR="#FF0000"]<allDesktops>yes</allDesktops>[/COLOR] 
        <finalactions>
          <action name="Focus"/>
          <action name="Raise"/>
          <action name="Unshade"/>
        </finalactions>
      </action>
    </keybind>

```
Save, log out, log in. Alt+Tab will now cycle through all windows on all desktops. Shift+Alt+Tab will cycle in reverse.

---

