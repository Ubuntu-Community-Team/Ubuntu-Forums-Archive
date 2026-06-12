---
title: "Uninstalled software still appears in Ubuntu Software. Can't remove it"
date: 2017-12-20
forum: General Help
---

### Post by bronxio on 2017-12-20
Hi. I want to use Telegram Desktop in Ubuntu. I've installed it from the official web (not a .deb package), but I missed it up a little bit (I'm afraid) and I had two Telegram icons in my dash. I had it with automatic startup, had a minor bug (had to open it twice to show the window when minimized in tray) and, as far as I know, it never was able to update. So I tried to uninstall both through Ubuntu Software, and one of them was fine, but the other one, I clicked in the uninstall button, Ubuntu ask me for the confirmation as usual, and then it doesn't even ask me for the root password: it acts like I cancelled the operation.

It was still appearing in my dash as well, but I erased manually files from usr/share with "telegram" in the name and nothing. telegram-desktop doesn't appear anymore in terminal neither (starting typing and tab)

I installed the "telegram-sergiusens" for a try anyway, and the Telegram icon in the system tray doesn't appear anymore. Instead, it appears that classic icon indicating it couldn't load it (yes, I deleted manually it before as well, but I thought the telegram-sergiusens installer will put it again there) and it forgets everything when I close it (Telegram tells me "welcome!" again as it's the first time I log in).

So... Any ideas/suggestions to remove all the telegram-desktop stuff completely to be able to make a fresh, new and healthy installation? Where "Ubuntu Software" looks for the installed software? It's obvious that Telegram is still there...

Any help will be appreciated! :)

---

### Post by monkeybrain20122 on 2017-12-20
> **bronxio said:**
> Hi. I want to use Telegram Desktop in Ubuntu. I've installed it from the official web (not a .deb package), but I missed it up a little bit (I'm afraid) and I had two Telegram icons in my dash. I had it with automatic startup, had a minor bug (had to open it twice to show the window when minimized in tray) and, as far as I know, it never was able to update. So I tried to uninstall both through Ubuntu Software, and one of them was fine, but the other one, I clicked in the uninstall button, Ubuntu ask me for the confirmation as usual, and then it doesn't even ask me for the root password: it acts like I cancelled the operation.

It was still appearing in my dash as well, but I erased manually files from usr/share with "telegram" in the name and nothing. telegram-desktop doesn't appear anymore in terminal neither (starting typing and tab)

I installed the "telegram-sergiusens" for a try anyway, and the Telegram icon in the system tray doesn't appear anymore. Instead, it appears that classic icon indicating it couldn't load it (yes, I deleted manually it before as well, but I thought the telegram-sergiusens installer will put it again there) and it forgets everything when I close it (Telegram tells me "welcome!" again as it's the first time I log in).

So... Any ideas/suggestions to remove all the telegram-desktop stuff completely to be able to make a fresh, new and healthy installation? Where "Ubuntu Software" looks for the installed software? It's obvious that Telegram is still there...

Any help will be appreciated! :)

You probably have a telegram .desktop file in your ~/.local/share/applications, jut delete it (it is called telegramdesktop.desktop in mine. I installed from telegram's website. Works great, and I get updates often by just opening it) .local is a hidden folder to see it, open your file manager,  press ctrl+H or choose show hidden from menu.

---

### Post by bronxio on 2017-12-20
Thanks, Monkeybrain! I did what you wrote: I deleted that .desktop file from the first .local folder I found using the search box in nautilus (can't remember its path) and yes, it disappeared from Ubuntu Software (great!) I installed it again from the official web (extracted the Telegram folder and moved to /opt with root permissions, as I did the first time), but I noticed that the settings were saved and the icon doesn't appear yet (and I don't remember where it was -.-u ). So I rebooted just to check if the icon doesn't appear anymore until I place it manually again.

Telegram tried to open (it's still in the startup programs), and told me that it can't open a file for writing (/home/bross/.local/share/TelegramDesktop/tdata/working). I searched for .local in nautilus in root mode, and I found 2 .local folders: one in the root folder, and one in my personal one. telegramdesktop.desktop is in the root one, but not in the personal folder one.

I'm afraid that I still needed to remove more things to be able to do a fresh new installation... What would be easier? Uninstalling again, removing everything manually  about Telegram and reinstalling, or fix manually this installation? Does anyone knows any of these ways?

Here is the log it showed me:

 [I][2017.12.20 23:28:48] Launched version: 1002001, alpha: [FALSE], beta: 0, debug mode: [FALSE], test dc: [FALSE]
[/I]
[I][2017.12.20 23:28:48] Executable dir: /opt/Telegram/, name: Telegram
[/I]
*[2017.12.20 23:28:48] Initial working dir: /home/bross/*
[I][2017.12.20 23:28:48] Working dir: /home/bross/.local/share/TelegramDesktop/
[/I]
[I][2017.12.20 23:28:48] Command line: /opt/Telegram/Telegram -startintray
[/I]
*[2017.12.20 23:28:47] Executable path before check: /opt/Telegram/Telegram*
*[2017.12.20 23:28:48] Logs started*
*[2017.12.20 23:28:51] Connecting local socket to /tmp/ad231d139808edefd56444d53eda8599-{87A94AB0-E370-4cde-98D3-ACC110C5967D}...*
*[2017.12.20 23:28:51] This is the only instance of Telegram, starting server and app...*
*[2017.12.20 23:28:51] Moved logging from '/home/bross/.local/share/TelegramDesktop/log_start0.txt' to '/home/bross/.local/share/TelegramDesktop/log.txt'!*
[I][2017.12.20 23:28:51] Opened '/home/bross/.local/share/TelegramDesktop/tdata/working' for reading, the previous Telegram Desktop launch was not finished properly :( Crash log size: 0
[/I]
*[2017.12.20 23:28:51] FATAL: Could not open '/home/bross/.local/share/TelegramDesktop/tdata/working' for writing!*

---

### Post by bronxio on 2017-12-23
Ok, now I relaized that I can't open Audacity (it flashes in the apps bar and then dissapear), tried to uninstall through ubuntu Software, but does the same than with Telegram before I erased the file that MonekyBrain told me.

Any ideas to completely remove these applicatons or, at least, to know what happened? Why software installations are that corrupted?

---

