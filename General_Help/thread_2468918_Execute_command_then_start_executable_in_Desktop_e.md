---
title: "Execute command then start executable in Desktop entry - possible?"
date: 2021-11-14
forum: General Help
---

### Post by Brent_Santin on 2021-11-14
Hi,

I used to be able to start the Amiga emulator WinUAE under in Wine from a desktop entry I created.
Recently there was an update to Lubuntu's MESA drivers which causes WinUAE to crash. I can work around this by temporarily using old MESA drivers. To do this from the terminal I enter the following commands:

export MESA_GL_VERSION_OVERRIDE=4.5
wine winuae64_4400.exe

I'd like to modify my desktop shortcut so that all this will happen when I click on the icon (rollback of driver and starting of emulator). I don't know if that's possible as I am not an advanced Linux user, but here's the way I tried to modify the shortcut to add the MESA driver rollback line (which did not work):

[Desktop Entry]
Name=WinUAE (gfx fix)
Comment=Windows Amiga emulator under WINE, with workaround to revert to old MESA drivers
Exec=export MESA_GL_VERSION_OVERRIDE=4.5
Exec=wine "/home/brent/.wine/drive_c/Program Files (x86)/WinUAE/winuae64_4400.exe" -norawhid
Icon=WinUAE
Terminal=false
Type=Application
Categories=Games;

Can anyone tell me if what I want to accomplish is possible, and if so how I can get the desktop shortcut to work?

Thanks.

---

### Post by dragonfly41 on 2021-11-14
There might be other standard ways (I don't use Wine) but since
you mention games I suggest a small tool Actiona which you will find in repo.

sudo apt install actiona

Then you can use the Actiona GUI to write an automation script.

Use the Command widget to write your commands as you have written above.

The "command" is simply "wine"
and the rest is placed in arguments.

Save the script and it can be launched using

actexec myscript.ascr

Then you can use a desktop app to run actexec myscript.ascr.

Alternatively, you could of course also just include
 the commands in a bash or python script if that is easier.

Actiona does have many other uses including simulation including game interaction (looking for events on the screen)

---

### Post by GhX6GZMB on 2021-11-14
No reason to install anything.
Write a little script containing:
```
[COLOR=#000000]sh export MESA_GL_VERSION_OVERRIDE=4.5[/COLOR]
[COLOR=#000000]sh wine winuae64_4400.exe[/COLOR]
```
Save it somewhere sensible (eg, $HOME/.local/share) and execute it from the .desktop file. Remember to make the script executable.

---

### Post by Holger_Gehrke on 2021-11-14
First, there's no need to export the variable you can just prefix it to the command, like this:
```
[COLOR=#000000]
[/COLOR][COLOR=#000000]MESA_GL_VERSION_OVERRIDE=4.5 [/COLOR]wine "/home/brent/.wine/drive_c/Program Files (x86)/WinUAE/winuae64_4400.exe" -norawhid

```
If you export the variable it will be passed to all programs you start from that shell and that might have unforeseen consequences. Put that command in a shell script, change your .desktop file to call the script instead of running wine directly and there you go. You might even get away with changing the Exec line in your .desktop to
```

Exec=bash -c '[COLOR=#000000]MESA_GL_VERSION_OVERRIDE=4.5 [/COLOR]wine "/home/brent/.wine/drive_c/Program Files (x86)/WinUAE/winuae64_4400.exe" -norawhid'

```
but I'm not certain that this'll work.

Second: is there a reason to use WinUAE ? There's a package named 'fs-uae' in universe in the repositories. From it's description: "Cross-platform Amiga emulator based on UAE/WinUAE".

Holger

---

### Post by Brent_Santin on 2021-11-14
Hi,

Thanks, I'll try the suggestions.
Yes, I use WinUAE under Wine sometimes instead of the native FS-UAE because WinUAE has some features FS-UAE does not have yet (MIDI support for music composing, for instance).

---

### Post by Brent_Santin on 2021-11-17
> **Holger_Gehrke said:**
> You might even get away with changing the Exec line in your .desktop to
```

Exec=bash -c '[COLOR=#000000]MESA_GL_VERSION_OVERRIDE=4.5 [/COLOR]wine "/home/brent/.wine/drive_c/Program Files (x86)/WinUAE/winuae64_4400.exe" -norawhid'
```
but I'm not certain that this'll work.


It worked! Thanks!

---

