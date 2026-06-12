---
title: "X11 thinks :1.0 is my primary display"
date: 2008-07-10
forum: General Help
---

### Post by johnsto on 2008-07-10
This is driving me nuts. This is on Hardy with an nVidia 8400GS with the 173.14.05 drivers.

The problem is that X11 is configured for one screen and one screen only. When I'm in gnome, 'who' reports that I'm using display :0. However, the environment variable $DISPLAY is set to :1.0 and 'xlsclients -display :1' also tells me what all my apps are running on display :1. 'xlsclients -display :0' reports nothing.

This little issue causes all sorts of weirdness in SDL apps, as they refuse to start unless I change DISPLAY to :0, and then when they do start, appear without any window decorators, and in the top-left corner of the screen covering everything else.

Anyone know what might be going on here?

---

### Post by Davidian1024 on 2008-12-09
I see that it's been some time since this thread was posted.  But I'll post anyway since I'm having the exact same problem.  Well, actually it's my brother who's having the problem.  And I thought maybe I could add some details that might point someone in the right direction.

He's running Ubuntu 8.04 Hardy with a Radeon HD 3200.

The DISPLAY environment variable is coming up as [COLOR="Red"]:1.0[/COLOR] when it should be [COLOR="Red"]:0.0[/COLOR]

This is causing direct rendering to fail.  I had him run [COLOR="Red"]export DISPLAY=:0.0[/COLOR] from a shell which allows him to get direct rendering in apps that are also run from the command line.

I think this is what caused the issue:  It all started when he tried getting dual monitors setup.  He was following some directions on a forum post and he installed the fglrx driver from their site.  The problem with that is an ATI driver was already installed and in use in Ubuntu's hardware manager.

I figure that variable is getting set that way in a script somewhere but I'm stumped as to where to look.

---

