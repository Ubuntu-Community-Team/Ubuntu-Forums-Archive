---
title: "How do I close an SSH session without killing the process"
date: 2007-03-25
forum: General Help
---

### Post by I922sParkCir on 2007-03-25
How do I close an SSH session without killing the process?

I want to run Folding@home and initiate it from a laptop, but when I exit the process ends. How to keep the process going so that when I log back in I can check up on it?

---

### Post by 505 on 2007-03-25
> **I922sParkCir said:**
> How do I close an SSH session without killing the process?

I want to run Folding@home and initiate it from a laptop, but when I exit the process ends. How to keep the process going so that when I log back in I can check up on it?

Use dtach. That program is available from the repros. It creates a virtual screen. I use it to run rtorrent on my server en check on the download progress once in a while. I think dtach can only do terminal programs, not GUI.

An example of my script to start and check on rtorrent:

dtach -A /tmp/rtorrent rtorrent

This command creates a session with the rtorrent program if not running, or open the session if running. Pressing Ctrl+\ detaches the program, so you can exit SSH, but the program itself will continue.

---

### Post by Ramses de Norre on 2007-03-25
You can also use **nohup** which is in fact created for problems like yours.
If you execute ```
nohup command &
``` the command will run independent from the invoking shell and will output everything to ~/nohup.out (or something like that).

---

### Post by cwaldbieser on 2007-03-25
> **I922sParkCir said:**
> How do I close an SSH session without killing the process?

I want to run Folding@home and initiate it from a laptop, but when I exit the process ends. How to keep the process going so that when I log back in I can check up on it?

You can also use the "screen" command.
[http://en.wikipedia.org/wiki/GNU_Screen]("http://en.wikipedia.org/wiki/GNU_Screen")

---

