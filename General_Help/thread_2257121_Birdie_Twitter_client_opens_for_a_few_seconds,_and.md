---
title: "Birdie Twitter client opens for a few seconds, and then closes"
date: 2014-12-17
forum: General Help
---

### Post by RichieB07 on 2014-12-17
[COLOR=#333333][FONT=UbuntuRegular]I have the Birdie Twitter client installed on my Ubuntu 14.04 machine, and when I click on the icon, the windows opens for a good 1-2 seconds, then closes. Nothing shows up on the UI that opens, and the window just closes.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Running "sudo start birdie" gives the "start Unknown job: birdie" error.[/FONT][/COLOR]

---

### Post by oldos2er on 2014-12-17
Try ```
birdie
``` in a terminal to see if it outputs anything useful.

---

### Post by RichieB07 on 2014-12-17
> **oldos2er said:**
> Try ```
birdie
``` in a terminal to see if it outputs anything useful.

After putting that in, it comes out with this: 

[_LEVEL_INFO 21:36:00.936354] Birdie.vala:194: Birdie version: 1.1
[_LEVEL_INFO 21:36:00.936462] Birdie.vala:196: Kernel version: 3.13.0-43-generic
[_LEVEL_FATAL 21:36:01.847130] Twitter.vala:343: Authorization Required
[_LEVEL_FATAL 21:36:01.847251] birdie will not function properly.
Segmentation fault

---

### Post by RichieB07 on 2014-12-19
Bumping up since it's been two days.

---

