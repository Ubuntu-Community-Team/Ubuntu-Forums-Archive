---
title: "Webapp created with Ice doesn't show the right icon in dock"
date: 2023-03-19
forum: General Help
---

### Post by frenchynerd on 2023-03-19
I've migrated recently from Linux Mint, where the webapp function was very handy.

I tried to install it on Ubuntu, but the installation failed. I've discovered another webapp manager called Ice. I've set it up to be able to use ProtonCalendar and set it up so it would use the favicon from the website. However, in the dock, it's the Chromium icon that shows. How can I change that?

---

### Post by MAFoElffen on 2023-03-19
Summarized answer, as I am going out the door to work: Edit the application's startup .desktop file of the 'shortcut', and change the icon= line to point to whatever icon you want it to be.

Maybe someone else can explain that to you while I am at work. If not, then I'll finish answering that when I return.

---

### Post by frenchynerd on 2023-03-19
The .desktop file reads like this:
> [Desktop Entry]
Version=1.0
Name=ProtonCalendar
Comment=ProtonCalendar (Ice SSB)
Exec=chromium-browser --app=https://calendar.proton.me --class=ICE-SSB-protonca>
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/home/user/.local/share/ice/protoncalendar.ico
Categories=GTK;Network;
MimeType=text/html;text/xml;application/xhtml_xml;
StartupWMClass=ICE-SSB-protoncalendar
StartupNotify=true



The correct icon is selected. In the app launcher and in the menu, it's the correct icon. But not in the dock. In the dock, I'm stuck with Chromium's icon.

---

### Post by MAFoElffen on 2023-03-20
Can you post the content of the .desktop file for me to look at please?

---

### Post by frenchynerd on 2023-03-20
> **MAFoElffen said:**
> Can you post the content of the .desktop file for me to look at please?


[Desktop Entry]
Version=1.0
Name=ProtonCalendar
Comment=ProtonCalendar (Ice SSB)
Exec=chromium-browser --app=https://calendar.proton.me --class=ICE-SSB-protonca>
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/home/user/.local/share/ice/protoncalendar.ico
Categories=GTK;Network;
MimeType=text/html;text/xml;application/xhtml_xml;
StartupWMClass=ICE-SSB-protoncalendar
StartupNotify=true

---

