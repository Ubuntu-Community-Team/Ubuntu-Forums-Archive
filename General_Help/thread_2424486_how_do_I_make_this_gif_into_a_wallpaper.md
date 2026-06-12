---
title: "how do I make this gif into a wallpaper?"
date: 2019-08-09
forum: General Help
---

### Post by ardouronerous on 2019-08-09
I'm running Lubuntu 18.04.

[https://www.youtube.com/watch?v=eD8nJknxw9o](https://www.youtube.com/watch?v=eD8nJknxw9o)

I've already converted this video into a gif file using this command:

```
 ffmpeg -i input.mp4 output.gif
```

What options do I have to use this as a live wallpaper on Lubuntu? Thanks.

---

### Post by yetimon_64 on 2019-08-09
Here are a few links that may be worth reading for you on this subject. It may be possible with xwinwrap (not in the repos, but a fork of it is available on github) or feh which is available in the repos; both use a bit of scripting to do the job...
[URL="https://www.reddit.com/r/linuxquestions/comments/81g4xo/ubuntu_1604_possible_to_set_animated_gif_as/"][COLOR=#0000ff]
--feh and script--[/COLOR][/URL]
[[COLOR=#0000ff]--xwinwrap and script--[/COLOR]]("https://www.reddit.com/r/linuxquestions/comments/81g4xo/ubuntu_1604_possible_to_set_animated_gif_as/")
[[COLOR=#0000ff]--xwinwrap on github--[/COLOR]]("https://github.com/ujjwal96/xwinwrap")

I tried this idea on Ubuntu a few years back after remembering the live wallpapers I used to use on Windows Vista, but without any success at the time. Hope it works for you, good luck. Cheers, yeti.

---

### Post by cruzer001 on 2019-08-09
Even though its a dead project i ran electricsheep for a while.  Perhaps you could use their old code.

---

### Post by Holger_Gehrke on 2019-08-09
feh won't work for this, it only displays the first frame of an animated gif. gifview from the package gifsicle is the program you'd want to use. It needs the option --animate or -a to show animations (without that option it displays the gif as a slideshow and waits for a keypress before going to the next frame. You can use it without any need for xwinwrap if you pass it the window-id of the desktop with the option '-w' (no, it's not the root window (wid==0) ...). Use xwininfo to find out what the window id of the desktop is. Or you could use mpv and use the mp4 without converting it to gif and pass the options '-loop-file=inf' and '--wid=<ID>' (replace <ID> with the window-id).

Holger

---

### Post by ardouronerous on 2019-08-09
Hi Holger.
Tried gifview first, it didn't turn out so well, the result was a slow moving gif background and it also covers my icons.

The results of mpv was better, but a few issues, first, when I hover my mouse over the background, it shows the Play/Pause options on the bottom, and second, no icons on the desktop.

---

### Post by again? on 2019-08-10
This works for me in Xubuntu 18.04.

I resized a gif to my screen resolution using gifsicle ...
ie
```
gifsicle input.gif --resize [target-size] > resized.gif
```


and then used wmctrl in the gifview command to print Desktop ID....
eg
```
gifview --no-interactive -w $(wmctrl -l | awk '/Desktop/{print $1; exit}') /home/glen/Desktop/resized.gif -a
```

May need to install wmctrl and gifsicle.
 
Desktop menu and conky was still shown but Desktop icons were not.
Gifview used 14.5mb of mem.
Vid showing gifview on desktop. [https://streamable.com/fd6j1](https://streamable.com/fd6j1)

---

### Post by ardouronerous on 2019-08-10
> **guber2 said:**
> This works for me in Xubuntu 18.04.

I resized a gif to my screen resolution using gifsicle ...
ie
```
gifsicle input.gif --resize [target-size] > resized.gif
```


and then used wmctrl in the gifview command to print Desktop ID....
eg
```
gifview --no-interactive -w $(wmctrl -l | awk '/Desktop/{print $1; exit}') /home/glen/Desktop/resized.gif -a
```

May need to install wmctrl and gifsicle.
 
Desktop menu and conky was still shown but Desktop icons were not.
Gifview used 14.5mb of mem.
Vid showing gifview on desktop. [https://streamable.com/fd6j1](https://streamable.com/fd6j1)

Doesn't work for me though, the result was a slow moving background animation.

> **Holger_Gehrke said:**
> feh won't work for this, it only displays the first frame of an animated gif. gifview from the package gifsicle is the program you'd want to use. It needs the option --animate or -a to show animations (without that option it displays the gif as a slideshow and waits for a keypress before going to the next frame. You can use it without any need for xwinwrap if you pass it the window-id of the desktop with the option '-w' (no, it's not the root window (wid==0) ...). Use xwininfo to find out what the window id of the desktop is. Or you could use mpv and use the mp4 without converting it to gif and pass the options '-loop-file=inf' and '--wid=<ID>' (replace <ID> with the window-id).

Holger

Hi Holger, I managed to get set the video as wallpaper with mpv:

```
 mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=<ID> /path/to/video
```

It works well, the only downside is no desktop icons.

---

### Post by ardouronerous on 2019-08-11
UPDATE: My wid=ID has changed, so the video doesn't play anymore during startup. How do I fix this without editing my autostart launcher every time my wid changes?

---

### Post by Holger_Gehrke on 2019-08-11
The answer to that is already in the post by guber2. The part in '$( ... )' of the gifview command in his post is a command-line substitution. The output of that command is put into the command line. So what you'd use is
```
mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') /path/to/video
```
You might have to use a different name for the window instead of 'Desktop' depending on locale (for example: in my German Xubuntu I would use 'Schreibtisch').

Holger

---

### Post by ardouronerous on 2019-08-11
Here's the results:
```
mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') /home/~/Videos/video.mp4
Error parsing option wid (option requires parameter)
Setting commandline option --wid= failed.

Exiting... (Fatal error)
```

---

### Post by Holger_Gehrke on 2019-08-11
Hm, perhaps the last sentence in my previous post was not clear enough. The 'wmctrl -l' produces a list of windows, the 'awk '/Desktop/ {print $1}' searches that list for the string 'Desktop' and outputs the first field of the line where it occurs. So if the desktop window is not named 'Desktop' in your locale there will be no output that gets put after "-wid=". In that case you have to put whatever the desktop window is called instead of 'Desktop' between the slashes in the awk-command. To find out what to put there just examine the output of  'wmctrl -l', it should be obvious.

Holger

---

### Post by ardouronerous on 2019-08-11
That worked, thanks!

---

### Post by ardouronerous on 2019-08-11
Spoke to too soon. I placed it inside a launcher in /.config/autostart:

```
[Desktop Entry]
Version=1.1
Type=Application
Name=Video Wallpaper
Exec=mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') /home/~/Videos/video.mp4
```

But when I restarted my computer, the video doesn't start at all. But it seems to work when I run the command in the Terminal.

---

### Post by yetimon_64 on 2019-08-11
> **ardouronerous said:**
> ...
```
[Desktop Entry]
Version=1.1
Type=Application
Name=Video Wallpaper
Exec=mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') **/home/~**/Videos/video.mp4
```

But when I restarted my computer, the video doesn't start at all. But it seems to work when I run the command in the Terminal.

You may have a problem with what I bolded in your config file details. Either "~" (by itself) or "/home/$USER" should work a bit better there.

---

### Post by Holger_Gehrke on 2019-08-11
The 'Exec'-line of a .desktop -file is **not** interpreted by the shell, so shell language construct will fail. The command-line substitution '$( ... )' and the pipe '|' are shell-language constructs. You can either put that line in a script and call that script from the .desktop-file or write it as
```

Exec=bash -c "mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') /path/to/video"

```

Holger

---

### Post by ardouronerous on 2019-08-11
Doesn't work on startup.
Strange, the other programs that I have on  /.config/autostart seems to start okay, all except video-wallpaper.desktop.
But it works when I manual click on the .desktop file though.

---

### Post by ardouronerous on 2019-08-11
UPDATE: I've retried this command on autostart:  

```
mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=<ID> /home/ardouronerous/Videos/video.mp4
```

And it works on startup. I don't know, for some reason, autostart isn't accepting to run this at start up:

```
bash -c "mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') /home/ardouronerous/Videos/video.mp4"
```

---

### Post by again? on 2019-08-11
Try delaying the start with the sleep command.
eg
```
bash -c "**sleep 5**; mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') /home/ardouronerous/Videos/video.mp4"
```

---

### Post by ardouronerous on 2019-08-11
> **guber2 said:**
> Try delaying the start with the sleep command.
eg
```
bash -c "**sleep 5**; mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') /home/ardouronerous/Videos/video.mp4"
```

This worked, thank you

I'll be monitoring it for a couple of days.

Thanks! :)

---

### Post by again? on 2019-08-11
Here's a toggle script based on your commands, if interested.

**toggle_live-desktop.sh** (make executable)(See note below for wmctrl command for your desktop)
```
#!/bin/bash

# checks if mpv -loop-file=inf process is running
# if not, runs mpv command
# else kills mpv -loop-file=inf process

STATUS=$(ps aux | grep -c "[m]pv -loop-file=inf")

if [ "$STATUS" == "0" ]
	then
		mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') /home/ardouronerous/Videos/video.mp4 
	else
		pkill -f "mpv -loop-file=inf --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') /home/ardouronerous/Videos/video.mp4"

fi
exit 0
```

**[COLOR="#FF0000"]**[/COLOR]Note** that the **wmctrl -l|awk '/Desktop/ {print $1}'** command would most likely need to be
altered for Lubuntu.
In Lubuntu, the pcmanfm file browser draws the desktop.
Check your **wmctrl -l** output.
eg List windows in  Lubuntu with pcmanfm running....
```
**[COLOR="#006400"]glen@Ubionic:~$[/COLOR] wmctrl -l**
0x00c00024 -1 Ubionic panel
0x01000003 -1 [COLOR="#0000FF"]Ubionic pcmanfm[/COLOR]     [COLOR="#FF0000"]<---desktop[/COLOR]
0x01000050  0 Ubionic glen       [COLOR="#FF0000"]<-----pcmamfm browser opened at my home directory[/COLOR]
0x02800003  0 Ubionic glen@Ubionic: ~
```

So the command for this example to retrieve the desktop window ID would be...
```
wmctrl -l | awk '/[COLOR="#0000FF"]Ubionic pcmanfm[/COLOR]/{print $1}'
```
Yours should be similar with a different hostname.

---

