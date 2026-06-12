---
title: "Why did my OS suddenly get messed up, and can I fix it without reinstalling?"
date: 2013-04-23
forum: General Help
---

### Post by 151rby on 2013-04-23
I have Ubuntu 11.04, and today I decided to try to install a Retrolink USB N64 controller on it. In addition to the gamepad itself, there was a little disk to install the driver, which as far as I can tell, installed just fine via Wine. As for getting the system to recognize the gamepad, I just followed the instructions here: [http://linuxgamingtoday.wordpress.com/2008/01/24/install-and-use-usb-based-gamepads-in-ubuntu/](http://linuxgamingtoday.wordpress.com/2008/01/24/install-and-use-usb-based-gamepads-in-ubuntu/)
When I did:
[COLOR=#494949][FONT=Verdana]sudo apt-get install joystick
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]it seemed to go fine, but there were a few 404 Not Founds. When I did:
[/FONT][/COLOR][COLOR=#494949][FONT=Verdana]sudo apt-get install jscalibrator
[/FONT][/COLOR][COLOR=#000000]it failed and said the package was not found. But I recklessly and blindly decided to go ahead anyway with:
[/COLOR][COLOR=#494949][FONT=Verdana]sudo chmod 666 /dev/input/js0
[/FONT][/COLOR][COLOR=#000000]at which point my music promptly stopped, all my open programs except terminal seemed to disappear, the task bar on the left side of the screen became solid grey with no icons, and all the icons on my desktop changed from my chosen high-contrast style to the default(?) style. I didn't try opening any of them, but I probably should have[/COLOR][COLOR=#000000]. My solid-color desktop background was still there, and the mouse touchpad still worked fine, though I didn't try right-clicking, and I actually can't recall whether or not my chosen cursor had changed to the default cursor. [/COLOR][COLOR=#000000]The stuff in the upper-right corner of the desktop, like the power icon and the clock, was gone, but the menu options at the top of the desktop were still there. I didn't really try to do anything with them though. I exited terminal (which still seemed to be working fine), turned off my computer with the power button, and turned it back on.

Now when I turn my computer on, it doesn't get past the screen where it says Ubuntu and five little dots change from white to red-orange and back again. It gets to the part where all the dots turn red-orange (as if the login screen is just about to show up), but no further. I tried booting in recovery mode and repairing broken packages. No change. I tried booting into a file system check. The check seemed to be carried out properly, but there was no change. I tried pressing Ctrl-Alt-F1 at the Ubuntu screen with the dots, and it takes me to a command line screen to login, but when I try to login from there it says "Unable to cd to '/home/[my username]'". Same thing happens when I boot in recovery mode and then continue with normal boot.

I know I can just reinstall Ubuntu and then (probably) recover my data like I did the last time my Ubuntu OS got mutilated. But, well, I don't want to. If anyone has any ideas as to how I can fix this without reinstalling, I'd love to hear them.

My biggest question right now is, WHY did this happen!? Did I cause it through my ignorant use of the sudo command in terminal? Could the gamepad or the driver have caused it? (probably not..) Is this a mysterious occurrence, and if so, which log files should I look to for clues?

One last thing, and I don't know if this is of any significance at all, but this computer has a bit of a troubled past. Almost one year ago, something went wrong during an upgrade, and the OS became unusable and I had to re-install. The old broken OS still resides on my computer as I've been too lazy to clean it up. There is also a perfectly fine (as far as I know) copy of Precise Pangolin on my computer, which I've never really used. I'm kind of attached to 11.04.

Many thanks to all who give helpful input![/COLOR]

---

### Post by GameX2 on 2013-04-23
Sorry to say that, but Ubuntu 11.04 has reached end-of-life since october.  That would explain the 404 errors you've got.  I would recommend using Precise, it's very good and stable.  If you don't like Unity, you can still install the classic GNOME2 desktop by doing " sudo apt-get install gnome-session-fallback ".

---

### Post by 151rby on 2013-04-24
My main reason for having stayed with 11.04 is the ease of customizing the color scheme. I don't really know how to do that in 12.04.

---

### Post by Sef on 2013-04-24
> [COLOR=#000000]My main reason for having stayed with 11.04 is the ease of customizing the color scheme. I don't really know how to do that in 12.04.[/COLOR]

So ask that question in the forums before you upgrade to 12.04.

---

### Post by ibjsb4 on 2013-04-24
Here's a "Classic" head start :)

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

