---
title: "custom unity launcher from terminal"
date: 2014-08-25
forum: General Help
---

### Post by clint4 on 2014-08-25
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I am creating a custom live cd using UCK and after installing the applications I want I would like them to be the only apps on the launcher.  I have tried editing 
```
[/COLOR][FONT=Ubuntu Mono]gsettings get com.canonical.Unity.Launcher favorites[/FONT][COLOR=#000000]
```
using
```
[/COLOR][FONT=Ubuntu Mono]gsettings set com.canonical.Unity.Launcher favorites[/FONT][COLOR=#000000]
```
and while the settings save it does not appear to edit the launcher for the user name I log into.  If the username is "student" where would I find the launcher config file for that username?  Thanks in advance.[/COLOR]

---

### Post by mc4man on 2014-08-25
I think you may be approaching the wrong way. As far as gsettings - those settings are saved per user in ~/.config/dconf/user which is not user readable.

All new users (including the first user on a fresh install) get a launcher populated as set in /usr/share/glib-2.0/schemas/com.canonical.Unity.gschema.xml
as in - (the ubiquity icon is only used for live session.
```
    </key>
  </schema>
  <schema path="/com/canonical/unity/launcher/" id="com.canonical.Unity.Launcher" gettext-domain="unity">
    <key type="as" name="favorites">
      <default>[
        'application://ubiquity.desktop',
        'application://nautilus.desktop',
        'application://firefox.desktop',
        'application://libreoffice-writer.desktop',
        'application://libreoffice-calc.desktop',
        'application://libreoffice-impress.desktop',
        'application://ubuntu-software-center.desktop',
        'application://ubuntu-amazon-default.desktop',
        'application://unity-control-center.desktop',
        'unity://running-apps',
        'unity://expo-icon',
        'unity://devices'
      ]</default>
      <summary>List of items that should be shown by default in the launcher</summary>
      <description>These items can be: application://desktop-id.desktop, device://uiid and unity://special-id (including: unity://running-apps (icons of running applications) unity://devices (icons of attached devices), unity://expo-icon (icon of the workspace switcher) and unity://desktop-icon (the show-desktop icon)); the order of this list determines the launcher item's position.</description>
```
So editing there & then compiling the schema would then use the edited list for any new user.
Note that the unity://....  probably should not be removed, as far as the application://.. ones your are free to alter as long as the .desktop does exist (the app is installed

If you do edit that file (or any glib schema) then you must (re)compile the schemas for it to take affect. Also note that *any* error in editing will be reported during the compile, they **must be taken care of before a log out or reboot**, otherwise the schema may be ignored in part or in  full which could be quite a problem.

To compile schemas - 
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

It should complete **without any comment** in the terminal, if anything is presented then read & **fix**

Edit: it would be a good idea to back up the schema file before fooling with..

---

