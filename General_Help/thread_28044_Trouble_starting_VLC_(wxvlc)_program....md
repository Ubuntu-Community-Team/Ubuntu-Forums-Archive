---
title: "Trouble starting VLC (wxvlc) program..."
date: 2005-04-18
forum: General Help
---

### Post by Turin Turambar on 2005-04-18
Uh oh I have another problem. :(

After I restarted the system I could not start VLC for Gtk+ program from the APP menu. Nothing happened, but I did see the program in the System Monitor "sleeping". However, it runs the media files when I click on them, but there's no GUI - nothing, the files just play. But if I press "sudo wxvlc" or "sudo vlc" it will run with the GUI!

I'm puzzled. The only thing that I did before I restarted the system, was that I installed the Graveman and deinstalled Mpeg321! I really don't remember that I changed any permissions and some core stuff.

What happened and what should I do to fix it?

Oh yeah, the program used to play MP3's when I just move the mouse pointer over a MP3 file (it was like a preview). Nothing happens now.

---

### Post by bored2k on 2005-04-18
[QUOTE=Turin Turambar]Uh oh I have another problem. :(Oh yeah, the program used to play MP3's when I just move the mouse pointer over a MP3 file (it was like a preview). Nothing happens now.[/QUOTE]

The program is called Nautilus, and I believe it uses mpg321/123 to preview MP3 files. You mentioned you removed that file, so.. try reinstalling it.

---

### Post by Turin Turambar on 2005-04-18
Thanks, that solved the preview problem!

I also solved the VLC thing - I deleted the vlc config file and now works great. :)

---

