---
title: "Ubuntu 22.04. How to change primary login monitor away from external HDMI monitor."
date: 2022-11-09
forum: General Help
---

### Post by Advait on 2022-11-09
[COLOR=#000000][FONT=Arial]AMD laptop with Ubuntu 22.04 Gnome Wayland. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]A few days ago I executed this command to change my primary login monitor to my external HDMI monitor:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo cp ~/.config/monitors.xml /var/lib/gdm3/.config/[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](This command sets the external monitor as the boot login monitor.)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]How do I reverse this command? I want to change my primary monitor back to the laptop monitor.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]See this page for more details: [https://ubuntuhandbook.org/index.php/2022/11/login-screen-external-monitor-ubuntu/](https://ubuntuhandbook.org/index.php/2022/11/login-screen-external-monitor-ubuntu/)[/FONT][/COLOR]

---

### Post by philhughes on 2022-11-09
Just delete the file and restart:

```
sudo rm /var/lib/gdm3/.config/monitors.xml
```

---

### Post by kurt18947 on 2022-11-09
I'm using dual desktop monitors but I assume the procedure would be the same. No need to edit or create any files. This is using the default Ubuntu desktop

- Click the top right corner
- Settings
- Displays
   You'll see a window with several choices. On top will be 3 choices - Joint Displays, Mirror or Single display. I have Join Displays selected. The rest you 
   figure out. The Primary Display will be the one with the top bar and controls. The only glitch I've run into is the mouse cursor not moving from one display to another; I've had to run the cursor off the right edge of the right monitor then it appears on the left monitor. What fixes that for me is to switch the position of the two monitors on the Displays page. They're labelled 1 & 2, drag 2 to the left of 1. You may want to switch the Primary Display designation so the top bar is where you want it. Hope this helps.

---

### Post by philhughes on 2022-11-10
What you are describing is the procedure to change the monitor arrangement once you have logged in. However, when you have done this, sometimes the arrangement of the monitors at the login screen (which is what Advait is asking about) will not be the same, and will not be affected by the changes you make from Settings > Screen Display. In this case the solution is to copy the monitors.xml file (which is created when you make changes from Settings) to /var/lib/gdm3/.config/, as shown in the original post.

---

### Post by Advait on 2022-11-10
> **philhughes said:**
> Just delete the file and restart:

```
sudo rm /var/lib/gdm3/.config/monitors.xml
```

A simple solution. Nice! My favorite kind. Thanks.

---

