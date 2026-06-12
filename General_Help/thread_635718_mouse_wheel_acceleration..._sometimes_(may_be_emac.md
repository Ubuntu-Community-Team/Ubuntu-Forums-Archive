---
title: "mouse wheel acceleration... sometimes? (may be emacs specific)"
date: 2007-12-09
forum: General Help
---

### Post by NinjaYeti on 2007-12-09
First off, no, this is not one of those 'How do I make the mouse wheel work in emacs" threads. 

Here's the deal. I've found that sometimes, when I use the mouse wheel to scroll in emacs, I get some acceleration (things start scrolling faster if I do more 'ticks' in a short period of time). I don't get this in any other apps that I've tried -- firefox scrolling has no acceleration, and neither does nautilus -- so, I'm suspecting this is an emacs-specific issue. However, I did say this only happens 'sometimes': I've found through some more testing that this magical acceleration doesn't occur if the mouse is in motion. Presumably, the mouse scroll events have to come from the same cursor position for this 'feature' to activate? 

I did some searching before posting this, and didn't find anything. Has anyone else experienced anything like this before? And are there any emacs/ubuntu gurus out there that might know what's going on? 

I run emacs on Debian at work, and don't see the same behavior there... 

I'm using a custom xft emacs-snapshot from [_this site_]("http://peadrop.com/blog/2007/09/17/pretty-emacs-reloaded/"), but I also see the same behavior on a vanilla build of the latest GNU source. 

version shows GNU Emacs 23.0.60.1

Any thoughts?

---

