---
title: "Difficulties"
date: 2022-12-27
forum: General Help
---

### Post by normanicus on 2022-12-27
I have installed Ubuntu on and old Dell Inspiron 5000 series with AMD A6 processor. It works but there are many annoyances.

1. I have no way of typing a pipe symbol. I have read endless posts and articles which tell me where the pipe symbol should be but I get # and, with shift, ~. Eventually I decided to reassign keys but, coming from a Mac, I am astonished that this seems to require either permanently changing a system file or writing a script.

2. Cut and Paste don't seem to work consistently. In the browser I can use Cmd-C, V, X etc but, in the terminal, I need to add shift. Is there logic to this?

3. I installed the Brave browser as I get much less clutter on screen when using it. However, virtually none of the keyboard shortcuts I am used to, work.

4. Where have all the application menus gone? How do I get them back?

There are other issues but I don't want this to turn into a rant. I suppose anyone coming from a Mac misses 'Hide ..' and 'Hide Others' just like coming from Windows and missing a right click to create a file/document of specific types in the folder one is in.

On the plus side, it is pretty snappy considering the age and lack of power of the hardware.

---

### Post by QIII on 2022-12-28
> 1. I have no way of typing a pipe symbol. I have read endless posts and articles which tell me where the pipe symbol should be but I get # and, with shift, ~. Eventually I decided to reassign keys but, coming from a Mac, I am astonished that this seems to require either permanently changing a system file or writing a script.

Does your keyboard not have the pipe?  With a standard keyboard there should be no need to change anything or write a script.

> 2. Cut and Paste don't seem to work consistently. In the browser I can use Cmd-C, V, X etc but, in the terminal, I need to add shift. Is there logic to this?

That is the default behavior in the terminal.  This is something that comes from *nix's Unix-like lineage.

> 3. I installed the Brave browser as I get much less clutter on screen when using it. However, virtually none of the keyboard shortcuts I am used to, work.

I don't use Brave, so we'll have to wait for someone who does.

> 4. Where have all the application menus gone? How do I get them back?

This is a "feature" of the GNOME3 desktop environment.  That Desktop Environment (DE) is just one of very many -- and I don't happen to care for it much.  Other people like it very much.  For some familiarization, [this]("https://help.gnome.org/users/gnome-help/stable/shell-introduction.html.en") might help.

Your transition will be made easier if you keep one thing in mind:  Linux != Apple != Windows.  Linux distributions (there are more of them than  you can shake a stick at) are under no obligation to behave like other operating systems.

---

### Post by Impavidus on 2022-12-28
> **normanicus said:**
> 1. I have no way of typing a pipe symbol.What's your keyboard layout? On mine (US-keyboard), the pipe is typed with shift+the key above enter. If your keyboard isn't correctly configured, you can reconfigure it with```
sudo dpkg-reconfigure keyboard-configuration
```
> 2. Cut and Paste don't seem to work consistently. In the browser I can use Cmd-C, V, X etc but, in the terminal, I need to add shift. Is there logic to this?ctrl-x, ctrl-c and ctrl-v were already assigned to different functions in the terminal before cut and paste were invented and kept their old functions. In particular ctrl-c is commonly used to kill applications by sending the terminate signal.
> 3. I installed the Brave browser as I get much less clutter on screen when using it. However, virtually none of the keyboard shortcuts I am used to, work.Apart from the few keyboard shortcuts that are handled by the window manager or the kernel, shortcuts are handled by each application separately. There's no guarantee that the same shortcuts have a similar effect in multiple applications, although there are a few de facto standards.
> ... missing a right click to create a file/document of specific types in the folder one is in.This function actually exists, although I never use it. You need some templates in the ~/Templates directory, then you can right-click and create a new file of a specific type. This will copy the template of the right type to the directory where you clicked. Depending of your locale settings, the ~/Templates directory may have a different name. Run```
grep TEMPLATES ~/.config/user-dirs.dirs
```to be sure about the name.

---

### Post by pantazi on 2022-12-28
Re Brave browser, there are a number of web pages devoted to this, just do a search,
e.g. [https://shortcutworld.com/Brave-Browser/win/Brave-Browser_Shortcuts](https://shortcutworld.com/Brave-Browser/win/Brave-Browser_Shortcuts)

---

### Post by ian-weisser on 2022-12-28
> **normanicus said:**
> It works but there are many annoyances.

Keep in mind that we are not the Complaint Department.
Nor are we the Bug Tracker.

Please file complaints appropriately.
Please report bugs properly.

The software on your Ubuntu system is Open Source. If you wish to dig into the code and fix some of the issues that you find annoying, your contributions will be welcome.

---

