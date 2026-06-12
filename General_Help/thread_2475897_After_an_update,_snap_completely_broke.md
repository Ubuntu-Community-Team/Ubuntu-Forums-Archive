---
title: "After an update, snap completely broke"
date: 2022-06-11
forum: General Help
---

### Post by wontoon on 2022-06-11
Hello, I recently installed an update that was prompted through Software in Ubuntu 22.04 LTS! After a restart, I suddenly could not run any snap package.

snap run firefox gave me this output:

[FONT=courier new]/snap/firefox/1443/snap/command-chain/desktop-launch: line 52: /home/wontoon/.config/user-dirs.dirs: Permission denied[/FONT]
[FONT=courier new]sed: can't read /home/wontoon/.config/user-dirs.dirs: Permission denied[/FONT]
[FONT=courier new]/snap/firefox/1443/snap/command-chain/desktop-launch: line 261: /home/wontoon/.config/user-dirs.dirs: Permission denied[/FONT]
[FONT=courier new]cp: cannot open '/home/wontoon/.config/user-dirs.locale' for reading: Permission denied[/FONT]
[FONT=courier new]/snap/firefox/1443/snap/command-chain/desktop-launch: line 266: /home/wontoon/.config/user-dirs.locale: Permission denied[/FONT]
[FONT=courier new]Error: cannot open display: :0[/FONT]


Discord gave me this error:

[FONT=courier new]/snap/discord/137/snap/command-chain/desktop-launch: line 52: /home/wontoon/.config/user-dirs.dirs: Permission denied[/FONT]
[FONT=courier new]sed: can't read /home/wontoon/.config/user-dirs.dirs: Permission denied[/FONT]
[FONT=courier new]/snap/discord/137/snap/command-chain/desktop-launch: line 261: /home/wontoon/.config/user-dirs.dirs: Permission denied[/FONT]
[FONT=courier new]cp: cannot open '/home/wontoon/.config/user-dirs.locale' for reading: Permission denied[/FONT]
[FONT=courier new]/snap/discord/137/snap/command-chain/desktop-launch: line 266: /home/wontoon/.config/user-dirs.locale: Permission denied[/FONT]
[FONT=courier new]Discord 0.0.18[/FONT]
[FONT=courier new]Quitting secondary instance.[/FONT]
[FONT=courier new]Failed to generate minidump.Segmentation fault (core dumped)[/FONT]

From what I can tell, permissions weren't set properly or... something. Is there anything I can actually do to fix this short of a full reinstall? Maybe I could try a reinstall of snap itself (that is my first guess)?

**Edit: Nevermind, uninstalling and reinstalling snapd actually fixed the issue!**

---

### Post by TheFu on 2022-06-13
> **wontoon said:**
>  
**Edit: Nevermind, uninstalling and reinstalling snapd actually fixed the issue!**

Please use the thread tools button to mark this thread as SOLVED to help people seeking and helping.  Otherwise, people will waste time when the issue is solved.

---

### Post by kal9mba on 2022-06-24
For me removing and installing snapd and firefox in it did not resolve the issue. It is still the same "Permission denied" errors like above.
Do i need to purge it instead of removing? I would like to save my browser settings and all stuff. So purging might cause some problems.

---

### Post by web-user on 2022-06-24
[FONT=courier new]cannot open display: :0 looks like something that has to do with Xorg display, $XDG_RUNTIME_DIR and permissions. I think they broke for some reason during update[/FONT]

---

### Post by kal9mba on 2022-06-24
> **web-user said:**
> [FONT=courier new] looks like something that has to do with Xorg display[/FONT]

Issue happens also on Wayland

---

### Post by TheFu on 2022-06-24
kal9mba, these forums are best when 1 thread per person happens.  "Me Too" threads aren't really used, because our systems and sofware are all different.  

In short, start your own thread. Provide any output you see by the prior poster that was offered or requested and use a clear, concise thread title.
So, "22.04 Gnome, patch updates broke all snaps"   Or "20.04 KDE, patch updates broke 1 snap, xyz" are both more helpful titles.

They be certain to say what you've tried already and include links for other forum posts you've already read and tried.

That's how to get the most help.

---

