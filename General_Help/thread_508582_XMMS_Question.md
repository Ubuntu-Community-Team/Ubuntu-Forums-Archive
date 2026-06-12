---
title: "XMMS Question"
date: 2007-07-24
forum: General Help
---

### Post by ghandi69_ on 2007-07-24
Hey guys,

I really like the way XMMS looks, with all the different themes available.  However, I have like 60 gigs worth of music, and having a library that displays each and every song is about impossible to use.  Is there a plugin somewhere where I can view my music files by directory structure or by album folder??

Thanks in advance.

---

### Post by Jose Catre-Vandis on 2007-07-24
Just click on the "Open" icon, or right click on the playlist window and choose "Add".

I tend to browse files with nautilus and use a nautilus script to enqueue:
```
#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	xmms --enqueue $uri &
done
```
(copy this text and paste into an empty file, make it executable and place in your nautilus scripts folder. then all you have to do is right click on your selected files and select this script)

My daughter (on Windows/Firefox) uses GNUmp3D which is set up on our file server to browse, enqueue and play, in Winamp. I would do the same but for some reason I cannot get XMMS/Firefox to handle the m3u files correctly

---

### Post by ghandi69_ on 2007-07-24
I use fluxbox and thunar, although I'm assuming I could use a similar script somewhere, anyone out there have one?

---

### Post by Jose Catre-Vandis on 2007-07-24
have a look here:

[http://thunar.xfce.org/pwiki/documentation/custom_actions](http://thunar.xfce.org/pwiki/documentation/custom_actions)

(Scroll down a bit to the "play music" section)

Maybe this will sort things for you?

---

### Post by ghandi69_ on 2007-07-25
Thanks Jose...

That has allowed me to browse with thunar and have them be added into XMMS.

I think what I was looking for (having a library of sorts, feature within XMMS) just isn't really supported.  This will work great for now though.

---

### Post by vanadium on 2007-07-25
XMMS indeed lacks an extended music library function. Yet for me, it is the player of choice because of gappless playback. I am using Nautilus to browse my music collection. For loading an entire album, I just navigate to the directory where the album directory is stored, then right-click - Open with XMMS (the first time, you will need to add this right-click item using "open with other application" while right-clicking the directory.

For encueing individual songs, the script is a good idea. The search function of Nautilus allows to quickly locate songs that then could be encued.

Nautilus allows to have the album cover used for displaying the directory, which is very nice. Unfortunately, however, setting it to use a graphic cannot be automated. I recently reformatted my drive to ntfs and used another disklabel. As a result, I can manually apply the customisations again.

---

