---
title: "My power off button is gone!"
date: 2008-03-06
forum: General Help
---

### Post by LeoSolaris on 2008-03-06
OK, I have a weird glitch. I was playing around with the login screens, to make one of my own by rewriting an existing one. I downloaded a bunch of themes and stuff from art.gnome.org using the art program in the repo. Anyways after I finished everything up, I went to turn my laptop off, but the shutdown and reboot buttons were missing from the normal shut down screen, the one to get through the quit button at the end of the menu. The rest of the buttons where there, like the logout, suspend, and hibernate.

I am at a loss as to what I even did, let alone how to fix it. Nothing I messed with said anything about shutdown or reboot, so...

Any uber-gurus out there have any ideas?

Leo

---

### Post by jimv on 2008-03-06
Usually that's what happens when you don't log in with GDM.

Try this in a terminal

sudo apt-get install --reinstall gdm

Then reboot (sudo reboot)

---

### Post by LeoSolaris on 2008-03-06
ok, nothing changed... I reinstalled the GDM and it said it was sucessful. I restarted the comp, but the icons are still missing. Maybe the login screen I used as a template for mine did something to get rid of them?

---

### Post by jimv on 2008-03-06
Try this:

Go to System>Administration>Login Window

Click the Local tab

Make sure that Show Actions Menu is checked.

---

### Post by LeoSolaris on 2008-03-07
Thank ya jimv! That did the trick...    now that ya mentioned it, I remember turning that off to see what it would do...  Now I have my answer!

Thank ya!

Leo S

---

### Post by RebelwithoutaClue on 2008-03-11
Ditto as above for the most part.

Thanks jimv

G

---

### Post by spadewarrior on 2008-03-11
> **jimv said:**
> Try this:

Go to System>Administration>Login Window

Click the Local tab

Make sure that Show Actions Menu is checked.

I'm also trying to get my Power off and restart buttons back, but 'Login Window' isn't on my Administration options. Is there another way to fix this?

Btw, the buttons disappeared when I installed KDE. The buttons are available in KDE, but not Gnome.

---

### Post by LeoSolaris on 2008-03-13
> **spadewarrior said:**
> I'm also trying to get my Power off and restart buttons back, but 'Login Window' isn't on my Administration options. Is there another way to fix this?

Btw, the buttons disappeared when I installed KDE. The buttons are available in KDE, but not Gnome.

I had more than a few issues when I tried putting KDE in with Gnome, too. Try left clicking on the menu button on the panel, and go to Edit Menus. Look through it to see if KDE simply deselected it for display. KDE did all sorts of funky things to Gnome when I tested it, like nearly completely altering my menu set up and replacing a large number of controls with their KDE counterparts.

If that doesn't help, then I am as lost as you are. I ended up fully removing KDE with synaptic.

If you decide to keep it, I hope you have better luck than I did!

Leo S.

---

