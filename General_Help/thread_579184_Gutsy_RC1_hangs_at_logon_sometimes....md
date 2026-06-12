---
title: "Gutsy RC1 hangs at logon sometimes..."
date: 2007-10-18
forum: General Help
---

### Post by w.d on 2007-10-18
Hi all,

Since yesterday I have a problem (well, to be honest, I noticed it yesterday, the problem might have been there a while). I'm sure it wasn't there last weekend.
When I boot my computer, it's no problem to login to gutsy rc1. But when I log off and try to login again, I get a black screen with only a mouse pointer. Nothing more, nothing less!
When I try to switch to a different runlevel (ctrl-alt-F1 for example) I only see a blinking cursor in the upper left corner of a black screen.
When I press ctrl-alt-backspace, I can get back to the logon screen. 
Safe mode doesn't work, the only thing that works is reboot my computer. Then everything is fine again, until I log off...
Th only program I've installed in a week is Avant Window Navigator. Removing that program and its obsolete dependencies doesn't solve the problem.
I can't find anything weird in the logs, but then again, I'm only an amateur ;)
Does anyone have a clue? I'm not too keen on reinstaling the whole system...

TIA!

---

### Post by radostyle on 2007-11-15
I have the exact same issue.  I have an Nvidia card, I tried turning off the visual effects, but I still can't use the ctrl-alt-backspace.  This is a problem for me because I use that to switch over to a different display.  Running "sudo /etc/init.d/gdm restart" at the command line works fine for restarting gnome, but if you do that after hitting ctrl-alt-backspace it doesn't work, it just hangs there with an empty tan screen and and a cursor pointer.

---

