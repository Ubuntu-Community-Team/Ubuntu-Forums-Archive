---
title: "program closes after terminal/console closes (even with ampersand)"
date: 2007-03-15
forum: General Help
---

### Post by josephus on 2007-03-15
I'm running Edgy Eft for a couple months now, and recently I've noticed that programs that I launch from the terminal are closing after the terminal closes.  I use the ampersand (&) after the command (e.g. rhythmbox &)  but the program closes after I close the terminal window.

I've tried this on a number of programs and all have the same effect.  I don't see any messages in the system log which seem to be related, so I don't even no where to start.  Any help would be appreciated.

---

### Post by lloyd_b on 2007-03-15
> I'm running Edgy Eft for a couple months now, and recently I've noticed that programs that I launch from the terminal are closing after the terminal closes. I use the ampersand (&) after the command (e.g. rhythmbox &) but the program closes after I close the terminal window.

I've tried this on a number of programs and all have the same effect. I don't see any messages in the system log which seem to be related, so I don't even no where to start. Any help would be appreciated.

If a program is associated with a terminal, when that terminal is closed, the program is terminated.  This is normal behaviour in the Unix world.  The fact that you're running the program in background (via the "&") doesn't change this.

I'd suggest launching those programs from Gnome (or KDE, or Xfce).

Lloyd B.

---

### Post by josephus on 2007-03-16
thanks.  I always thought that & dissociated the program from the terminal, and not simply putting it in the background.  

Is there a command that properly dissociates programs from the terminal?

---

### Post by DougieFresh4U on 2007-03-16
Try this in terminal:   **nohup (program name)**. then when program opens try closing terminal. Let us know if that worked.

---

### Post by josephus on 2007-03-16
That's exactly what I was looking for.  Thanks a lot.

---

### Post by DougieFresh4U on 2007-03-16
> **josephus said:**
> That's exactly what I was looking for.  Thanks a lot.

Your very welcome!! :)

---

