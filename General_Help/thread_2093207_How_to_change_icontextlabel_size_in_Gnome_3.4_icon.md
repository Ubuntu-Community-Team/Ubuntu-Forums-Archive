---
title: "How to change icon/textlabel size in Gnome 3.4 icon grid"
date: 2012-12-10
forum: General Help
---

### Post by hzFVOW00pw on 2012-12-10
The standard icons in the application grid are way too big and the text labels are cut short which makes long titles unreadable. A number of applications don't even have an icon with high enough resolution, these icons will appear blurred or jagged if they are enlarged too much. To fix these annoyances you can either edit the file /usr/share/gnome-shell/theme/gnome-shell.css or you can copy the whole /usr/share/gnome-shell/theme folder to ~/.themes/CustomTheme/gnome-shell and edit the file from there.

All the following commands can be run from a Terminal, like for instance gnome-terminal. You can easily select and copy a command from this page, then paste it in a terminal, and hit enter.

To edit the global theme css file directly, run in a terminal this command:

```
sudo gedit /usr/share/gnome-shell/theme/gnome-shell.css
```

Then look for this code:

```
/* Application Launchers and Grid */

.icon-grid {
    spacing: 36px;
    -shell-grid-horizontal-item-size: 118px;
    -shell-grid-vertical-item-size: 118px;
}

.icon-grid .overview-icon {
    icon-size: 96px;
}
```

...and alter it to:

```
/* Application Launchers and Grid */

/* Size of grid cell for one icon */ 

.icon-grid {
    spacing: 0px; /* was 36px */
    -shell-grid-horizontal-item-size: 280px; /* was 118px */
    -shell-grid-vertical-item-size: 120px; /* was 118px */
}

/* Size of one icon */ 

.icon-grid .overview-icon {
    icon-size: 64px; /* was 96px */
}

/* Size of the text label for one icon */ 

.icon-grid .app-well-app > .overview-icon,
.search-result-content > .overview-icon {
    width: 280px; /* new entry */
    height: 120px; /* new entry */
}
```

You can vary the numbers to suit you. These are the settings that work best with my 1920x1080 monitor.

To view your changes you have to save the file, and then restart the Gnome Shell by pressing Alt+F2 and enter "r" or "restart". There is no need to close your applications, they will keep running.

If you edit the global theme ccs file directly like I described here then your changes will be overwritten in case of a Gnome Shell upgrade. That's why it might be wiser to copy the theme to your home directory an edit it from there.

First, create a directory for your custom theme:

```
mkdir -p ~/.themes/CustomTheme/gnome-shell
```

(You can replace the name CustomTheme with anything you like. The name will show up in tools like Gnome Tweak Tool / Advanced Settings)

Copy the theme:

```
cp /usr/share/gnome-shell/theme/* ~/.themes//CustomTheme/gnome-shell
```

Of course if you are really lazy you could just use a graphical file manager like Nautilus or Thunar or even MC to accomplish these tasks.

To make use of custom user themes you have to install the "User Themes" extension from this page: [https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)

Once installed you start the Gnome Tweak Tool (Advanced Settings) and choose the theme from the dropdown list in "Theme > Shell theme". Choose the name of your user theme directory, in this case "CustomTheme".

Then edit the file ~/.themes//CustomTheme/gnome-shell/gnome-shell.css as described above.

```
gedit  ~/.themes//CustomTheme/gnome-shell/gnome-shell.css
```

To view your changes you have to save the file, and then restart the Gnome Shell by pressing Alt+F2 and enter "r" or "restart".

---

