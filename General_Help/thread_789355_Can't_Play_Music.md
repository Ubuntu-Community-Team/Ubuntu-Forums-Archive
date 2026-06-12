---
title: "Can't Play Music"
date: 2008-05-10
forum: General Help
---

### Post by madeleine2383 on 2008-05-10
I tried to listen to my music on my computer but it won't play. I know the sound cards are detected and working (not muted) because i can listen to music online. If i try to play a song with rhythmbox or gstreamer it won't work. I don't know what else to try.

---

### Post by macaholic on 2008-05-10
Are there any errors when you try to play files with programs launched from a terminal?

---

### Post by madeleine2383 on 2008-05-10
no errors whatsoever. Rhythmbox opens up and all my music is there but when i hit play it won't. It says how long the song is but the slider doesn't move. The same happens in GStreamer. When i restart my computer it will work but it will do it again if i stop the music or pause it.

---

### Post by ghost_ryder35 on 2008-05-10
perhaps you do not have all the nessassary plugins
sudo apt-get install gstreamer*

---

### Post by madeleine2383 on 2008-05-10
> **macaholic said:**
> Are there any errors when you try to play files with programs launched from a terminal?

how do you launch programs from a terminal? I haven't tried that

---

### Post by ghost_ryder35 on 2008-05-10
just type the programs name, in this example i used totem
 
```

totem

```

---

### Post by minus198 on 2008-05-10
> **madeleine2383 said:**
> how do you launch programs from a terminal? I haven't tried that

Start a terminal. (Applications -> Accessories -> Terminal)

Then type in "rhytmbox /home/<your username>/Music/The Name Of The Song.mp3"

You can use Tab to complete file and directorynames. Like this:

You are standing in "/home/username/Music/" and if you tab a couple of time, it will list all the musicfiles. Then you can typ the first letter of the song, and the name should be completed.

---

### Post by madeleine2383 on 2008-05-10
tried all the above suggestions and the music still won't play :(

---

### Post by madeleine2383 on 2008-05-11
> **madeleine2383 said:**
> tried all the above suggestions and the music still won't play :(

Help me please!!!!! [-o<

---

### Post by cmavr8 on 2008-05-12
My exact problem too.. "Play" button is pressed, but seconds are not changing, slider not moving, no sound.

---

### Post by madeleine2383 on 2008-05-12
BUMP...someone must know how to fix this. PLEASE?!?!?!??!?!??!

---

### Post by cmavr8 on 2008-05-16
[COLOR="SeaGreen"][B]SOLVED!

The magic command:
$ sudo apt-get --reinstall install ubuntu-restricted-extras[/B][/COLOR]

---

