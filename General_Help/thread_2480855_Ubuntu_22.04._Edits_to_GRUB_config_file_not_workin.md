---
title: "Ubuntu 22.04. Edits to GRUB config file not working."
date: 2022-11-12
forum: General Help
---

### Post by Advait on 2022-11-12
[COLOR=#000000][FONT=Arial](I’m a noob and know very little about terminal commands and almost nothing about how Linux works under the hood.)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]See attached image. I want my system to default boot from the top menu item (Ubuntu) and not from the 3rd menu item (which it does now).[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]So I edited the Grub file and changed GRUB_DEFAULT=2 to GRUB_DEFAULT=0. Then I saved the edited file and then reopened the file to make sure the change was there. (see attached image)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Then I rebooted and it still default booted from the 3rd item. Grrrr![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Any ideas why the change isn’t working? Any commands I can run to diagnose this issue? Does the location of my /boot/efi/ partition make a difference? (see attached image)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]In my laptop are 2 nvme drives. My main one (2TB, n1p2) and a smaller one (500GB, n1p1). The 2nd one also has Ubuntu 22.04 in case the main nvme goes bad.

[IMG]https://imgur.com/ACn43rU.png[/IMG]
[/FONT][/COLOR]

---

### Post by coley9225 on 2022-11-12
You didn't mention if you updated the grub prior to the reboot. If you did not, that's the problem. Recheck the grub file, and if it is still OK, run sudo update grub, then try a new reboot. Good luck.

---

### Post by &amp;KyT$0P# on 2022-11-12
> **coley9225 said:**
> run sudo update grub, then try a new reboot.

This, but the correct command to run is
```
sudo update-grub
```

---

### Post by Advait on 2022-11-12
> **halogen2 said:**
> This, but the correct command to run is
```
sudo update-grub
```

Worked great. Thanks! I saw this on the website but forgot when I did the edit.

---

### Post by Impavidus on 2022-11-12
It's mentioned in the comment on the first line of the file you edited.

---

### Post by Advait on 2022-11-13
> **Impavidus said:**
> It's mentioned in the comment on the first line of the file you edited.

Yep, I saw that earlier but it didn't stick in my mind. Got it now. :-)

---

