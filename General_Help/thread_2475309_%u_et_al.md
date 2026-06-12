---
title: "%u et al"
date: 2022-05-22
forum: General Help
---

### Post by peter228 on 2022-05-22
Could you please tell me where to look .... 

I was trying to set the command line for thunderbird in the Startup setting.  At present it says thunderbird %u and that works.

Then I thought what does %u mean and what are the other choices.  I cannot find out any list for this, google is no help.

Ultimately I would like to change this setting to tell thunderbird to open on my second monitor.

Any information or suggestions of how to search appreciated.

---

### Post by grahammechanical on 2022-05-22
I found this:

[https://superuser.com/questions/138433/what-is-the-u-command-in-all-my-programs-command](https://superuser.com/questions/138433/what-is-the-u-command-in-all-my-programs-command)

[https://askubuntu.com/questions/30210/what-does-u-mean-when-calling-a-command](https://askubuntu.com/questions/30210/what-does-u-mean-when-calling-a-command)

Regards

---

### Post by peter228 on 2022-05-22
nice find, thank you.  Remarkable that you are the only person to find anything, but I could also not :)

So, whilst I understand a bit more about %u, I can also see that this is not a method to consider for getting a program to open in a defined monitor ....

---

### Post by grahammechanical on 2022-05-22
It can be done if we use System Settings>Screen Display>Join Displays and then drag the application across to the other monitor. I do not know how to do this by adding an option to a command to load an application. I have only recently obtained a two monitor setup and I have yet to realize the potential of such a setup.

Regards

---

### Post by peter228 on 2022-05-23
Well, yes, I have startup applications launch without issue and then drag off to the other monitor.  But I would like this to be automatic.  I am sure it can be done but the question is how.  For example in the system settings you can choose which monitor your clock appears on so why not individual applications ...

---

### Post by Holger_Gehrke on 2022-05-23
Would that be in a .desktop file or in command-entry field that's going to end up as the Exec-line in a desktop file ? I think on Gnome startup applications are made by having .desktop files in $HOME/.config/autostart just like it's done on XFCE. If that's right, you can find the various %-escapes [at freedesktop.org in the description of the exec-key in a desktop file]("https://specifications.freedesktop.org/desktop-entry-spec/latest/ar01s07.html"). But those option are not going to help you with what you want to do.

For X11 multi-monitor setups work by having a big virtual desktop and the displays are viewports that 'look' at different parts of that desktop. So for example with two HD-display side by side the first would start at 0,0 and go to 1919, 1079 and the second would start at 1920,0 and go to 3839,1079. So to position a window on the second display you have to somehow make it open at the right coordinates. A lot of programs accept the option '--geometry {xpos}x{ypos}+{width}+{height}' (it's a standard option that gets passed by the program to the windowing system) so try 'thunderbird -geometry 1920x20+1920+1060' (adding a bit of y-offset and reducing the height to leave space for the bar at the top of the screen ...). If that doesn't work you can try writing a small wrapper script that starts thunderbird and then uses wmctrl to move the window where you want it to go.

I don't know about Wayland though. If you're using that, somebody else will have to come up with an answer.

Holger

P.S.: Wouldn't that question have fit better in the 'General Help' Section of the forum ?

---

### Post by peter228 on 2022-05-24
Hi Holger,

thank you for your link and information, very helpful to me.

You ask "P.S.: Wouldn't that question have fit better in the 'General Help' Section of the forum ?"  .... erm actually there do not appear to be any guidelines of what to post where but since this is not 'General Help' then I think posting here is the right place.   Everybody sees %u but it appears very few know what it means.  Similarly having programs open by default on separate displays appears to be not rocket science but certainly a challenge of the future.  This is not addressed by Canonical and the management of Clock location and attributed for example is still clumsy so more demanding users who wish to treat displays seperately have to ask on the forums or wait for the powers to be to join in the real world.

---

### Post by Holger_Gehrke on 2022-05-24
Just played around with Thunderbird a bit (I normally use evolution for mail). On XUbuntu 22.04 it opens where it was last closed. So if I move it to my second display and close it, it will open there the next time **unless** it was maximized at the time of closing. If it was maximized it will open maximized on the main display (which means whatever display I set to be the main display in the display settings for XFCE).

Doing
```

thunderbird & sleep 10; wmctrl -r 'thunderbird' -b remove,maximized_horz ,maximized_vert -e 0,1920,0,1366,768

```
starts thunderbird, waits 10 seconds until it actually has a window open (yes, I'm running a potato ...) then un-maximizes it horizontally and vertically and moves the window to the second display and changes the size of the window to 1366x768 (the size of my laptop's display).

Oh, and there are Posting Guidelines ... but they are a bit hard to find. There's a sticky post from 2013 at the top of the 'Forum Feedback & Help' forum (and why do I get a flashback to the beginning of the 'Hitchhiker's Guide to the Galaxy' while writing this ?). But the fact that there's a line at the top of this page saying 'Hello $user_name, this sub-forum is for chat, not support – hence the  name. If you need technical help, please post in an appropriate support  sub-forum.' made me question whether this post actually was in the right place ...

Holger

---

### Post by DuckHook on 2022-05-24
> **Holger_Gehrke said:**
> P.S.: Wouldn't that question have fit better in the 'General Help' Section of the forum ?
*Thread moved to **General Help** as the more appropriate forum.*

Your wish is my command. :D

---

### Post by peter228 on 2022-05-27
I have tried with your suggested settings as modified for my system but they do not seem to work so could I please explain what I did and what I do not understand in order to perhaps get it working ....

your command - 
thunderbird & sleep 10; wmctrl -r 'thunderbird' -b remove,maximized_horz ,maximized_vert -e 0,1920,0,1366,768

So I changed to ..

thunderbird wmctrl -r 'thunderbird' -b remove,maximized_horz ,maximized_vert -e 0,1920,0,1920,1080

Both my displays are 1920 x 1080

The problem is that nothing happens in that thunderbird does not launch at all on reboot (or power on).  
I can see that this command launches thunderbird and then passes control to the windows manager.  Then it is removed from one position and passed to another.  I did not understand why you did not define both x and y on the first monitor (only that it was 1920) At least that is how I read it.

---

### Post by Holger_Gehrke on 2022-05-27
The command I gave doesn't automatically run on boot. You need to put it in a script, create a desktop file for that script and put the desktop file in ~/.config/autostart/. You can't put the command directly in the desktop file because it's actually three commands in one line and you can't do that in the Exec-line of a desktop file since that line isn't parsed by the shell.

To explain the command:
**'thunderbird &'** : starts Thunderbird and lets it run in the background (that's the meaning of the '&'; without that the script waits for Thunderbird to finish before executing the next command).
**'sleep n;'** : wait for a moment for Thunderbird to actually set up it's window; even on a fast machine you'll need a second or two for that, if you leave it out the next command might run before there is a window for Thunderbird and then the move and resize would fail.
**'wmctrl -r "thunderbird" -b remove,maximized_horz ,maximized_vert -e 0,1920,0,1366,768'** : find a window containing 'thunderbird' (case insensitive match) in it's title, remove the maximized status horizontally and vertically then set the windows gravity to 0 (meaning use the standard reference point of the window for positioning) and move the window to 1920 pixel horizontally and 0 vertically (should be the top left corner of the second display) and resize it to a width of 1366 pixels and a height of 768 pixels. As I mentioned before multiple display are seen as one continuous bitmap.

So: create a text file - lets call it '~/.local/bin/tbmov' with the content
```

#!/usr/bin/env bash
thunderbird &
sleep 2
wmctrl -r 'thunderbird' -b remove,maximized_horz ,maximized_vert -e 0,1920,0,1920,1080

```
make it executable with 'chmod u+x ~/.local/bin/tbmov'. Then create a desktop file ~/.config/autostart/tbmov.desktop with the content
```

[Desktop Entry]
Version=1.0
Type=Application
Name=Start, Move and Resize Thunderbird
Exec=~/.local/bin/tbmov

```

That should be it.

Holger

---

### Post by peter228 on 2022-05-30
This is a good challenge.

It does not work as intended.  As an autostart entry, nothing happens.   If launched from the command line it will open Thunderbird but only on the monitor where the command is executed.

The terminal displays the following - 

console.debug: "Found 0 public keys and 0 secret keys (0 protected, 0 unprotected)"
console.debug: "Successfully loaded optional OpenPGP library libgpgme.so.11 from system's standard library locations"
console.debug: "gpgme version: 1.16.0-unknown"
console.warn: services.settings: thunderbird/hijack-blocklists has signature disabled

Do I need to find gpgme or is this a red herring ...?

---

