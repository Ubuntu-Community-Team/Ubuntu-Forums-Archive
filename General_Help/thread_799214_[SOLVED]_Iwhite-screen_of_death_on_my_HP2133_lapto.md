---
title: "[SOLVED] Iwhite-screen of death on my HP2133 laptop after installing WUBI"
date: 2008-05-18
forum: General Help
---

### Post by aeshanw on 2008-05-18
I just installed WUBI via Vista on my HP2133 laptop.some forums say the white screen is due to ubuntu conflicting with the  VIA-chipset.How can add xforcevesa to the GRUB on ubutntu-boot?

---

### Post by abn91c on 2008-05-18
that could also be that compiz or beryl is activated and it doesnt like you video card because it does not have openGL or 3d support, reboot then start linux in safemode then check the settings for the video card

---

### Post by aeshanw on 2008-05-18
Hi there,
I tried safe-mode but i get:
"Loop-mounted file systems already present" in an error dialog box which (despite clicking OK) refuses to go away.Any diea what might be causing this? As i did install ubuntu into the disk via WUBI , so id dont see why the installer should activate itself again.thanks!

---

### Post by aeshanw on 2008-05-18
how can I enter linux command-line mode directly?coz it looks like somethings wrong with my kernal =(
how can u disable compix/beryl?
Cheers!

---

### Post by ago on 2008-05-19
> **aeshanw said:**
> Hi there,
I tried safe-mode but i get:
"Loop-mounted file systems already present" in an error dialog box which (despite clicking OK) refuses to go away.Any diea what might be causing this? As i did install ubuntu into the disk via WUBI , so id dont see why the installer should activate itself again.thanks!
You may wanto to uninstall and reinstall
Press esc at boot after "ubuntu" and select safe graphic mode

---

### Post by aeshanw on 2008-05-19
Hi Ago,
Thanks for the tip.I uninstall/reinstall'd it and it now works!just have a few minor gfx tweaks but my next concern is WiFi =) .for which I'll close this thread and open a new one.
Cheers!

---

### Post by alexzzz on 2008-07-03
> **ago said:**
> You may wanto to uninstall and reinstall
Press esc at boot after "ubuntu" and select safe graphic mode

I have the same problem and haven't understand exactly what to do. Can you please explain it a little bit?

---

### Post by ago on 2008-07-03
> **alexzzz said:**
> I have the same problem and haven't understand exactly what to do. Can you please explain it a little bit?

Uninstall wubi
defragment + run chkdsk /r (never hurts)
Install wubi (better if you use 8.04.1) again 
Then if you still have problem, at boot time, after you select "Ubuntu", press ESC at the countdown. You will see some extra boot options. Try them out.

---

