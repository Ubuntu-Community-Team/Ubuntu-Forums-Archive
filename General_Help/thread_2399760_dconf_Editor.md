---
title: "dconf Editor"
date: 2018-08-29
forum: General Help
---

### Post by AngelOfNorath on 2018-08-29
Hello everyone,

I have a problem with Ktorrent, its tray icon won't appear on my system tray (I use Ubuntu 16.04). After reading a lot of threads I came to the solution of dconf Editor, in order to whitelist the systray icons. When I opened the dconf Editor the "Panel" option under the "Desktop" section wouldn't exist, along with other options. Is there any way to fix this? 

** My main problem is the system tray icons. If you have a better solution to propose than dconf Editor, don't hesitate!


Here is a picture of what I see.

[ATTACH=CONFIG]280883[/ATTACH]

This is what according to the Solution Threads I should see (I took this pic from the internet)

[ATTACH=CONFIG]280884[/ATTACH]

---

### Post by Frogs Hair on 2018-08-29
Try looking for the application in the dconf-editor under org>gnome. If it appears there check for options that apply to the tray icon.

---

### Post by AngelOfNorath on 2018-08-29
I also searched the under options and found nothing similar. Here, take a look:

[ATTACH=CONFIG]280891[/ATTACH]

---

### Post by Frogs Hair on 2018-08-29
Can you link the source of the information about using the dconf-editor in order to whitelist the systray icons ?

---

### Post by deadflowr on 2018-08-29
Is this what you are running into:
[https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/1440884]("https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/1440884")

Also, your screenshots of your dconf editor are highlighting the top sections which are empty .
(The first post you had was highlighting the apps directory, the second  highlighted the top org directory.
Those in and of themselves have no schemas so no information will be shown in the main window area.)

And the screenshot from the Solution thread you found is rather old I think, the unity sub section would be in com.canonical now.

---

### Post by AngelOfNorath on 2018-08-29
[https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/1440884](https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/1440884)

> [COLOR=#333333][FONT=monospace]KTorrent have «show tray icon» enabled, but it shows a tray icon only when downloading something. Such behavior is only for unity and does not appears in KDE, Cinnamon, XFCE and so on, so I belive, this can be a Unity bug. Or both.[/FONT][/COLOR]

Yes, this is my problem. Actually, I was triggered creating a thread here because I remember myself seeing the tray icon, but I don't remember when. Maybe it was when downloading.

---

### Post by AngelOfNorath on 2018-08-29
> **deadflowr said:**
> Is this what you are running into:
[https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/1440884](https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/1440884)

Also, your screenshots of your dconf editor are highlighting the top sections which are empty .
(The first post you had was highlighting the apps directory, the second  highlighted the top org directory.
Those in and of themselves have no schemas so no information will be shown in the main window area.)

And the screenshot from the Solution thread you found is rather old I think, the unity sub section would be in com.canonical now.


Yes I know, the highlighted sections are empty. But their ***children ***are not! (as they should be).I searched in different sections and their children but I had not luck finding the ***Panel ***section...

If you want I cant capture a screenshot of the child directories.

---

### Post by AngelOfNorath on 2018-08-29
> **Frogs Hair said:**
> Can you link the source of the information about using the dconf-editor in order to whitelist the systray icons ?


Here are your links!:

1. [https://askubuntu.com/questions/456950/system-tray-icons-disappeared-after-upgrading-ubuntu](https://askubuntu.com/questions/456950/system-tray-icons-disappeared-after-upgrading-ubuntu)
2. [https://www.youtube.com/watch?v=30GOGXhHOHE](https://www.youtube.com/watch?v=30GOGXhHOHE)

---

