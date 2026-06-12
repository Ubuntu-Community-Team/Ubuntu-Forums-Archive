---
title: "[SOLVED] Swap CapsLock and Ctrl - keyboard caps lock light doesn't swap"
date: 2008-03-26
forum: General Help
---

### Post by MountainX on 2008-03-26
Does your caps lock light on your keyboard continue to toggle (on pressing former caps lock, now ctrl key) even after swapping the caps and ctrl keys?

Mine does under Hardy. I don't remember it doing that before.

---

### Post by -grubby on 2008-03-26
I would think this is a function of your keyboard. It probably depends what keyboard you're using

---

### Post by Whiffle on 2008-03-26
I have my capslock mapped to the Super/Win key, and it doesn't toggle the light.  Thats under Feisty, Arch, and maybe under gutsy, I don't remember.

---

### Post by MountainX on 2008-03-27
I just checked it on my laptop where my capslock is mapped to control and it doesn't trigger the capslock light. Strange that it is happening on my desktop. (Both use IBM keyboards, but different models of course. And I'm pretty sure this didn't happen on my desktop prior to me reinstalling today.)

---

### Post by MountainX on 2008-03-27
I tried another keyboard on my desktop. The capslock light isn't working correctly there either. Maybe this is a Hardy bug. I'll move this thread over to the development forum.

---

### Post by MountainX on 2008-03-27
tehkain gave this info:
Here is the bug report: [https://bugs.launchpad.net/ubuntu/+s...er/+bug/173350](https://bugs.launchpad.net/ubuntu/+s...er/+bug/173350)

There is a workaround there also. You are correct that this is a new issue.

---

### Post by MountainX on 2008-04-03
I finally found a solution by reading the man for xmodmap.
See [http://ubuntuforums.org/showthread.php?t=738490](http://ubuntuforums.org/showthread.php?t=738490)

Here is the info:

I'm using Hardy beta.

Do NOT use gnome's keyboard control (Ubuntu System > Preferences > Keyboard > Layout Options).
Instead follow the example in man xmodmap as explained below.

NOTE: before doing this, undo any changes in Keyboard layout options. Put the options back to defaults in gnome's keyboard control.

And, if you have done anything advanced to try to work around these issues, remove those modifications too. For example, the following is NOT needed so if you are using it, remove it (may require a restart):
xmodmap -e "clear lock" -e "add lock = Caps_Lock"

Put the following in a text file.

!
! Swap Caps_Lock and Control_L
!
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L

save the above as /etc/SwapCapsCtrl.kmap

then, from a terminal, run:
xmodmap /etc/SwapCapsCtrl.kmap


To make the change permanent, do this:
edit /etc/rc.local
add the following before the last line that says 'exit 0'
sudo xmodmap /etc/SwapCapsCtrl.kmap

Now in tsclient (Terminal Services Client) version 0.150, in the Local Resources tab, make sure the correct keyboard layout is selected. For me, it is en-us. Previously I either left it blank (or I tried two letter codes like "us"). With the correct code, everything works. With the incorrect code, tsclient will often give an error when disconnecting -- and the keyboard layout options are not applied correctly, as mentioned previously.

Everything is now working exactly right for the first time.
__________________

---

### Post by MountainX on 2008-04-11
> **MountainX said:**
> 
Everything is now working exactly right for the first time.


I spoke too soon. I'm still using the above fix and it is still the best I have found so far, but my keyboard problems with rdesktop/terminal server client are not completely solved. See:
[http://ubuntuforums.org/showpost.php?p=4697285&postcount=7](http://ubuntuforums.org/showpost.php?p=4697285&postcount=7)

---

