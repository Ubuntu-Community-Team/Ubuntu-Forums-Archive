---
title: "Mouse no longer triggers compiz events!"
date: 2008-05-27
forum: General Help
---

### Post by wastedfluid on 2008-05-27
Ubuntu 8.04
Compiz
Emerald

Suddenly, sometime tonight.. my wireless mouse stopped enabling the bindings for Compiz Special Effects.

None of them work anymore(ie; Rotate cube, the transparency plugin) - none of them that have to deal with the mouse.  The plug ins are still enabled, but no longer work.

However, I know the cube is still there - if I drag a window the next desktop over, It'll flip desktops and rotate the cube.  Or if I press Alt+control+right/left on my keyboard - the cube flips!  But pressing control+alt+dragging my left button on my mouse no longer moves the Cube.  Additionally, the transparency plugin via using your scrollbar on your mouse no longer works for me, either.. or for my synaptics touchpad either.

This is very frustrating, and the only thing I can think of was maybe I had to switch batteries in my mouse, and had to restart my laptop without them mouse for a session.

Can anyone help?  Any ideas?

Thanks in advance!

---

### Post by Forlong on 2008-05-27
I'm sorry, never heard of such a problem.
You could try resetting all your Compiz related settings like this:
```
gconftool-2 --recursive-unset -a /apps/compiz
```
But then all your settings will get lost of course.

---

### Post by wastedfluid on 2008-05-27
Thanks for your reply.  I did that, as well as another HOWTO on how to remove all gnome settings... still no dice.

Here's something that might help.

When I press ctrl+alt+hold my left button, it goes to select files.. creates that box that flows with your cursor, as if it's not detecting the CTRL+ALT, or the "BUTTON1" activation...

Also, yesterday, my "ACTIVE WINDOW" toggles were messing up.. as in, if I am in Firefox, and i have xchat in the background, behind it.. and I click on xchat, anywhere in the Window - it wouldn't switch the active window, it would keep FIREFOX as the active.

Hope this helps.;  This is kind of annoying.

---

### Post by wastedfluid on 2008-05-27
Did a complete re-install, with BRAND new settings, and everything - still does it.  

No rotate cube... but I can change desktop via CTRL+ALT+right/left.. and the windows don't toggle correctly between active/not active.

Bump?

---

### Post by wastedfluid on 2008-05-28
I have figured it out, it's totally key bindings.  Why it's not working, I have NO idea... but KEY BINDINGS are the reason it's not working.  Something with the keys(Control+Alt+Button1) isn't registered.  The cube is there, and all other desktop effects work.. I just wish I knew why the key bindings for ROTATE cube don't.  And If I change the bindings, it still doesn't work.  When you go to drag on the desktop, it acts as if you want to select/highlight multiple files.

---

### Post by conspiro on 2008-12-19
I just unplug wireless usb receiver and then plug it again! It solves the problem!

---

