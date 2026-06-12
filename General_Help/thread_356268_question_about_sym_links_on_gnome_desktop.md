---
title: "question about sym links on gnome desktop"
date: 2007-02-08
forum: General Help
---

### Post by elettronicha on 2007-02-08
If  I link with a symbolic link something to the desktop (or it may be everywhere) , such as for instance
```
elettro@elettro:~/Desktop$ ln -s /media/data/Music/ Music
```,

when I click on the link, obviously it appears the nautilus window, but the location which is in is /home/elettro/Desktop/Music. 

The problem is that if I want to go up in the 'data' partition it's impossible with a single click (as it should be in theory), since with a single 'go up' click I go /home/elettro/Desktop.

---

### Post by tocleora on 2007-02-08
What you could do instead is create a launcher that points to "gnome-terminal --working-directory=/media/data/Music/" (without quotes).  This will open a terminal window and start you in the right folder.  Or if you'd prefer it be in a window you could do "nautilus /media/data/music".  Hope that helps.

---

### Post by elettronicha on 2007-02-08
Yes, it helps, thanks! :)
Although I keep thinking that seems a little inconcistency of the Gnome desktop and an easier way should be found.

---

### Post by sdide on 2007-02-08
Hey, 

you cannot obtain what you want with linking, beacuse it preserves working directory.

if you want a link on your desktop that opens a window with showing files and with the
right working directory.

you could do 

```
cd ~/Desktop
```
and 
put the following in a executable file:

```
#!/bin/sh
nautilus file:///media/data/Music &
```

which will start nautilus in the desired directory.

---

### Post by tocleora on 2007-02-08
I think the reason is, like if you have an app that requires /this/global/file, a shortcut would just take you to where the file really is which might confuse the app. Instead a sim link assumes the position of /this/global/file so everything works as it should.  That's completely a guess but makes sense to me at least. ;)

---

