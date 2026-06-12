---
title: "Gui / Cli"
date: 2008-06-21
forum: General Help
---

### Post by lost09 on 2008-06-21
Does anyone know how to switch to CLI? Or, ideally, how to toggle between GUI and CLI?

Thanks,
l

---

### Post by atomkarinca on 2008-06-21
Ctrl + Alt + F1 (also F2,F3 to F6) prompts you to CLI, Ctrl + Alt+ F7 back to GUI.

---

### Post by lost09 on 2008-06-21
Thanks! Is there a difference in functionality between F1, F2, etc when going to CLI?

Also, after logging in, I don't see a prompt. 

On an aesthetic note gigantic text is rather... ick. How can I change the resolution?

---

### Post by ibutho on 2008-06-21
By default there isn't any difference, but you can configure the functionality to be different if you wish. In most distros you can edit /etc/inittab to change the functionality. I think in Ubuntu you use /etc/default/console-setup and the tty files in /etc/event.d directory.

---

### Post by lost09 on 2008-06-21
Thanks. That still leaves the apparent lack of a prompt. It doesn't seem to allow me to do anything after I've logged in. Any thoughts?

---

### Post by ad_267 on 2008-06-21
Weird. You should have a prompt. Also you can use the cli by going to Applications - Accessories - Terminal if that's more what you're after.

---

### Post by lost09 on 2008-06-21
Yes, I know that. I was looking for more of a complete switch from the GUI. I don't know what's up with the lack of prompt, though. What sort of CI doesn't allow one to enter commands?

---

### Post by lswb on 2008-06-21
Maybe the "gigantic text" is a clue. Are the characters are about twice as big as expected? Default VT should have 25 lines of text and be 80 characters wide. If the resolution is not set up correctly you may in fact, have the prompt, but it may not be visible. 

If you think this may be the case, you can try this, you may have to enter it "blind", that is, it won't be visibly echoed to the screen

First, login with you userid and password,

then type 
   sudo vbetool vgamode 3

and press enter. If it doesn't change right away or if there are still some problems, Alt-F7 back to X then Ctrl-Alt-F1 back to the VT. ,

---

### Post by lost09 on 2008-06-22
The command wipes the screen and prints, in slightly smaller text "function not supported", before giving me a prompt. I'm not really sure what this means...

---

