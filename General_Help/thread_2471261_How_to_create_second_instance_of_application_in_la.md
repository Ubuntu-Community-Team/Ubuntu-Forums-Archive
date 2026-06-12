---
title: "How to create second instance of application in launcher bar"
date: 2022-01-24
forum: General Help
---

### Post by temporos on 2022-01-24
I set up a new profile called "App" in Firefox to run WhatsApp Web in its own window with a customized interface. Essentially, I'm trying to make it look like its own application separate from Firefox. I created a .desktop file for it, so it shows up in the Ubuntu launcher, but it still shows as a Firefox window in the launcher bar after it's launched. I'd like it to show up as a separate "app" using the icon specified in the .desktop file. How can I do this?

.desktop file
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289900&stc=1[/IMG]

.sh file
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289899&stc=1[/IMG]

Launcher Bar - See how it shows as an open Firefox window (with the dot)? I want it to show up as a new item in the bar using the specified icon.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289901&stc=1[/IMG]

---

### Post by vanadium on 2022-01-25
Run firefox with the GTK --class option to set a custom WMClass, then in your desktop launcher, refer to that WMClass you have set with a "StartupWMClass" entry key.

---

### Post by temporos on 2022-01-26
> **vanadium said:**
> Run firefox with the GTK [FONT=courier new][COLOR=#0000cd]--class[/COLOR][/FONT] option to set a custom WMClass, then in your desktop launcher, refer to that WMClass you have set with a "StartupWMClass" entry key.
I'm not familiar with GTK classes. Do I just use an arbitrary name for the class, like [COLOR=#0000cd][FONT=courier new]firefox --class WhatsApp[/FONT][/COLOR] to create the class, and then stick [FONT=courier new][COLOR=#0000cd]StartupWMClass=WhatsApp[/COLOR][/FONT] in the .desktop file? Will (how will) this affect all other apps that don't use the [COLOR=#0000cd][FONT=courier new]--class[/FONT][/COLOR] option?

---

### Post by temporos on 2022-01-26
OK, it's running the way I wanted it now. I created a new class by running [COLOR=#0000cd][FONT=courier new]firefox --class=WhatsApp[/FONT][/COLOR], and then changing the .sh file to execute ```
[FONT=courier new][COLOR=#0000cd]firefox --new-instance -P WhatsApp --class=WhatsApp https://web.whatsapp.com[/COLOR][/FONT]
``` Now I have a separate WhatsApp icon in the dock while running it, and it's using the custom WhatsApp profile theme and settings.

Curiously, putting the executable command in the .desktop file would ignore the [FONT=courier new][COLOR=#0000cd]--class=WhatsApp[/COLOR][/FONT] argument, and adding [FONT=courier new][COLOR=#0000cd]StartupWMClass=WhatsApp[/COLOR][/FONT] was also ignored. The only way I could get it to work was putting the whole executable string (including the [COLOR=#0000cd][FONT=courier new]--class[/FONT][/COLOR] argument) in a .sh file, and then telling the .desktop file to execute the .sh file.

---

### Post by temporos on 2022-08-15
Unfortunately, this solution no longer works after the upgrade to LTS 22.04.1, and Firefox's switch to Snap. The launcher icon shows up in the applications launcher, but it launches under the Firefox icon already on the launcher bar, not as a separate icon. Any ideas? Here's what I have currently...

whatsapp-web.sh
```
#!/bin/sh
firefox -new-instance -P WhatsApp --class=WhatsApp https://web.whatsapp.com
```

whatsapp.desktop
```
[Desktop Entry]
Type=Application
Name=WhatsApp Web
Exec="/home/[user]/snap/firefox/common/.mozilla/firefox/qn2p5hav.WhatsApp/whatsapp-web.sh"
Icon=/home/[user]/.local/share/icons/whatsapp.png
StartupWMClass=WhatsApp
```

---

### Post by temporos on 2022-08-19
Marking this as "unsolved" again, since Jammy doesn't want to cooperate with what worked in Focal.

Anyone have an idea how to fix this? I want separate instances/profiles in Firefox to appear in the launcher bar as separate icons, not stacked Firefox icons with dots.

---

### Post by dragonfly41 on 2022-08-19
The "hack" I used with another application was to simply clone the binary and name it app2 as executable.

Then I could use /usr/bin/app1 to call /usr/bin/app2 (clone of app1).

---

### Post by temporos on 2022-08-19
That's an idea, but I have a couple concerns...
[LIST=1]
[*]Where even *is* the binary for Firefox now that it's a snap? 
[*]Wouldn't that cause a situation where you need to re-clone the binary every time there's a package upgrade? 
[/LIST]
 After much searching, I found a [question on AskUbuntu]("https://askubuntu.com/questions/1423412/multiple-firefox-icons-on-dock-in-22-04") that's almost the same as this thread. It sounds like using profiles and WM classes to separate the icons in the Ubuntu dock is no longer possible with snapped applications, which Firefox now is. Since the snapped one is, unfortunately, the official one, I'd prefer to use it instead of installing the PPA version.

It sounds like this is actually an issue with snap, and not with Firefox, so other snapped applications will have this same issue. It's a drawback of snap currently, but hopefully, they'll fix it as snapped apps become more widespread.

Going to leave this thread as "unsolved," because, well, it's *not* solved. At least, not until snap is fixed to allow it. In the meantime, I'll install Chrome to use specifically for this use case, since Chrome has the "launch as application" feature for websites, which is effectively what I'm trying to get Firefox to do. For general browsing, I'll continue to use Firefox as the default.

---

### Post by dragonfly41 on 2022-08-19
The _untested_ idea would be to clone/rename/install the cloned Firefox extension

---

