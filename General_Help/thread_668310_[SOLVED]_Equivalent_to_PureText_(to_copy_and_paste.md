---
title: "[SOLVED] Equivalent to PureText (to copy and paste without formatting)?"
date: 2008-01-15
forum: General Help
---

### Post by fishwebby on 2008-01-15
Hello,

I'm new to Ubuntu, having come from Windows. In Windows I used to use a rather useful little utility - [PureText]("http://www.stevemiller.net/puretext/") -  that allowed me to paste text without formatting in any application. For example, sometimes when you copy text from a webpage and paste it into an email, you just want the text, not the formatting that goes with it. I know some applications have this option, but I was just wondering if there was an OS level way of doing it.

Does anyone know if anything similar exists (or there's already a method to do it) in Ubuntu?

Any help gratefully received!
Dave

---

### Post by dda on 2008-01-31
Hi Dave,

I tried glipper (sudo apt-get install glipper) - it seems that when you select formatted text, and then click on glipper icon, and click on the last item, formatting gets lost. I haven't found a way to use a shortcut (as in PureText) for pasting plain text. Hope it is still possible.

Best regards,
Dmitry.

---

### Post by HermanAB on 2008-01-31
Glipper on Gnome and Klipper on KDE.

Cheers,

Herman

---

### Post by fishwebby on 2008-02-01
Hi,

thanks for the replies - I've installed Glipper and tried what you said but I can't get it to remove the formatting on copied text. I see that Glipper supports plugins, and I thought there might have been one to do this but I haven't been able to find one. I suppose I could learn Python and write one!

Cheers
Dave

---

### Post by dda on 2008-02-01
I tried in pidgin - for example, selected "rather useful little utility - PureText" text with link on this page, and inserted it with middle-click - got the link inserted in pidgin, and then clicked on Glipper icon, and clicked on the topmost item in the list, and again inserted it with middle button in pidgin: [https://url.odesk.com/sb347](https://url.odesk.com/sb347) - see, the link is gone!

---

### Post by fishwebby on 2008-02-04
Ah ha! Now I've got it to work - thanks! :-)

---

### Post by dda on 2008-02-04
Interesting: the topic is '[SOLVED]' now (who did it?), but I'd not mark it as that, since we haven't found a hotkey.. I wonder if it is possible.

Regards,
Dmitry.

---

### Post by fishwebby on 2008-02-06
Hi, 

sorry that was me! I was so pleased to have a way to remove the formatting before pasting, I had forgot that the original question was a simple shortcut too. Well using Glipper there is a way, but it requires more than one keypress:

- Use Ctrl-C to copy some formatted text
- Press Ctrl-Alt-C to open Glipper
- Select the first item, using the mouse or press the down arrow twice
- Then use Ctrl-v to paste, and all the formatting has gone. Hurrah!

(this assumes you've got Glipper running all the time - I've put it to start when I log on)

I've also configured Glipper to only save one clipboard item (so the menu is nice and small) but you don't have to do that.

I don't know if a script could be written to do this and we could assign a shortcut key to it (is there a sort of system-level macro language? I know a bit about shell scripts but dunno how they could be used here... anyone?

Best regards
Dave

---

