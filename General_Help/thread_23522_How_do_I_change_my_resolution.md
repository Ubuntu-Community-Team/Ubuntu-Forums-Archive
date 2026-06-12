---
title: "How do I change my resolution?"
date: 2005-04-02
forum: General Help
---

### Post by IceDigger on 2005-04-02
How do I change my monitor in ubuntu?

It is set for 1024x768 and the LCD's native resolution is 1280x800.

I tried to set it up in the "Screen Resolution" program under System and that only went up to 1024x768.

My LCD is a Proview pl576ws.  It was cheap :D

I'm new to linux so don't kill me.

---

### Post by askreet on 2005-04-02
During the installation it auto-detects and sets up your xorg.conf/XF86Config files (depending on which ubuntu you are using)

IF you are using Hoary edit your /etc/X11/xorg.conf file, if you are using Warty edit /etc/X11/XF86Config-4

Find this section:  (Yours may look different)

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection


Where you see the line Modes, change it to "1280x800" then restart X by closing all your programs and hitting ctrl-alt-backspace

Enjoy :D

---

