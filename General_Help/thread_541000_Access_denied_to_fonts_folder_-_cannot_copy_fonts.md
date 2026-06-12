---
title: "Access denied to fonts folder - cannot copy fonts"
date: 2007-09-02
forum: General Help
---

### Post by linfan on 2007-09-02
I am trying to copy some Windows fonts but when I drap & drop I am told permission denied?

---

### Post by strabes on 2007-09-02
The fonts folder is owned by root so you'll have to be root in order to write files to it. You could accomplish this by running "sudo nautilus" or just copying the fonts using the "cp" command:```
sudo cp /path/to/my/fonts/font.ttf /usr/share/fonts/truetype/font.ttf
```

---

### Post by chouf on 2007-09-27
I'm having more or less the same issue.
I'm trying to copy some .wav files in the */usr/share/sounds* directory, not that I especially want that particular folder but I've identified it as the *"main"* media repository for the OS; a little bit like *C:\Windows\Media*. Maybe I'm wrong, so don't hesitate to correct me.

Basically, I like some on the notification sounds from Windows XP and I'm simply trying to add them in the same folder as all the default Ubuntu sounds.

When I try to copy the files (drag drop files between windows), I get an error message saying that I do not have write access.

[LIST=1]
[*]Is there no other way to get "admin" access than using the terminal?
[*]Is it a good idea to copy extra media files in /usr/share/sounds?
[*]I'm from Windows and I know where to store my docs, application,... would you know where I could find a brief description of all folders in Ubuntu (like if I want to install software ABC, where's the best place to install it?)
[/LIST]

Thanks in advance

Chouf

---

