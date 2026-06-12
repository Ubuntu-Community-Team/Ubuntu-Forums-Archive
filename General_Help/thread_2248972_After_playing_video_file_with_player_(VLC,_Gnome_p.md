---
title: "After playing video file with player (VLC, Gnome player) Chrome cant start."
date: 2014-10-18
forum: General Help
---

### Post by GYcode on 2014-10-18
Hi, 
i have played video file with video player, after that trying to open google chrome, but it freezes on opening, just shows in status bar chrome panel.
And then i loging out from lubuntu and loging back, chrome starts normaly, but then i after chrome is closed, and i play some video with vlc player, 
chrome wont start again. Same for chrome or chromium, but firefox starts normally with no problem. 
With xubuntu same problem.

Then opening with terminal getting error:
> gytisc@gytisc-desktop:~$ google-chrome
[8619:8619:1018/212233:ERROR:process_singleton_posix.cc(241)] readlink(/tmp/.com.google.Chrome.4suShd/SingletonCookie) failed: Permission denied
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[8661:8661:1018/212233:ERROR:sandbox_linux.cc(305)] InitializeSandbox() called with multiple threads in process gpu-process
[8619:8619:1018/212234:ERROR:desktop_window_tree_host_x11.cc(1547)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState)
[8619:8619:1018/212234:ERROR:desktop_window_tree_host_x11.cc(802)] Not implemented reached in virtual void views::DesktopWindowTreeHostX11::InitModalType(ui::ModalType)
[8619:8683:1018/212237:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates
[8661:8669:1018/212245:ERROR:gpu_watchdog_thread.cc(253)] The GPU process hung. Terminating after 10000 ms.

Anybody can halp ? I like chrome, becouse for me its faster browsing, but this bug very annoying.

---

### Post by GYcode on 2014-10-19
Then playing video with gnome player and  closing it immediately, chrome will not start, but then playing with VLC  player and closing it immediately after starting video, google chrome  will start normally!!! But... then played video with VLC player longer  approximately 1 minute, it could be shorter or longer I don't know, but  after ~1 min. something happening, and Chrome will not start! Omg weird  bug! But question is??? Why gnome player doing this to something  immediately, but VLC player need to be played longer??? The answer is  there.

---

### Post by mc4man on 2014-10-19
Set up your fail scenario but try opening chrome or chromium with this option 
```
--disable-gpu-watchdog
```
Does that help?

---

### Post by GYcode on 2014-10-19
Not helped.

> gytisc@gytisc-desktop:~$ google-chrome --disable-gpu-watchdog
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[2987:2987:1019/192955:ERROR:sandbox_linux.cc(305)] InitializeSandbox() called with multiple threads in process gpu-process
[2948:2948:1019/192955:ERROR:desktop_window_tree_host_x11.cc(1547)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState)
[2948:3012:1019/192958:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates

---

### Post by mc4man on 2014-10-19
(- well it removed the last 2 errors but 3 remain
Can't say I can reproduce in an Ubuntu install, you need someone with Lubuntu (or maybe Xubuntu) to ck.

Otherwise 2 things - 
If you try in a guest or create a new user session does this still happen?
If you disable the power management option in vlc does this happen? (screen

Edit; when opening chrome/chromium without any player activity first what does terminal show?

---

### Post by GYcode on 2014-10-20
Both things happening.

Withiut player activity, get:
> gytisc@gytisc-desktop:~$ google-chrome
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[12187:12187:1020/172633:ERROR:sandbox_linux.cc(305)] InitializeSandbox() called with multiple threads in process gpu-process
[12145:12145:1020/172633:ERROR:desktop_window_tree_host_x11.cc(1547)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState)

---

### Post by mc4man on 2014-10-20
How about if you start either with a --disable-gpu option?

---

### Post by GYcode on 2014-10-26
With this option chrome starts, but with disabling gpu, all video runs on cpu ?

---

### Post by mc4man on 2014-10-26
> **GYcode said:**
> With this option chrome starts, but with disabling gpu, all video runs on cpu ?

You'd need someone who uses chrome/chromium to comment but the perspective here is that google anything has crap support for hw acceleration for video **decoding**. 
(- hardware assisted rendering works but of marginal value so no real loss

---

### Post by GYcode on 2014-10-26
Thanks for help, I think it's something with my gpu drivers, my radeon hd 4670 have no official amd drivers.

---

