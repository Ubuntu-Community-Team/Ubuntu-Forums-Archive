---
title: "DVD mounting problems"
date: 2007-03-03
forum: General Help
---

### Post by Zalbor on 2007-03-03
If I insert a CD in my drive, it's auto-mounted with no problems. But the following problem happens with most (not all) DVDs:
I insert it, and its icon appears on the disk mounter applet. Then I try to open it, but instead of getting a window with the files contained, I get a DVD creator window. If I open a terminal and go to the directory where it's supposed to be mounted, I find it empty. I can mount the disc by "sudo mount /cdrom" and then I can see the files from the terminal, but the only way to see them from nautilus is to go to the directory (the "DVD-ROM DISC" icon still opens the dvd creator).
This happens with all kinds of DVDs that I've tried. Movies or data, printed or burned.

What could be causing that?

---

### Post by treesurf on 2007-03-03
I am suddenly having this exact same problem as well.  Any suggestions would be appreciated.

---

### Post by treesurf on 2007-03-03
Totem shuts down when I try to open any dvd with it.  However, I found that VLC Media Player will play a disc.  I still can't open it with Nautilus, though.

---

### Post by vince32 on 2007-03-04
**[FONT="Arial Black"][/FONT]**

under system-preferences-Removable drives and media click to open.
under multimedia tab Play video dvd disc when insert,, type in or browse
/usr/bin/vlc.
  Now when you insert a disc to play cd or dvd vlc will open.



Vince32

---

### Post by Zalbor on 2007-03-04
That's not what I want to do though, I want to mount them so that their files are accessible. If it's a movie and I want to watch it, I can launch a video player myself.

---

### Post by Zalbor on 2007-03-09
Any one else?

---

