---
title: "Applications and Open-Save dialogues freezing and blank (after upgrade)"
date: 2013-06-25
forum: General Help
---

### Post by nclm on 2013-06-25
Hello! :)

I upgraded yesterday from 12.10 to 13.04 and am now encountering this weird little bug. It is quite annoying and a large amount of things are unusable because of it. Can you help me? I tried some things but didn't manage to improve anything.

The issue appears in some applications or some windows (that I'll list after), systematically. Here is what happens in the concerned places:
[LIST]
[*]The window is totally empty, white, blank. 
[*]The whole application freeze, I have to terminate it to close it. 
[*]In the monitor, it turns from [FONT=courier new]poll_schedule_timeout[/FONT] to [FONT=courier new]futex_wait_queue_me[/FONT]. 
[/LIST]
That's instant as soon as the application or dialogue is opened. It does exactly the same with Cinnamon and with Gnome Shell.

Where does it happen?
[LIST]
[*]In the Open/Save/Save-As dialogues of several applications: Firefox, Thunderbird, Chrome, Gnome Subtitles, LibreOffice… I'm unable to open or save anything in them. 
[*]Some applications as a whole: The Gimp, HomeBank, SoundConverter… 
[/LIST]

It doesn't happen in:
[LIST]
[*]The Open/Save/Save-As dialogues of other applications: Gedit, Inkscape, Transmission, Totem, Brasero… they're all able to open and save. 
[*]Other applications. 
[/LIST]

I notably tried uninstalling/reinstalling Nautilus and Nemo, doesn't change anything. The system is up to date. How is managed the Open/Save dialogue? Is it still [FONT=courier new]GtkFileChooserDialog[/FONT]? Are some applications using different methods so that would explain the difference. Is this a GTK problem, then?

I'm lost and need your help! 
Thank you a lot.
Have a nice day!
~ Nicolas

---

### Post by nclm on 2013-06-25
When opening a faulty window, always this message in terminal:
> (firefox:9187): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/nicolas/.local/share/recently-used.xbel', but the parser failed: L'ouverture du fichier « /home/nicolas/.local/share/recently-used.xbel » a échoué : Permission non accordée.

(homebank:9242): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/nicolas/.local/share/recently-used.xbel', but the parser failed: L'ouverture du fichier « /home/nicolas/.local/share/recently-used.xbel » a échoué : Permission non accordée.

(gnome-subtitles:9278): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/nicolas/.local/share/recently-used.xbel', but the parser failed: L'ouverture du fichier « /home/nicolas/.local/share/recently-used.xbel » a échoué : Permission non accordée.

(gimp:9303): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/nicolas/.local/share/recently-used.xbel', but the parser failed: L'ouverture du fichier « /home/nicolas/.local/share/recently-used.xbel » a échoué : Permission non accordée.
I tried:
```
sudo chown nicolas /home/nicolas/.local/share/recently-used.xbel
sudo chgrp nicolas /home/nicolas/.local/share/recently-used.xbel
sudo chmod 775 /home/nicolas/.local/share/recently-used.xbel
```
The error doesn't display anymore, but the freezing blank issue is still there.
Was it a false trail?

---

### Post by nclm on 2013-08-18
That's crazy.

Today, I finally decide to completely re-install the system.
Even when playing everyday to bypass it, the previously described issue makes using the system unbearable.

So, here I am with an all freshly installed new Ubuntu 13.04.
Everything's good, I start installing some applications, customizing a little&#8230;

And the problem is back!

These Open/Save windows are totally broken again.
A not-even-one-hour old system is already unusable.

How is it possible to get the same thing again on a all new system?!
Do you have any idea of what is going wrong?
Many thanks!

**Edit:** [My apt history from system installation to soon after the problem's coming-back]("http://pastebin.com/DyD82Z9W").

---

### Post by nclm on 2013-08-18
Problem resolved!
In fact, it was useless to do a system re-install.

The cause was:
**The typeface Terminus (xfonts-terminus) used as the system font!**

Default font family restored and everything is back to normal.

Edit: [Launchpad Bug]("https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1182036")

---

