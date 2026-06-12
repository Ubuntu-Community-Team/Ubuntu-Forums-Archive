---
title: "Firefox lost bookmarks + history, rsync fail - 17.10"
date: 2017-12-20
forum: General Help
---

### Post by sterator on 2017-12-20
I installed 17.10 on my computer the other day, and began setting things up the way I need them, such as sites - like this one - and the log ins in Firefox. I've done some real work of the kind I do: Scribus, Gimp, Inkscape. I'm a designer/illustrator

Last night, I installed GNOME tweaks and made a couple of adjustments which it offers, restarted as it suggested. Everything looked fine.

Then I tried to do an rsync backup - made no apparent change in the destination folder whatsoever, yet I was told that I was running out of room! The size of my backup files is about 220GB; the destination drive is 500GB. I then removed all files from the destination and emptied the trash thinking I'd start with a clean slate, ran rsync again and when I woke, there wasn't anything in the destination drive at all! Zippo. Nada.

No errors thrown when I initiated the process, but at the end there was something about not being able to find the destination - I'd think that error would be thrown upon giving the command in terminal, yet I saw all of the rsync information fly up on the terminal window as per normal - going through all the files, etc.

Firefox, also, suddenly has no bookmarks I've saved and no history! It's as though I'd never launched it. I certainly didn't erase them.

Any clue what might be at work here? Would I be better off in 17.04? Is 17.10 still going through some..."growing pains?"

Thanks for any clues!

---

### Post by dragonfly41 on 2017-12-20
This sounds like a wrong rsync command run.

To view your last few commands run 

[B]history n

[/B]e.g. history 10

Post your rsync command here .. might be misuse of slashes.

Try using grsync (the gui for rsync) and use "dry run".

If you have important files to recover stop using your drive and use a LiveUSB to recover deleted files.

---

### Post by vasa1 on 2017-12-20
> **sterator said:**
> ...

Then I tried to do an rsync backup ...
No errors thrown when I initiated the process, but at the end there was something about not being able to find the destination - I'd think that error would be thrown upon giving the command in terminal, yet I saw all of the rsync information fly up on the terminal window as per normal - going through all the files, etc.
...

As dragonfly41 suggests, you could post the entire rsync command here for people to look at. You can also deal with "all of the rsync information fly up on the terminal window as per normal - going through all the files, etc." by logging the screen output to a file. I have *&>$(date +\%l)rsync.log* at the end of my rsync command. That generates a file that one can look at leisurely.

---

### Post by sterator on 2017-12-20
> **dragonfly41 said:**
> This sounds like a wrong rsync command run.

To view your last few commands run 

[B]history n

[/B]e.g. history 10
```

   36  Removed /run/systemd/system/media-artmaker-Bento_Backup.mount.
   37  Removed /run/systemd/system/run-user-1000.mount.
   38  Removed /run/systemd/system/run-user-124.mount.
   39  Removed /run/systemd/system/tmp.mount.
   40  sudo apt install gnome-shell-extensions
   41  su artboxeR
   42  sudo apt install gnome-shell-extensions
   43  sudo apt install gnome-shell-extensions
   44  sudo rsync -azvv /home/artmaker/Documents /media/artmaker/Bento_Backup
   45  history 10
```

> 
Post your rsync command here .. might be misuse of slashes.

```

sudo rsync -azvv /home/artmaker/Documents /media/artmaker/Bento_Backup
```

[/QUOTE]


Thank you!

---

### Post by dragonfly41 on 2017-12-21
I see that you did not have closing slashes on source and destination like this ...

```
[COLOR=#000000][FONT=&amp]sudo rsync -azvv /home/artmaker/Documents[/FONT][/COLOR]**[COLOR=#ff0000][FONT=&amp]/    [/FONT][/COLOR]**[COLOR=#000000][FONT=&amp]/media/artmaker/Bento_Backup[/FONT][/COLOR]**[COLOR=#ff0000][FONT=&amp]/[/FONT][/COLOR]**[COLOR=#000000][FONT=&amp] 
```[/FONT][/COLOR]

I suggest that you research the different results you get when leaving off closing slashes.
Here is one explanation I found ..
[http://qdosmsq.dunbar-it.co.uk/blog/2013/02/rsync-to-slash-or-not-to-slash/](http://qdosmsq.dunbar-it.co.uk/blog/2013/02/rsync-to-slash-or-not-to-slash/)

And install grsync and learn how to do a "dry run" before the real thing.

---

