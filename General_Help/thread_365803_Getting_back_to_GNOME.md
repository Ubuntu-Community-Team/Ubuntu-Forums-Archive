---
title: "Getting back to GNOME"
date: 2007-02-20
forum: General Help
---

### Post by wdbreen on 2007-02-20
Gday All,
I recently installed Xubuntu via CD on my IBM thinkpad and all went well.  In fact Xubuntu is great and lives up to all its hype about speed and 'unbloatedness'.  But i chose to return to full Gnome Ubuntu by the *sudo apt-get install ubuntu-desktop* command.  Again, all went well and i have my Ubuntu Desktop back but i still get on start-up the "little mouse inside the ubuntu logo" whilst the progress bar is going until my Ubuntu log-on screen appears.
Is this what they call the usplash screen?
How do i get it back to the real Ubuntu start-up screen?
Will this effect anything when moving to Feisty Fawn later this year?

Breeny

---

### Post by Franchie on 2007-02-20
Its just a image, but it can be changed if you really can't stand it any longer ;-).

I do not know the exact commands, but here is a general procedure:

go to /usr/lib/usplash, and look at the files there. You should have at least usplash-theme-ubuntu.so and usplash-theme-xubuntu.so. If not, then use synaptic to get them.

Next, open a terminal, and run: (note: replace "fingerprint" with the name of the theme you want)...

ln -f -s /usr/lib/usplash/fingerprint.so /usr/lib/usplash/usplash-artwork.so
update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/fingerprint.so 10
update-alternatives --config usplash-artwork.so
update-initramfs -u

There. That last step should take some time, and the line before should give you a menu allowing you to choose your splash screen.
And if you get bored with that theme, you can always download more, or compile your own -- its really easy!

Hope this helps,
F.

---

