---
title: "Ctrl key always pressed"
date: 2008-07-03
forum: General Help
---

### Post by letired on 2008-07-03
It seems that there is a shortcut to make it so that my keyboard recognizes the ctrl key as pressed. This often happens when I'm editing large quantities of text, and I think I'm pressing ctrl + some arrow. Basically, after this, when I press f I get search, when I press s I get a save-dialog etc. The only way to get out of this, that I know of, is ctrl+alt+backspace-ing my way out of the mess, sometimes losing text entered in web browsers etc.
What is this, and how do I avoid it?

---

### Post by unutbu on 2008-07-03
Most likely, there is a dot config file in your home directory that is messed up. If you press Ctrl-Alt-F2 to get to a text terminal, does the Ctrl-problem persist even at the text terminal? If not, try the suggestion here:
[http://ubuntuforums.org/showpost.php?p=5312430&postcount=21](http://ubuntuforums.org/showpost.php?p=5312430&postcount=21)

It was written for someone with a different keyboard problem, but the solution may be similar.

---

### Post by letired on 2008-07-04
> **unutbu said:**
> Most likely, there is a dot config file in your home directory that is messed up. If you press Ctrl-Alt-F2 to get to a text terminal, does the Ctrl-problem persist even at the text terminal? If not, try the suggestion here:
[http://ubuntuforums.org/showpost.php?p=5312430&postcount=21](http://ubuntuforums.org/showpost.php?p=5312430&postcount=21)

It was written for someone with a different keyboard problem, but the solution may be similar.

So basically this is not a feature but a.. non-feature, I see. The problem is that in order to test whether it still happens in text-mode, I need to understand how it's turned on in the first place. Otherwise, I'll have to wait until it happens again, which could be days or weeks from now. Is there  a some kind of list/config file that spills which keyboard bindings/shortcuts there are on my installation?

---

### Post by unutbu on 2008-07-04
Maybe I should have asked this first: what program are you editing text with? (gedit?) and does the Ctrl-problem happen only within that text editor, or does it extend to other programs as well (such as a terminal and your web browser)?

To answer your question in the previous post: You can try the suggestion 
[http://ubuntuforums.org/showpost.php?p=5312430&postcount=21](http://ubuntuforums.org/showpost.php?p=5312430&postcount=21)
without having to wait for the Ctrl-problem to manifest itself. If my initial guess was right, you simply won't experience the Ctrl-problem again. You will have to reset all your GNOME configuration settings, but that usually does not take that much time.

The command
```
xmodmap -pke > xmodmap.conf
```
will dump your current keyboard mapping to the file xmodmap.conf.

This will not show you your keyboard shortcuts, however. Your GNOME keyboard shortcuts are stored in XML files in one of the four directories: ~/.config, ~/.gconf, ~/.gnome, ~/.gnome2. Someone who understands GNOME better than I do may be able to tell you more specifically where they are located.

---

### Post by drs305 on 2008-07-04
> **unutbu said:**
> 
This will not show you your keyboard shortcuts, however. Your GNOME keyboard shortcuts are stored in XML files in one of the four directories: ~/.config, ~/.gconf, ~/.gnome, ~/.gnome2. Someone who understands GNOME better than I do may be able to tell you more specifically where they are located.

Keyboard shortcuts made via System, Prefs, Keyboard Shortcuts or via gconf-editor are normally stored in /home/*username*/.gconf/apps/metacity/global_keybindings folder.

---

### Post by unutbu on 2008-07-04
Here is a way you can learn (or at least narrow down the possibilities for) where GNOME saves keyboard shortcuts:

1. Close all applications like Firefox. 
2. Wait for a minute. Literally.
3. Go to System>Preferences>Keyboard Shortcuts, and change something. (Remember what it used to be so you can change it back)
4. Open a terminal and type

```
find . -mmin -1
```
The output will show all the files in your current directory (i.e. any thing in your home account) that has changed in the last minute. Among the files changed should be whatever file GNOME uses for keyboard shortcuts.

Obviously you can use this same method to discover other files GNOME uses for configuring various things.

Since I don't use metacity, I've discovered my Desktop keyboard shortcuts are saved in ~/.gconf/apps/gnome_settings_daemon/keybindings/%gconf.xml

---

### Post by letired on 2008-07-04
> **unutbu said:**
> Maybe I should have asked this first: what program are you editing text with? (gedit?) and does the Ctrl-problem happen only within that text editor, or does it extend to other programs as well (such as a terminal and your web browser)?

I can recall it affecting web browsers, text editors (both gedit and oo.org) as well as Nautilus - I haven't tried using a terminal at these instances but as far as I know the ctrl-key is "pressed" globally.
Anyway, I'm trying out the possible fixes you posted, and I'll report back ASAP. Thanks.

---

### Post by drs305 on 2008-07-04
If you experience the stuck CTRL key, these commands may help troubleshoot which key is generating the signal and you may be able to disable the key:

```

xmodmap -e "keycode 37 = NoSymbol"    # Disable Left Control Key
xmodmap -e "keycode 109 = NoSymbol"    # Disable Right Control Key
xmodmap -e "keycode 37 = Control_L"    # Restore Left Control Key
xmodmap -e "keycode 109 = Control_R"    # Restore Right Control Key

```

---

### Post by unutbu on 2008-07-04
```
xmodmap -e "keycode 109 = Control_R"    # Restore Right Control Key
```

---

### Post by drs305 on 2008-07-04
> **unutbu said:**
> ```
xmodmap -e "keycode 109 = Control_R"    # Restore Right Control Key
```

Thanks. Sometimes I hate cut & paste :confused:

---

### Post by letired on 2008-08-07
Alright, it just happened again, so I ctrl+alt+f1-ed and tried xmodmap etc, but I got some error message. I haven't been able to pinpoint the source of the problem. Anyway, when I returned to X, the issue was gone. I guess that's convenient enough to work as a workaround.

---

### Post by Rounin on 2008-12-28
This problem has prevented me from using Linux for a long time. I read somewhere that it could be related to some error messages related to keycodes that kept appearing in dmesg.

> [4335062.871000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335063.546000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4335063.546000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335063.607000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4335063.607000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335073.996000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4335073.996000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335074.114000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4335074.114000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

These error messages can be stopped by disabling a service called "hotkeys-setup". So I'm hoping going to System->Administration->Services and disabling hotkeys-setup will solve the problem once and for all. It's too early to say as of yet, though.
_____________
After 16 hours without hotkeys-setup, it's still working. It's looking good.

---

### Post by Rounin on 2008-12-30
Ah no, it was too good to be true after all. The bug's back again, it just took a while to manifest itself again.

---

### Post by karlwilbur on 2009-08-05
I have been running into this issue for over a year, across multiple Ubuntu releases (7.10, 8.04, 8.10 and now is seems 9.04 as well) and across different hardware (2 laptops and 2 desktops).

I am not certain of exactly what triggers it. I find that it occurs while editing in Komodo Edit (a LOT of Ctrl+C/Ctrl+V where I am holding the Ctrl key...perhaps I accidentally hit another key? )

When this "Ctrl lock" kicks in, I cannot access the "Applications", "Places" or "System" menus, nor can I type in Terminal, since it seems that the Ctrl key is locked down. However switching to another virtual terminal seems to work just fine (Ctrl+Alt+[1-6]). 

I have not tried exiting X/Gnome to a tty and running "[FONT="Courier New"]setxkbmap[/FONT]" while this "Ctrl Lock" is in effect, but I have tried executing [FONT="Courier New"]setxkbmap[/FONT] from a tty and I get the 'Cannot open "default display"' error message. I am not certain if this would actually fix my problem despite the error message, but should I find that it does work, I'll post back here to let the world know.

---

### Post by karlwilbur on 2009-08-10
Just had it happen again. Trying ```
setxkbmap
``` from a tty did not work. Just got the "default display" error. Tried: 
```
setxkbmap -d 0:0
```
```
setxkbmap -d 0
```
```
setxkbmap -d :0
```

none worked. Only Crtl+Alt+Bksp...which sucked. :-(

---

### Post by Melpomene on 2010-06-23
I have the same problem with my ALT -key. 

I found that the problem stopped when I set my graphic-settings to "None", but it returns as soon as I change that setting to something else.

---

### Post by Melpomene on 2010-10-11
Has anyone found a solution to this to enable me to use my graphic-settings ? Upgrading to 10.10 apparently did not work, neither did switching to the graphic driver NVIDIA v 173 (instead of the current version).

---

### Post by Melpomene on 2010-12-12
Just stumbled over this thread again. Managed to solve this problem some time ago. 

I opened the window System->Settings->Window and there I changed the setting "use this button to drag" from the Alt-key to the other one and saved. Then I simple changed it back to the Alt-key, and voila, everything was back to normal. 

Hope this helps.

---

### Post by dphirschler on 2011-01-26
Sure if this will help, but I solved my own CTRL key stuck issue just now.  My system is an Aopen Minipc.  The keyboard and mouse must be USB.  So I have a Microsoft wireless mouse plugged into USB, and a Dell 105 keyboard plugged into a PS1/USB adapter.

I checked that maybe my keyboard was defective by plugging in a USB keyboard.  No change.  I removed the adapter.  No change.  I booted up with a live CD and the CTRL key was still stuck.  

Then I suspected it might be some weird BIOS setting that somehow got changed.  I could not boot up into BIOS settings because the DEL key could not be read.  

I unplugged the wireless mouse adapter and I was able to get in.  Then a lightbulb went up!  The wireless mouse is part of a keyboard/mouse combo.  I quit using the keyboard a while back and it was sitting on a shelf nearby.  And recently, I had stacked something on top of it (in the process, pressing some keys down).  I grabbed it and hit some keys and bingo!  Typing appeared in my text editor.  All I had to do was either remove the batteries from the wireless keyboard, just use it, or use another mouse.  Either way, problem solved!

Hope this helps somebody else out there.


Darryl

---

