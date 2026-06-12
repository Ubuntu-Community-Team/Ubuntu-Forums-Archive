---
title: "Keyboard Keys 6 and 7 Not Working - Seeking Assistance"
date: 2023-10-28
forum: General Help
---

### Post by littleskeleton on 2023-10-28
Hello Ubuntu Community,
I am encountering an issue with my laptop keyboard where the keys "6" and "7" are not functioning. I have attempted various solutions to input these characters without success. I seek assistance in resolving this matter or finding alternative methods to input these specific characters.
I have tried the following methods to input "6" and "7" without success:

[LIST=1]
[*]**Physical Keys Not Working:** The "6" and "7" keys on my laptop keyboard are unresponsive, and I'm unable to physically replace them at the moment.

[*]**xdotool Method:** I attempted to use xdotool to simulate key presses. Despite installing xdotool and setting up custom shortcuts, the command does not seem to work as intended. I used the following command in the custom shortcuts: xdotool key 6 for "6" and xdotool key 7 for "7".
[/LIST]
I am seeking guidance on potential solutions or alternative methods to input "6" and "7" until I can resolve the issue with these specific keys on my keyboard.
Could someone provide insight or alternative solutions to this issue? Any guidance, advice, or additional methods that could help me input these characters without using the physical keys would be greatly appreciated.
Thank you for your time and assistance.

---

### Post by dragonfly41 on 2023-10-28
One interim suggestion .. until key fault is diagnosed 

Install Florence Virtual Keyboard

---

### Post by MAFoElffen on 2023-10-28
Note: xdotool and most other keyboard remapping ututilies work when using X11 as the Graphics renderer...

So the easiest way is to ensure you are not using Wayland...

If you need to edit / remap keys in Wayland, you need to remap udev / evdev: [https://www.foell.org/justin/remapping-keyboard-keys-in-ubuntu-with-udev-evdev/](https://www.foell.org/justin/remapping-keyboard-keys-in-ubuntu-with-udev-evdev/)

Have you thought about or looked into just replacing your keyboard? I am assuming this is maybe a laptop or notebook? A new keyboard for mine was only $35 on Amazon. I started losing keys, and some would stick. Never knew exactly how much it was really worn out until I replaced it, and now, night-and-day difference.

Some times the time and effort we spend on avoiding or working around "a problem" ends up costing us much more.

---

