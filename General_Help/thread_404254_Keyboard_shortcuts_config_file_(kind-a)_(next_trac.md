---
title: "Keyboard shortcuts config file (kind-a) (next track)"
date: 2007-04-08
forum: General Help
---

### Post by Reschat on 2007-04-08
I have a problem with two of my hotkeys that worked yesterday (and the day before) and just stopped working right now.

The keys work (0xb2 and 0xec) and they are set in "Keybord Shortcuts" to "Skip to next track" and "Skip to previous track" - but they don't do it anymore.

When I first had to make the keys work for switching tracks in Listen (music player) I had to change two lines in a "config"-file:
> xmms --next
xmms --prev
(or maybe another music-player)
to
> listen --next
listen --prev

And then it all worked.
But after installing (removing and reinstalling) a few video players (Kaffeine, MPlayer, Xine and Totem) earlier today - my two keys stoped working.

So I think it is the "config"-file that has been changed - but I have no idea where to find it.

I have also tryed:
gconf-editor > apps > metacity
and setting the keys to the commands "listen --next" and "listen --prev".
But no luck. That didn't work either.

Any ideas? Or anyone who knows where to find the file that specifies the  "Skip to next track" and "Skip to previous track"?

***EDIT*** I still need to know the file where I can change the actions for the "next track" and "previous track"

---

### Post by Reschat on 2007-04-08
Forget it. I found out a way to do it. I could use metacity - just not by opening it (that didn't change anything) but with commands it worked.

> gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_2 "0xb2"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_2 "listen --next"

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_3 "0xec"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_3 "listen --prev"


---

### Post by Reschat on 2007-04-08
After using this for a couple of hours now I can see that it takes about 1 sec. from pressing the key to the song changes. Before was it instantly.

So anyone know anything about this? Or know the file I was talking about?

---

### Post by xopher on 2007-04-08
Im actually having a similar problem, and my Media keys change names too :D. From eg. 0xef to XF86MediaNext etc. :rolleyes:

---

### Post by Reschat on 2007-04-08
xopher:

I know that one. It is because they already are set. Like if you set a key to "next track" it will have this funktion and not it's original. But when you change it (or remove it) (it = the function you have set it to), it will be the normal key again (like 0x2b).

So not really a problem. You just have to be aware of what you have set the diffirent keys to.

:)

---

### Post by strayduck_uk on 2007-04-09
I have a Dell wireless keyboard that has a shed-load of extra keys that I'd love to make work. What I'd really like to get going is the little media center cluster in the top right hand corner, which controls volume, plays, pauses, skips etc.

These keys did work in Kubuntu 6.10 with AmaroK, but I'm not a fan of KDE and when I switched to Ubuntu 6.10 and installed amaroK on the side, the keys stopped working. I can only control the volume.

Can you point me in the direction of where I can change this, if possible?

---

### Post by Reschat on 2007-04-09
If it dosn't work with:
System > Preferences > Keyboard Shortcuts
then you could try the metacity-methode:

First of all be sure that the setting in
System > Preferences > Keyboard > Layout
is right (or almost)

Then find out what the "keycode" is. You can do this from 
System > Preferences > Keyboard Shortcuts
(by using them to a not-used thing. Disable again with "backspace")

After this you can do something like this (i'm not sure about the commands - maybe they are diffirent from Listen):
(no sudo/root ; and KEYCODE is the keycode you just found)
> $ gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_3 "KEYCODE-TO-NEXT"

$ gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_3 "amarok --next"

$ gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_4 "KEYCODE-TO-PREVIOUS"

$ gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_4 "amarok --prev"

$ gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_5 "KEYCODE-TO-PAUSE/PLAY"

$ gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_5 "amarok --play-pause"

It think it would work. But you better test the commands first.

---

### Post by strayduck_uk on 2007-04-09
Sorted - thank you.

Keyboard shortcuts in the preferences menu did sort it for Gnome apps like Banshee, but it didn't work for Amarok - I guess because its a KDE app. It was useful for figuring out the keycodes though - you can find out the code for any key on the board including the extra media stuff along the top row.

The metacity method works a treat, the commands you gave were nearly identical but you can figure the rest of them out by doing

```
$ amarok --help
```

---

### Post by Reschat on 2007-04-09
Sounds good.

You can actually get the "Next track", "Pause", "Previous track" and so on to work with music players like AmaroK and Listen from the "Keyboard Shortcuts"-menu - but you just have to change a few lines i a file. A file I can't find anymore.

I also use the metacity for next and previous track - but the "normale" keyboard shortcuts are still working for my pause/play.
When I use the pause/play button the action happens instantly - but with the next/prev button it takes up to 2 sec. before anything happen.
When I was using the "normale" keyboard shortcuts it never took more then a 1/4 sec.

So I still want to find the file that specifies which music-player the commands work for.
(I know this excists because I have found and used it before.)
I hope someone can help me.

---

### Post by strayduck_uk on 2007-04-09
I have noticed that the "Launch Music Player" opens up what Gnome thinks is my preferred music app (Banshee). I've used metacity on this key to make it load amarok instead.

There isn't an option in System > Preferences > Preferred Applications to change what your default music player is. Perhaps if you can find the file which specifies what your preferred browser is, it will also have details of your preferred music player...?

---

### Post by Reschat on 2007-04-09
strayduck_uk - The "file" has that option. I know this because I changed it from "banshee" (or maybe "xmms") to "listen". And this options hasn't been changed back - so my "Launch music player" still works (meaning that it opens Listen and not Banshee or XMMS).

I really would like to find the file again. But no matter what I search for I can't find it. :(

---

### Post by Reschat on 2007-04-21
After updating to Feisty Fawn the Play-Pause button dosn't work anymore. 
I have set it in Metacity - but like with next and previous track the function now takes more then 1 sec.

So now when I want the playing song to pause I hit the button and then a few seconds later the music pauses. This is not the way I like it.
And it is still the same thing with the next and previous track buttons. Slow.

So I hoped that anyone could help me find a way to make the buttons work faster - instantly like they did after I changed the configurationfile a long time ago.
Maybe a script or something? But the
listen --play-pause
is too slow running through metacity or terminal.

Please someone - help me.

---

### Post by bignickel on 2007-04-21
My amarok keyboard shortcuts stopped working in Feisty as well.  Any suggestions would be appreciated.

---

### Post by Reschat on 2007-04-22
The problem is actually worse in Feisty Fawn.

When I start up my computer - the key settings from Metacity with next, previrous and play/pause aren't working.

I still don't know why.

So does anyone have any ideas on how to get my keys working? 

I want the key **0x97** to use the command **listen --play-pause** or just play/pause in Listen (last is best).
I want the key **0xb2** to use the command **listen -next** or just next in Listen (last is best).
I want the key **0xec** to use the command **listen --prev** or just previous in Listen (last is best).

They are set in Metacity but after every restart I have to set every key to "Open Terminal" in "Keyboard Shortcuts" to make them work (they don't work at startup).

Please - I really need this.

---

### Post by bignickel on 2007-04-22
OK, I now have my keyboard shortcuts working in amarok.  It's a bit of a hack, but it works.  The problem (as I see it) is that the Gnome shortcuts won't affect a KDE program (like amarok), so you have to map the keys at the X level.

1) Open a terminal.  Type:
```
xev
```
Press your multimedia buttons and write down the keycodes as they get displayed (on a Dell Inspiron 8600 Play/Pause is 162, Stop is 164, Previous is 144, and Next is 153).  Close the event testing window to close the program.

2) Make a new .Xmodmap file.  In the terminal type:
```
cd ~
gedit .Xmodmap
```
In the window that comes up, put in the following:
```
keycode 162 = F13
keycode 164 = F14
keycode 144 = F15
keycode 153 = F16


```
Please note that these are my keycodes.  You'll have to substitute the ones you got from Step 1.  I mapped them to F13-F16 because they don't exist on most keyboards but are still available for use.  Save and close this file.

3) Make an .xstartup file to run the maps when X starts.  In the terminal type:
```
gedit .xstartup
```
In the gedit window put in:
```
xmodmap .Xmodmap


```
Save and close this file.

4) Logout from your session and log back in.  This should load your new key mappings.  Open amarok, and go to Settings -> Configure Global Shortcuts.  Click on the Play/Pause and push your Play/Pause button.  This should put F13 into the box.  Repeat with the other buttons.  You should be in business!

5) If this doesn't work go back and run xev again and make sure you have the keys mapped properly.  You can also run:
```
xmodmap -pke
```
and look in the list.

Hope this helps!  I'm sure there's a better way to do it, but it was really starting to annoy me.

---

### Post by Reschat on 2007-04-22
bignickel  - I tryed your "guide" but then I got to step 4 - and Listen dosn't have these settings. So that didn't work.

So I deleted the .Xmodmap and removed it from gedit .xstartup
But then after a restart - there was no sound from the jack.
I can still get sound from en internal speakers - but not from the external connected with jack.
I have tested the external speakers on another computer and they still works fine there.

So any ideas on how to get my speakers working again?

---

### Post by bignickel on 2007-04-22
Did you have something in the .xstartup file previously?  If not you should just be able to delete the .xstartup file and everything will revert back to the original settings.  It's really weird that changing key maps would affect your sound.

---

### Post by Reschat on 2007-04-22
There was nothing in it before - and now it is deleted. But still no sound on the output. :(

---

### Post by juanjoe on 2007-04-24
Hello.
try with alsamixer and look at the Headphone item.
Press M to switch it on or off.

Hope this help

regards

---

### Post by Reschat on 2007-04-24
juanjoe - Tryed that many times. No help there.

I think I need something to reset all the sound settings and sound programs. Maybe that would help.
But I have no idea on how to do that.

Wow. I did it:
[http://ubuntuforums.org/showthread.php?p=2492518]("http://ubuntuforums.org/showthread.php?p=2492518")

---

### Post by Reschat on 2007-04-27
After a total reinstall I still have the problem. (Feisty)

So I hoped that someone had an advice.

*** EDIT ***

I have given up. I changed to Rhytmebox. I miss some of Listen's features (like minimizing to tray on close and normal minimize - I loved that thing).

---

