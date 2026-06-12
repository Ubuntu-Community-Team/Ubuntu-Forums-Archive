---
title: "messed up my login"
date: 2007-07-01
forum: General Help
---

### Post by mik9dt on 2007-07-01
I use the gnome desktop
I added another user using users and groups
I enable accessible login
On re start I end up with a blank screen and a waiting symbol.

What did I do wrong?

How do I mend this?

---

### Post by mik9dt on 2007-07-01
OK here we go,

If you are tempted to enable system>Admin>Login Window>Accessibility tab>enable accessible login... Stop!

I don't know why, it is a bug, search google and find several horror stories.

Having selected this option you may not be able to login at all.

Here is how I escaped from disaster.

When you start the computer GRUB offers several options, usually you just select the top one or let it happen automatically. Well, when you see the list select the 2nd option down, the one marked "recovery".
I found myself at a prompt logged in as root.
If your login name is alan then type the following, obviously substitute your own login
**su alan**
then press enter you are now logged in at the prompt as alan.
**startx**
it said x was already running... problem... type
**sudo startx**
enter your password
Now you should get to your desktop... go straight to that option you enabled and uncheck the box!
Subsequent logins should be back to normal.

I recognise this may seem easy to an old hand, but to a noob it is far from obvious.

Do not enable accessible login until they have fixed the bug. IMHO:)

---

