---
title: "Compiz on Kubuntu?"
date: 2008-05-07
forum: General Help
---

### Post by Kdar on 2008-05-07
I am thinking to go back to KDE.. 

But I really like Compiz on Ubuntu.. Is it hard to configure and install Compiz on Kubuntu?

---

### Post by josh2112 on 2008-05-08
> **Kdar said:**
> I am thinking to go back to KDE.. 

But I really like Compiz on Ubuntu.. Is it hard to configure and install Compiz on Kubuntu?

Not *quite* as easy as on Ubuntu, but still very simple.  On Gutsy Gibbon and previous versions, it was totally unusable - took a long list of complicated commands and sketchy repositories to install and even then it crashed every 5 minutes. But with Hardy Heron I'm pleased to say it's stable enough that I used it constantly.

Just make sure the restricted driver for your nvidia card is installed (which it should offer to do the first time you log in, just like Ubuntu), then go to System -> Desktop Effects -> Extra Effects.  There's a big "Install" button that'll take care of everything.  Also install the [FONT="Courier New"]compizconfig-settings-manager[/FONT] package of course.

On Ubuntu compiz will start immediately after install... on Kubuntu it *tries* to, but never quite works for me and I always have to reboot once.

Also, if KWIN crashes (which happens quite often while messing around with compiz plugin settings) just go to a terminal and start [FONT="Courier New"]kde-window-decorator[/FONT]. That'll bring your window frames back.

---

### Post by Kdar on 2008-05-08
Oh so.. On Kubuntu now I also don't have to do it manually?

I mean installation of Compiz..

You using Kubuntu now?

---

