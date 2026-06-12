---
title: "System thinks Alt+Space is bound after reboot"
date: 2015-06-12
forum: General Help
---

### Post by Justin_Large on 2015-06-12
On my 14.04 System76 laptop, I like to reserve Alt+Space for Launchy instead of the default.  This works fine until I reboot.  Once I reboot and bring up Launchy, it complains that Alt+Space is already being used.  To fix this, I find the shortcut for "Key to show the HUD", which says it's disabled.  I map it to Alt+Space and disable it.  After that, I bring up Launchy, and everything's fine.  Is there anything I can do to avoid this workaround?

---

### Post by mc4man on 2015-06-12
The default key to show the Hud is to tap alt, nothing about space there..
alt+space is the default for "Activate the window menu", at least  here in 14.04 . System Settings > Keyboard > Shortcuts > Windows 
(- does sys76 change that??

---

### Post by CantankRus on 2015-06-12
Disable in keyboard shortcuts.
Click on the "Alt+Space" entry then hit backspace.

---

### Post by Justin_Large on 2015-06-12
I just did the same thing for "Activate the window menu".  Even if it shows as disabled, I still have to bind it to Alt+Space and then disable it again after a reboot.  I don't think it matters which item I do this to.  I just need to bind *something *to Alt+Space and then disable it.  It's like there's something that incorrectly thinks Alt+Space is bound.  This isn't a major deal since I just apply my workaround after every reboot, but it does seem like there's some kind of bug somewhere.  I wonder if there's some sort of startup bash script hack I could apply so at least I'm not manually doing stuff.

---

### Post by mc4man on 2015-06-13
*If* on reboots alt+space is being reset to the current default then you could try changing the default for activate window menus to nothing. That's done  fairly easily. you'd need to open /usr/share/glib-2.0/schemas/org.gnome.desktop.wm.keybindings.gschema.xml in a root text editor. 2 examples - 
```
sudo nano  /usr/share/glib-2.0/schemas/org.gnome.desktop.wm.keybindings.gschema.xml
```
In the terminal look for <key type="as" name="activate-window-menu"> 

Or in this case a root gedit is easier - 
```
sudo -H gedit  /usr/share/glib-2.0/schemas/org.gnome.desktop.wm.keybindings.gschema.xml
```
Search activate-window-menu & it will go right to the key (line 141 here

The current line is - 
```
<default><![CDATA[['<Alt>space']]]></default>
```
I'm not clear on the CDATA stuff so to set the default to nothing edit to this, eg.  removing ** '<Alt>space'** (scr 1
```
<default><![CDATA[[]]]></default>
```

Then recompile the schema, **the command must run without any error or any comment**, if not then you **must fix** or you can lose the entire gschema

```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```
After that open dconf-editor > org > gnome > desktop > wm > keybinding & on the top one highlight, then click on the Set to Default button at bottom (scr.2

Log out to reset anything in mem.

---

### Post by Justin_Large on 2015-06-13
I tried a couple of things.  First was your suggestion to set it to [COLOR=#000000][FONT=Ubuntu Mono]<![CDATA[[]]]>[/FONT][/COLOR] and second was to set it to [] which is how some of the other entries in the file had it.  However, I still had the same problem after reboot, even though dconf shows activate-window-menu having a value of [] with the "Set to Default" button greyed out.  Simply hitting Alt+Space doesn't do anything.

---

### Post by Justin_Large on 2015-06-13
I just went into Sublime Text and mapped "create new file" to Alt+Space.  This works even after a reboot, so part of me wants to blame Launchy, but another part of me is saying that Launchy must be seeing *something *in the system to say it's already mapped.  Or, maybe it's hardwired to assume Alt+Space is taken until it sees it actually being disabled.  Anyway, I do have a workaround, so I don't want to spend too much more time on this unless you can think of something easy to try, or you know of some sort of bash hack where I can run a "disable Alt+Space" command at startup time.

---

### Post by mc4man on 2015-06-14
As I had mentioned changing the default to none would only possibly have mattered if upon a reboot the default for alt+space had returned (as in opening the window menu
Not clear on whether that was the case from your post.
Probably this is a launchy issue.

You could try setting the default to 'disabled', if that doesn't have any effect then it's how launchy currently works. 
(- don't have installed

So you re-edit the schema, then recompile
```
<default><![CDATA[['disabled']]]></default>
```

---

