---
title: "Weird keyboard problem under VMware"
date: 2006-12-03
forum: General Help
---

### Post by celsofaf on 2006-12-03
Hey. I installed VMware server, then Windows XP under it, no problem. Well... yes, problem! Weirdly, one key from my keyboard doesn't work on it. It is the kay with "?" and "/" on it. And yes, it works perfectly under Kubuntu.

Trying to see if it was a problem only of Windows, I created another virtual machine and booted Kubuntu LiveCD from it... everything on the keyboard worked properly (including accents and special characters), except that damn key! ](*,) ](*,) 

Any clues, hints?

---

### Post by LLRNR on 2006-12-04
Is your keyboard, by chance, a... special one ? I mean, is it a modern keyboard with lots of additional buttons for web browsing, music playing and so on ?

You could at least try to borrow from somebody an old, plain keyboard to see if the problem persists. If so, maybe you could try changing some settings in the "Keyboard" section from "Control Panel" (in Windows) - I don't know, maybe trying to add a new keyboard profile, delete the initial one, and then re-add it... who knows ?

Also, I noticed that some minor glitches can be resolved by turning off the virtual machine and then powering it on again (from the buttons within VMware Server).

LLRNR

---

### Post by 1331 on 2007-06-05
I have run into this same bug.  I am running VMware Server 1.0.3 build-44356 on Ubuntu 7.04 Feisty Fawn.  I have a standard Japanese keyboard, and all of my keys work correctly on the host system using XKBMODEL="jp106" and XKBLAYOUT="jp,jp" in both /etc/X11/xorg.conf and /etc/default/console-setup.  Despite setting the keyboard settings correctly in guest operating systems, one key does not work under VMware.  The key that is causing problems for me is the one immediately left of the right shift key, which is the backslash (\) and underscore (_) key on a Japanese keyboard.  I was able to reproduce the bug in the following guest operating systems: Gentoo Linux, Ubuntu 7.04 server, Debian 4, Windows XP Pro.

To try to debug the problem, I used the showkey command:
[http://www.die.net/doc/linux/man/man1/showkey.1.html]("http://www.die.net/doc/linux/man/man1/showkey.1.html")
When I run the program in a console of my host system, the key is read correctly, as follows:
$ showkey --scancodes
0x73 0xf3
When I run the program in a console of a guest system (Gentoo for my test), showkey works for all keys except for the problematic one.  There is no response at all for the problematic key, which seems to indicate that the guest OS is not receiving the scancodes for the keypress.

I cannot find any other references to this bug...  Is it reproducible on other (non-Ubuntu) host systems, in which case it is a VMware bug?

1331

---

### Post by 1331 on 2007-06-06
I was unable to find other references to this bug in English, but this morning I was able to find one in Japanese, and it has a solution!

[http://www.aconus.com/~oyaji/suse9.3/vmware_server.htm]("http://www.aconus.com/~oyaji/suse9.3/vmware_server.htm")

To solve the problem on a Japanese keyboard put the following two lines in your ~/.vmware/config file:

xkeymap.usekeycodeMapIfXFree86 = true
xkeymap.keycode.211 = 0x073

You need to use the keycode and scancode for the key that is causing problems, so the numbers may be different if you have a different kind of keyboard, of course.  You can determine the keycode (211 in my case) by running `xmodmap -pk` in a terminal and finding your problematic key in the list.  You can determine the scancode (0x073 in my case) by running `showkey --scancodes` in a console (Ctrl+Alt+F2, for example); the correct one is the first of the two numbers that are displayed when you press the key.  (Log out and press Ctrl+Alt+F7 to get back to your X session.)

Note that doing a search on "xkeymap.keycode." results in many relevant results which may prove useful in solving similar kinds of VMware configuration problems.

1331

---

