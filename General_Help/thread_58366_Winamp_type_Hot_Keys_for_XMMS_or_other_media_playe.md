---
title: "Winamp type Hot Keys for XMMS or other media player?"
date: 2005-08-19
forum: General Help
---

### Post by celticmonkey on 2005-08-19
Does anyone know of a way to use Winamp type hotkeys to control XMMS (or another player) while using another application?

I do a lot of transcription using Winamp and it's really useful to be able to pause/play an interview while typing in a wordprocessor by hitting ctrl-alt-home. 

All of the hotkeys functions I've found for XMMS seem to require that it is the foreground application. That is, I would have to stop typing in my wordprocessor and alt-tab to XMMS before I could use my hotkeys. Or I'd have to click on an applet somewhere. 

I tried the transcription software in the ubuntu repository, but compared to winamp, it's really ackward and slow.

---

### Post by jasmuz on 2005-08-19
There is a little Gnome panel applet, called Gxmms, wich wil allow you to control your Xmms without having to switch programs.

---

### Post by celticmonkey on 2005-08-19
I've installed gxmms, but I can't see how to control XMMS without mouse clicks. That's not useful for transcription. With Winamp, I never had to take my fingers off the keyboard. I could pause and resume while typing in the wordprocessor.

---

### Post by SGC on 2005-08-19
[QUOTE=celticmonkey]Does anyone know of a way to use Winamp type hotkeys to control XMMS (or another player) while using another application?

I do a lot of transcription using Winamp and it's really useful to be able to pause/play an interview while typing in a wordprocessor by hitting ctrl-alt-home. 

All of the hotkeys functions I've found for XMMS seem to require that it is the foreground application. That is, I would have to stop typing in my wordprocessor and alt-tab to XMMS before I could use my hotkeys. Or I'd have to click on an applet somewhere. 

I tried the transcription software in the ubuntu repository, but compared to winamp, it's really ackward and slow.[/QUOTE]
 amaroK has a feature called "Global Shortcuts", which do exactly what you ask for. To configure it, from amaroK choose (Seetings -> Configure Global Shortcuts)

---

### Post by Emerzen on 2005-08-19
Hey, I do alot of transcription w/ XMMS myself and I understand the need for hotkeys.    With xmms in the foreground, pressing "x" will start the track and "c" will pause it.  If you right click on at the top of xmms, you'll get a drop down menu that has all the shortcuts listed w/ the commands.  Hope that was what you were asking about.  Good luck and enjoy.

---

### Post by celticmonkey on 2005-08-19
The global hot key feature of amaroK was *exactly* what I was looking for. It's perfect for transcription. Thanks!

---

### Post by 3david on 2005-10-21
I use "xbindkeys" to do this, just run:

   sudo apt-get install xbindkeys

and then put this code in ~/.xbindkeysrc.scm:

```

(xbindkey '(XF86AudioPlay) "xmms --play-pause")
(xbindkey '(Mod4 x) "xmms --play-pause")

(xbindkey '(XF86AudioPrev) "xmms --rew")
(xbindkey '(Mod4 Left) "xmms --rew")

(xbindkey '(XF86AudioNext) "xmms --fwd")
(xbindkey '(Mod4 Right) "xmms --fwd")

(xbindkey '(XF86AudioStop) "xmms --stop")

```

If you don't what's the string needed for your hotkey (Mod4 Left for example),
you can run "xbindkeys --key", and then press your key combination, and it will give you the text of this key combination.

(If anyone has an alternative way to do this, i'll be glad to hear, I've always searched for this ability in gnome)

I hope this helps :razz:

---

### Post by superr on 2005-10-21
It totally worked, thks

---

### Post by kracker on 2005-10-24
Background Details:

Keyboard: Logitech Internet Navigator (USB)
Running: Ubuntu Breazy 5.10 | GNOME
Date: 2005-10-20

Goal: To have my extra keyboard keys (media) controll xmms. Basicly the play/pause, stop, next(song), back(last song) player controls. 

Road: I did a bit of looking around and I'm sure that there is a simpler way to do this which is more correct, like properly configuring xorg/X keys and GNOME but ...

I gave this threads instructions for using xbindkeys a try, in less than 2 minutes I had the functionality I wanted without restarting xorg/X. 

Note: I did need to modify the specific configuration from the above suggested suggestions a little, by default (in my configuration) the forward and back keys seemed to be reversed.. so. Switching them around worked like a charm.

Here is the configuration I used,    ~/.xbindkeysrc.scm ```
(xbindkey '(XF86AudioPlay) "xmms --play-pause")
(xbindkey '(Mod4 x) "xmms --play-pause")

(xbindkey '(XF86AudioPrev) "xmms --fwd")
(xbindkey '(Mod4 Left) "xmms --fwd")

(xbindkey '(XF86AudioNext) "xmms --rew")
(xbindkey '(Mod4 Right) "xmms --rew")

(xbindkey '(XF86AudioStop) "xmms --stop")
```
[QUOTE=3david]I use "xbindkeys" to do this, just run:

   sudo apt-get install xbindkeys

and then put this code in ~/.xbindkeysrc.scm:

```

(xbindkey '(XF86AudioPlay) "xmms --play-pause")
(xbindkey '(Mod4 x) "xmms --play-pause")

(xbindkey '(XF86AudioPrev) "xmms --rew")
(xbindkey '(Mod4 Left) "xmms --rew")

(xbindkey '(XF86AudioNext) "xmms --fwd")
(xbindkey '(Mod4 Right) "xmms --fwd")

(xbindkey '(XF86AudioStop) "xmms --stop")

```

If you don't what's the string needed for your hotkey (Mod4 Left for example),
you can run "xbindkeys --key", and then press your key combination, and it will give you the text of this key combination.

(If anyone has an alternative way to do this, i'll be glad to hear, I've always searched for this ability in gnome)

I hope this helps :razz:[/QUOTE]

---

### Post by keitsi on 2005-12-04
apt-get install xbindkeys-config
pico ~/.xbindkeysrc
paste in the lines as kracker suggested
run xbindkeys

works like a charm for me, thanks :)

---

### Post by Nacker on 2006-01-21
Greetings everybody,
I think, I have an alternative way to make xmms hokeys work, which might be interesting for somebody. You'll have to complete several configuration steps to get that working:
1. Download and install xmmsctrl plugin from  [here]("http://user.it.uu.se/~adavid/utils/"). Just follow the installation instructions found within the package. To test the plugin just issue couple of simple commands in the console: "xmmsctrl launch", "xmmsctrl quit" and in case everything appears to be working, continue with the step 2.
2.Download the script code from the attachement below, rename it to something more apropriate for the script file :D (i.e. xmmshotkeys.sh) and chmod it to executable.
3. Now, try to run this script by passing some of the acceptable parameters to it (i.e. "./xmmsctrl up", "./xmmsctrl down" etc...). The list of the acceptable parameters:
[LIST]
[*]up - increases volume by 5%. Maximum value is set to 80% (Can be changed in the script)
[*]down - decreases volume by 5%
[*]v00 - sets the volume to 0%
[*]v25 - sets the volume to 20%
[*]v50 - sets the volume to 40%
[*]v75 - sets the volume to 60%
[*]v100 - sets the volume to 80%
[*]prev - jumps to the previous song
[*]next - jumps to the next song
[*]fw - skips 10 seconds forward
[*]bw - skips 10 seconds backward
[*]playpause - toggles play/pause modes
[*]play - starts the playback from the beginning of the song
[*]stop - stops the playback of the song
[*]runquit - to launch or quit xmms player
[/LIST]
4. Next step is to map xmmshotkeys.sh script to actual hotkeys. Open Configuration editor. Go to the apps -> metacity -> keybinding_commands section. Then modify one of the command_X keys (i.e. command_1) so it could run xmmshotkeys.sh script with one of the parameters (i.e. "/home/user/xmmshotkeys.sh up"). Now, go to the apps -> metacity -> global_keybindings section and assign key combination to one of the run_command_X keys (i.e. the modification of the run_command_1 key to "<Conrtol><Alt>Q" will allow the volume to be increased by 5% each time the key combination Ctrl+Alt+Q is pressed). Now, assign the hotkeys for every other parameter you need.
5. Fell free to modify the script as you like so it could fit your needs.

---

### Post by b0rka7a on 2007-12-31
Not working for me :D I'm using Gutsy.
I added the lines you posted 2 years ago to ~/.xbindkeysrc , but they still don't work...
Any advice ?
Thx in advance.

---

