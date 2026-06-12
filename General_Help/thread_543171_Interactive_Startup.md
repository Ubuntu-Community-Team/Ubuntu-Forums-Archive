---
title: "Interactive Startup"
date: 2007-09-04
forum: General Help
---

### Post by dburnett77 on 2007-09-04
I'm wanting to go into an Interactive Startup, or Verbose mode, with Feisty.
I tried pressing 'I' like you would in Red Hat, and also edited /boot/grub/menu.lst to remove the 'quiet' line.
Neither of these worked.

I've pressed 'ESC' while GRUB was loading to remove the 'quiet' option for the kernel I was booting, and still I get the graphical startup.

What am I doing/not doing?

---

### Post by thelocust on 2007-09-04
I think you have to remove "splash" to. I use recovery mode anytime I need to see whats going on.

---

### Post by glotz on 2007-09-04
quiet tells the kernel to stfu unless it's got something real interesting to say.

---

### Post by dburnett77 on 2007-09-05
> **thelocust said:**
> I think you have to remove "splash" to. I use recovery mode anytime I need to see whats going on.

Thanks, thelocust. Seems that at first I had the right idea, just the wrong location.
In GRUB, I was removing the last 'quiet' line, but at the end of the 2nd line there was a 'quiet' and 'splash'.  When I chose to edit the line that began: /boot/vmlinuz , it was off of the screen until I edited.

Also, Recovery mode gave me the same info.  However, the error I'm getting is right at the end of startup, and I go straight into log in before I can determine what it is.

I've checked /var/log/messages, and about the only thing I see relates to avahi, and eth0 not being ready.  I don't have a cable, as I use wireless.  This could be it, but I'm not certain.

I know in Windows/DOS, you can hit the PAUSE/BREAK key to stop the screen output.
Is there a way to do this in Ubuntu?

---

