---
title: "Things that break when upgrading Ubuntu (emulators)"
date: 2022-10-23
forum: General Help
---

### Post by skoggo on 2022-10-23
Hello, I upgraded to Ubuntu 22.10 and everything works fine except for my SNES, and N64 emulators.

I was expecting something to break along the way, and the only issues since upgrading have been with the two different emulators.

1) ares (installed through the app store for SNES roms)
- The roms, and saves are intact.
- The controller still works.
- The only thing broken is fullscreen.
- Fullscreen is mapped to 'f' key, and instead maximizing the screen, it puts the minimized screen in the top left corner, and the rest of the screen is blank.

2) Project64 (installed with wine through playonlinux)
- The ROMs work fine.
- What is broken is the controller.
- jstest-gtk indicates that the controller works fine.
- point of failure appears to be the project64 emulator that does not detect the start, select, or right bumper as inputs.

I tried reinstalling everything, and still there are the same issues for both emulators.

If it worked before it will work again.

If not help on this issue I am interested to know what what sort of things have gone awry when upgrading Ubuntu, and what resolved the issue.

---

