---
title: "Shutting down"
date: 2006-08-03
forum: General Help
---

### Post by Koybe on 2006-08-03
Hello,

I want my pc to shut down when i push the power button of the box. But since dapper, it brings up the "log off/switch user/poweroff/..." menu. How can i bring the shutdown back directly without clicking on screen?

Thank you

---

### Post by philippe_carlo on 2006-08-03
Seems like the Ubuntu control center does not provide an interface for that. I think you will have to read this mini howto to make this work for you:
[http://www.capaman.8m.com/acpid.html]("http://www.capaman.8m.com/acpid.html")

---

### Post by Felzix on 2006-08-03
I'm not positive what it is that you're asking, but I think that you want to bypass the decision given to select which shutdown mode to use when one pushes the power button.  It's probably important to note that I have a laptop.

I managed to do this by going into System, Preferences, Sessions, under the Session Options tab.  I then deselected the "Ask on Logout" option.

I have since reversed that change due to my annoyance at not having an option when I want one, so I can't confirm if it will work the way you desire under any circumstances.  I hope it helps, anyway.

---

### Post by Riverside on 2006-08-03
> **Koybe said:**
> I want my pc to shut down when i push the power button of the box. But since dapper, it brings up the "log off/switch user/poweroff/..." menu. How can i bring the shutdown back directly without clicking on screen?Whenever I want to shut down my computer and power it down completely, I type in a terminal window:

```
sudo poweroff
```
If I have understood your question correctly, that may work for you also.

---

### Post by Koybe on 2006-08-04
> **philippe_carlo said:**
> Seems like the Ubuntu control center does not provide an interface for that. I think you will have to read this mini howto to make this work for you:
[http://www.capaman.8m.com/acpid.html](http://www.capaman.8m.com/acpid.html)

This helped. I just edit the /etc/acpi/powerbtn.sh and comment the line related to gnome. But anyway it doesn't seem to desactivate the menu which stil appear. But it's shutting down the pc directly, that's ok. Anyway the X session is killed quite repidly and not very smoothly... So i guess there is another way. I'll search.

Thanks for the other suggestions but it's not really what i want.

---

### Post by kvonb on 2006-08-04
Hi,

You could make a simple script as follows:

#!/bin/sh
poweroff

Save the preceding text as shutdown.sh, make it executable: chmod +x shutdown.sh, then create a shortcut on your desktop/menu bar, give it a cool icon, then just click it when you want to shutdown.

The only problem is that I don't know how to make the script run as a root process, ie do away with "sudo" or asking for a password!


Something to do with "visudo" and enter the thing as a root privileged task, but that is beyond me at the moment, sorry, I'm not much use really!

Regards,

Kev :)

---

### Post by Koybe on 2006-08-04
Thank you, i know that. But what  want is shutting down using the power button of my pc. :-)

---

