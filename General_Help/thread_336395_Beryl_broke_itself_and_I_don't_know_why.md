---
title: "Beryl broke itself and I don't know why"
date: 2007-01-11
forum: General Help
---

### Post by Kossilar on 2007-01-11
When I left yesterday, everything was working fine. My desktop rotated happily when I needed it to. 

Today, I boot up my computer and Beryl isn't working. Its a bit annoying. I closed Beryl and tried running it from the command line and it gave me this:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I find this strange because my videocard is a Geforce 6800GS and I'm running the latest proprietary drivers. My understanding was that I didn't need GLX running on my system to run Beryl. The fact that I had Beryl running without ever having installed GLX seems to support this.

So what the heck happened? Running Linux without Beryl is like running a computer without the internet. It suddenly feels like a paper weight. :P

---

### Post by cmost on 2007-01-11
You probably installed that X server update that requires you to reinstall your video driver (ATI or nvidia.)  Hope this helps.

---

### Post by Kossilar on 2007-01-11
Yeah that seems to have fixed it. Thank you very much. :D

Any idea why the updates do that?

---

### Post by padlefot on 2007-02-11
How did you fix this? I have the same problem but I am not as skilled, could you post a simple howto?:-)

---

### Post by Kossilar on 2007-02-11
Well Cmost suggested that I needed to reinstall my videocard driver, so I did. And that immediately fixed the problem.

Since you probably had to install the proprietary Nvidia/ATI driver to get Beryl working, I would just recommend reinstalling your driver to see if that works.

---

### Post by amano on 2007-02-11
The envy script will reinstall the proprietary nvidia drivers automatically.

Install the .deb package, switch to the console with Ctrl+Alt+F2, log in and type "envy". Then choose to install the fitiing driver (nvidia or Ati).

But don't let it adjust your xorg.conf (it will ask you), if that worked before. It deactivated the beryl section there for me.

---

