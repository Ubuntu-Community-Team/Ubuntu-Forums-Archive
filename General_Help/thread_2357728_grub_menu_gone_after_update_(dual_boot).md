---
title: "grub menu gone after update (dual boot)"
date: 2017-04-05
forum: General Help
---

### Post by geegee2 on 2017-04-05
This has been asked before but the solutions dont work.

I upgraded kubuntu xenial.

it also popped up  a window that some aditional software was needed like intel cpu code.

anyway,
i did as aksed and upgraded and rebooted and now it boots straight to windows.

i already ran [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
but after reboot nothing changed... straight to windows.. no grub menu whatsoever.

how to fix this?

---

### Post by geegee2 on 2017-04-05
guess i fixed it by using windows.... to load the grub boot.

in admin cmd:

> [COLOR=#282828][FONT=InconsolataMedium]bcdedit /set [/FONT][/COLOR][COLOR=#666666][FONT=InconsolataMedium]{[/FONT][/COLOR][COLOR=#282828][FONT=InconsolataMedium]bootmgr[/FONT][/COLOR][COLOR=#666666][FONT=InconsolataMedium]}[/FONT][/COLOR][COLOR=#282828][FONT=InconsolataMedium] path [/FONT][/COLOR][COLOR=#BB6622][FONT=InconsolataMedium]**\E**[/FONT][/COLOR][COLOR=#282828][FONT=InconsolataMedium]FI[/FONT][/COLOR][COLOR=#BB6622][FONT=InconsolataMedium]**\u**[/FONT][/COLOR][COLOR=#282828][FONT=InconsolataMedium]buntu[/FONT][/COLOR][COLOR=#BB6622][FONT=InconsolataMedium]**\g**[/FONT][/COLOR][COLOR=#282828][FONT=InconsolataMedium]rubx64.efi[/FONT][/COLOR]

---

### Post by dvd65 on 2017-04-06
Had the same issue since a couple of days on Ubuntu 16.04.2 LTS. Boot-repair wasn't sufficient, but the command as described above did the trick.
Thanks!

---

