---
title: "Conky script logging massive amount of error messages"
date: 2019-01-22
forum: General Help
---

### Post by goodstuff9 on 2019-01-22
Ubuntu 18.04, conky 1.10.8.  

I have an internet radio player application called "Goodvibes" installed.  

I have a conky "script" (correct term?) running.  When Goodvibes is running, but the Goodvibes' state is "Stopped", then the conky script produces a message on the desktop that says, "Goodvibes is not playing."  When Goodvibes' state is "Playing", then the conky script produces this output:  The name of the station that is playing, the artist and track that is playing, , and the volume level and a volume bar.  This all works fine.  

The problem is when Goodvibes is not even running.  In this case, the conky script produces a message on the desktop that says, "Goodvibes is not playing."  That is what I want.  However.....  In this case conky is also flooding an error log with this message every three seconds:  "Service org.mpris.MediaPlayer2.Goodvibes is not running."  

I show the relevent section of the conky script below.  I believe the problem is that, even though Goodvibes is not running, the execi and execpi commands in the conky script are still being "evaluated", but because Goodvibes is not running, I  am getting these error messages.  

Goodvibes works, and the conky script works - I'm just trying to modify the conky script so that when Goodvibes is not running, I still get the output of "Goodvibes is not playing", but without all the error messages about the service org.mpris.MediaPlayer2.Goodvibes not running.  

How do I modify this conky script to accomplish that?  



conky.text = [[

${if_match "${execi 3 qdbus org.mpris.MediaPlayer2.Goodvibes /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlaybackStatus}" == "Playing"}

${color2}Goodvibes Info

Station:  ${color0}${execpi 3 qdbus org.mpris.MediaPlayer2.Goodvibes /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep "^goodvibes:station:" | cut -d':' -f3-}

${color2}Artist - Track:  ${color0}${execpi 3 qdbus org.mpris.MediaPlayer2.Goodvibes /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep "^xesam:title:" | cut -d':' -f3-}

${else}

${color2}Goodvibes is not playing.${color0}

${endif}

${color2}Volume (0 - 64):  ${color0}${exec amixer -c 1 get Master | grep Mono:}

${color0}                  ${execbar amixer -c 1 get Master | grep -o -E '[0-9]{2}' | head -n3 | tail -n1}

]]

---

### Post by CatKiller on 2019-01-22
You could try adding ```
2>/dev/null
``` to the commands that are executed.

That redirects the stderr to a black hole. It's possible that will also stop it logging the error.

Specifically, it's the first line that's triggering the error: you're execing that regardless of whether it's running or not, to see whether it's running or not. The execution of the other two lines is conditional.

---

### Post by goodstuff9 on 2019-01-22
> **CatKiller said:**
> You could try adding ```
2>/dev/null
``` to the commands that are executed.

That redirects the stderr to a black hole. It's possible that will also stop it logging the error.


Thanks.  

My preference is to get the logic "right" so the message are not even generated in the first place.  

If that can't happen, I actually did try what you are suggesting.  It never worked, I still kept getting all those messages.  But, I was never sure I was putting the 2>/dev/null in the exactly correct spot.  Should that go immediately prior to the final } (right brace) that ends each execi and execpi command?  That is where I had put it before when it did not have the desired effect.  (The way I know it wasn't working was if I'd run a command like this:  journalctl -b and output it to a text file, that text file was packed full of these error messages, even though I had added the 2>/dev/null to those commands as I described.)

---

### Post by CatKiller on 2019-01-23
> **goodstuff9 said:**
> But, I was never sure I was putting the 2>/dev/null in the exactly correct spot.

It would go after the command itself, so something like
```
${if_match "${execi 3 qdbus org.mpris.MediaPlayer2.Goodvibes /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlaybackStatus 2>/dev/null}" == "Playing"}
```

It's possible that you'd still get the entry in the log even with the error redirection; I haven't played much with qdbus to know either way.

[This page](https://askubuntu.com/questions/350208/what-does-2-dev-null-mean) has some information on how output redirection works.

It's possible that rather than interrogating qdbus for results about an object that doesn't exist, you could do something softer with Lua to wait for Good Vibes to announce itself. That's not something I have any experience with, though.

---

