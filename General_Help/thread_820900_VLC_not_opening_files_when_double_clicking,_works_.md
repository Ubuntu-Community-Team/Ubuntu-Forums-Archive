---
title: "VLC not opening files when double clicking, works in menu"
date: 2008-06-06
forum: General Help
---

### Post by oddworld on 2008-06-06
When I try to double click an avi file, I get the error: 
Unable to open 'file:///media/video500/Video/Futurama%20season%201-5%20(complete)%20+%20extras/Futurama%20Season%203%20(complete%20DVDRip)/Futurama%20-%20S03E09%20-%20The%20Bird-bot%20of%20Ice-catraz.avi'

But when I open up vlc, and click open and browse to the file, click on that in the vlc browser it will open and play as normal.
Why is it doing this?
How can I fix it?

---

### Post by spadewarrior on 2008-06-06
Try right click on file -> properties  -> open with -> select vlc 

I'm using xubuntu so the menus are a bit different, but it'll be similar to that( hopefully...).

---

### Post by oddworld on 2008-06-06
Did that, problem is much more complicated than that.
Its trying to open in VLC, but vlc opens and gives an error.

---

### Post by spadewarrior on 2008-06-07
Have you tried reinstalling vlc? Worth a go.

```
sudo aptitude reinstall vlc
```

---

### Post by oddworld on 2008-06-08
Did not work, still doing it.

---

### Post by cariboo on 2008-06-08
You've got way to many spaces in your file path and filename. Rename the file by replacing all the spaces with periods and give it a try, or you could try this:

```
vlc "Futurama - S03E09 - The Bird-bot ofIce-catraz.avi"
```

note the quotes around the filename.

Jim

---

### Post by oddworld on 2008-06-08
That is not my doing.
That is the error code produced when I double click on a file.
I am not controlling the number of spaces.

---

