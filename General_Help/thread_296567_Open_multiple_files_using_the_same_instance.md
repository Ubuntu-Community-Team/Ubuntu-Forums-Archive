---
title: "Open multiple files using the same instance"
date: 2006-11-09
forum: General Help
---

### Post by lazork on 2006-11-09
This is a problem I encountered while trying to open several mp3s with Audacious, but I guess the same issue applies to other files/applications as well.
When I open multiple files from nautilus (either by pressing enter or by choosing "Open with Audacious") it's like the commands being executed were:
```
audacious "file1.mp3"
audacious "file2.mp3"
...
```
which clears the audacious playlist before adding each of the songs (or, generally speaking, opens a different instance of the program for every file).
What I'd like to happen instead was:
```
audacious "file1.mp3" "file2.mp3" ...
```

I know that by typing this in a terminal, audacious acts properly (adds all the files to the playlist), so how can I do this with file association (choosing which command to use when opening the files)?

---

### Post by kerry_s on 2006-11-09
What happens when you high light all the files/select all and use open with, instead of picking 1 at a time? (click & drag to select several)

---

### Post by lazork on 2006-11-09
I see I didn't make myself clear enough.
What I'm doing is:
[LIST=1]
[*]select all the files I want to open (let's say I use ctrl+a to select all the  files in a folder)
[*]press enter (or right click and choose "Open with audacious")
[/LIST]
The odd thing is that xmms instead opens the files altogether (no other application does it - I'm trying with audacious, but the same thing goes for any other app (eg: vlc))

---

### Post by kerry_s on 2006-11-09
Ah, i see. I only use xmms and mplayer, that's why i thought it works in xmms.LOL, i just figured it would just work in others. 

Does it have a option to select a folder for the play list?

---

### Post by lazork on 2006-11-10
The only thing I can do is open a folder (or several files) from audacious, but that's kind of annoying, since I have to open the player first and then load the files from there.
What's more, I was trying to find a more general solution, that allowed me to do the same thing with other applications, in case I need to.
Does anyone know if there's something that can be done about it?
And still I'd like to know why xmms (and mplayer) behave differently...

---

### Post by lazork on 2006-11-12
I found the solution.
All I had to do was editing the file audacious.desktop (located at /usr/local/share/applications ) and change the line
```
Exec=audacious
```
to
```
Exec=audacious %U
```

---

