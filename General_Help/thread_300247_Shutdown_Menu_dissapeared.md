---
title: "Shutdown Menu dissapeared"
date: 2006-11-15
forum: General Help
---

### Post by Matusel3 on 2006-11-15
Last night my shutdown panel was working just fine, I could see all the icons, shut down, hibernate, suspend, etc. etc.

Then I decided to start Beryl, finish configuring it, and add it to startup.  When I went to shut down, I noticed that when I hit the button in the top right corner that normally makes the menu appear, nothing happens.

BUT... if I click on the spot on the screen where I know the shutdown option of the shutdown window should be, it shuts down.

So the window is there, it's just not appearing.

Any help on this is greatly appreciated, thanks!

Edit: Let me just add that Beryl had already been installed, I just hadn't got the issue with no menu bars resolved until last night.  So it isn't a setting I changed, it has to be something to do with the fact that Beryl is actually running now.

---

### Post by bulldog on 2006-11-15
Go to System>>Administration>>Login screen.

Go to the first tab local and tick the action-menu box

---

### Post by Matusel3 on 2006-11-15
That option was ticked...

Any other ideas?

---

### Post by DavidTangye on 2006-11-15
What is Beryl?
What version of Ubuntu are you running?

---

### Post by CatKiller on 2006-11-15
> **Matusel3 said:**
> Last night my shutdown panel was working just fine, I could see all the icons, shut down, hibernate, suspend, etc. etc.

Then I decided to start Beryl, finish configuring it, and add it to startup.  When I went to shut down, I noticed that when I hit the button in the top right corner that normally makes the menu appear, nothing happens.

BUT... if I click on the spot on the screen where I know the shutdown option of the shutdown window should be, it shuts down.

So the window is there, it's just not appearing.

This came up when xcompmgr was what all the cool kids were doing. Have you got that installed too? AFAIK there wasn't a fix, although that was a little while ago. You could learn the keyboard shortcuts ;)

---

### Post by strabes on 2006-11-15
@davidtangye

[www.beryl-project.org](www.beryl-project.org)

pretty much the best thing to hit open source besides this recent java hullaballoo

@matusel3

it has something to do with the separate login session that you (should) create when you install beryl. use sudo reboot and sudo halt instead. they're faster anyway.

---

### Post by kecsap on 2006-12-04
Try this: [http://ubuntuforums.org/showpost.php?p=1630565&postcount=12](http://ubuntuforums.org/showpost.php?p=1630565&postcount=12)

---

