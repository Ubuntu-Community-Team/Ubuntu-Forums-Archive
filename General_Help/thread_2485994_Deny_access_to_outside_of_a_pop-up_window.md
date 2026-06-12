---
title: "Deny access to outside of a pop-up window"
date: 2023-04-17
forum: General Help
---

### Post by loresucrub on 2023-04-17
Hi all,

When the system is turned on, I project a screen to the users over IP, how can I prevent the transition to another screen other than this screen?

Users should only have access to that screen. they should not be able to access the start menu.

GNOME version 3.36.8  Ubuntu 20.04.5 LTS

---

### Post by TheFu on 2023-04-17
If you don't want any menus, don't run a DE. Use a WM and customize it so there aren't any menus.

---

### Post by ActionParsnip on 2023-04-17
Is the thing you are presenting in a web browser?

---

### Post by loresucrub on 2023-04-17
Yes, firefox kiosk mode

---

### Post by loresucrub on 2023-04-17
[COLOR=#000000]Yes, firefox kiosk mode[/COLOR]

---

### Post by ActionParsnip on 2023-04-17
Then add a startup item to run the below script
```

#!/bin/bash


while true; do
firefox -kiosk https://www.bbc.co.uk
done

```

Change the URL to what you want to use. Even if the user closed the browser, it'll just relaunch

---

### Post by TheFu on 2023-04-18
> **loresucrub said:**
> [COLOR=#000000]Yes, firefox kiosk mode[/COLOR]

If all you want is a web browser and nothing else, I wouldn't use Ubuntu.  I'd setup TinyCore Linux with just a minimal X/Windows + Browser environment. It will load into RAM (65MB) and run as fast as CPU can go. Nothing extra, so there won't be much worry about hacking.

---

### Post by ActionParsnip on 2023-04-18
> **TheFu said:**
> If all you want is a web browser and nothing else, I wouldn't use Ubuntu.  I'd setup TinyCore Linux with just a minimal X/Windows + Browser environment. It will load into RAM (65MB) and run as fast as CPU can go. Nothing extra, so there won't be much worry about hacking.

Absolutely this. Why install more than you need. Puppy Linux is good too. I miss the old XPud days. That distribution was awesome and would totally fit the bill here

---

