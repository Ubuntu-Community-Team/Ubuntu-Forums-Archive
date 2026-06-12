---
title: "Unassociating .dat from MPEG videos"
date: 2006-10-15
forum: General Help
---

### Post by mrfoobar on 2006-10-15
I have a bunch of text files with the extension .dat that I'd like to be able to easily open in nautilus, but I get the following message each time I double click one.

```
The filename "####.dat" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file

```

How do I unassociate the .dat extension from MPEG video?

---

### Post by Kateikyoushi on 2006-10-15
In Nautilus right click on it, select properties, and in the open with tab change the application.

---

### Post by mrfoobar on 2006-10-15
Alas, only if it were that easy.  When I go into properties->Open With,the default application is indeed Text Editor.  Nautilus knows it is a plain text file, but the .dat association is somehow associated with MPEG video so nautilus won't let me open it because it "might present a security risk to your system". I could just change the file extension to .txt, or always open the files in a terminal but I'd prefer to solve this problem and be able to have nautilus open them in gedit with a double click without having to rename them.

Heres the message I get again:
"The filename "####.dat" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. "

---

### Post by taurus on 2006-10-15
Try to play it with mplayer from a terminal...

```
gmplayer <filename>.dat
```

---

### Post by Kateikyoushi on 2006-10-15
Those are not video files but text files.
So he can't play them with mplayer.

---

### Post by taurus on 2006-10-15
> **Kateikyoushi said:**
> Those are not video files but text files.
So he can't play them with mplayer.
But nautilus reports them to be MPEG video files!!!

---

### Post by Kateikyoushi on 2006-10-15
I see, you mean he might be mistaken about the content of those files.

Then mrfoobar play the files with mplayer, if it can play them those are not text files.

---

### Post by mrfoobar on 2006-10-16
No, mplayer cannot play them.  I've tried looking through the various text files in /usr/share/mime and the only place I found the association was in /usr/share/mime/globs. I tried commenting out the line that associates .dat files with video mpeg (video/mpeg:*.dat) but that didn't have any effect.  Does anybody know any other places I can go to change the extension->mime association?

---

### Post by pel on 2006-10-29
I have the same problem but with sgf (smart game format) files, except this time nautilus complains that the 'contents' of the file is probably a text file. Wich it is, too, in the same way an xml-file is a text file.

So nautilus ends up claiming it is a text file and it won't let me open it because it prolly contains unlawfull combatants.

---

