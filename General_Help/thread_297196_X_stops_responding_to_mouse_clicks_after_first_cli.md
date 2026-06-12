---
title: "X stops responding to mouse clicks after first click on boot"
date: 2006-11-10
forum: General Help
---

### Post by cfrancolini on 2006-11-10
I've been running a newly installed system with Edgy for about a week now and was very pleased with it, until things started going horribly wrong this evening. I deleted a file I wanted to get back, so I opened up the Trash can - none of the files would allow me to click on them. Even worse, some windows were responding to a mouse click (i.e. they would come to the forefront when clicked) but most weren't. I decided to reboot.

Now, every time I boot up, I can login OK, but as soon as I make the first mouse click (e.g. to open a terminal), X seems to seize up. I can continue typing into the window OK, and I can move the mouse around and the cursor follows fine, but from then on nothing responds to a click: I can't move windows around, I can't click on any toolbars or icons, I can't even click on the "logout" button.

I've tried two different mice and tried logging in via Gnome and KDE and the same thing happens every time. I've looked at top and nothing is happening processor-wise. I'm at a loss to know where to go next on this. Please help!

---

### Post by podunk on 2006-11-10
Do you happen to remember what you deleted? If you do you could likely re-download and install it using aptitude

---

### Post by cfrancolini on 2006-11-10
It was just a text file I was using to compile a playlist.

Turns out it was something to do with my MS Bluetooth mouse/keyboard thing. Even though I was also trying an ordinary USB mouse, until I unplugged the dongle and removed the BT config stuff, I just couldn't get it working.

Shame because the BT mouse/keyboard combo had been working all day until it fritzed on me. :(

---

### Post by petiejoe on 2007-01-31
Did you ever figure out how to fix the problem? I'm seeing the same thing, except that I've found that if I switch workspaces (using the keyboard, of course), and switch back again I can usually click to gain focus of the desired window, or sometimes if I first right click, then left click it will help. Basically, it's just as buggy as all heck which can get really annoying sometimes.

For anybody else who may be able to help, I'm using MS Bluetooth mouse and keyboard with XUbuntu on an old AMD processor. Any other questions, please feel free to ask (I'm not really sure what could be causing the problem besides possibly blue tooth in general)

---

