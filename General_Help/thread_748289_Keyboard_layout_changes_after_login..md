---
title: "Keyboard layout changes after login."
date: 2008-04-07
forum: General Help
---

### Post by CShadowRun on 2008-04-07
I created my own varient of colemak for english keyboards, stuck it into xorg.conf

It works fine, but only for the login screen. After that i revert back to qwerty! :(

I can type this ```
setxkbmap -v colemak && xset r 66
``` every time i login, but this is obviously not very ideal.

Is there any way to tell ubuntu to stop changing my keyboard layout and use what i set in xorg?

---

### Post by drs305 on 2008-04-07
I cannot guarantee this will work but it's worth a try if you don't get a better answer. 
One of the things I am unsure of is whether the command you cite can be used as a "keyboard command". 
If it doesn't work, the gconf-editor settings may allow you to accomplish what you want in a slightly different manner.

Open gconf-editor:
```
gconf-editor
```
Go to /desktop/gnome/volume_manager/autokeyboard_command
Doubleclick and enter your command in the autokeyboard_command value.
Also enable the autokeyboard setting immediately above this command.

If it works please let us know.

If it doesn't, I posted a way to invoke a keyboard layout using shortcut keys.
That solution is here:
[http://ubuntuforums.org/showthread.php?t=739034#4](http://ubuntuforums.org/showthread.php?t=739034#4)

---

### Post by CShadowRun on 2008-04-07
Your method did not work. The autokeyboard_command folder did not exist.

However, jrib from the ubuntu IRC channel pointed me at [this page](http://forum.colemak.com/viewtopic.php?pid=692)

Which says:

[quote=giom]To be able to add the colemak to the layout in the keyboard preferences, you need to edit the file /usr/share/X11/xkb/rules/xorg.xml

In this file find the node   <layoutList>
and copy this snippet of xml inside:
        <layout>
            <configItem>
                <name>colemak</name>
                <shortDescription>Colemak</shortDescription>
                <description>Colemak see colemak.com</description>
            </configItem>
        </layout>

This will tell gnome that you have the colemak layout installed and you will be able to choose it in the list when you add a new layout to the keyboard preference tool.

If you can't find the path /usr/share/X11/xkb/rules/xorg.xml , you may want to try the following paths

/usr/lib/X11/xkb/rules/xorg.xml
/usr/lib/X11/xkb/rules/xfree86.xml
It depends on the version of xorg/xfree86 you have installed

Hope this helps anybody[/quote]

This did fix the problem. :D

---

### Post by drs305 on 2008-04-07
> **CShadowRun said:**
> Your method did not work. The autokeyboard_command folder did not exist.

Just to clarify, the autokeyboard_command is an option within the volume_manager folder. You would have to click on volume_manager to see the options in the right pane.

In any case, I'm happy you found a solution to your problem :)
(And the moderators would probably like you to mark this SOLVED via Thread Tools at the top of your original post)

---

